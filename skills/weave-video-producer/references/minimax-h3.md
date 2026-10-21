# MiniMax H3 and fal H3 Max Prompting

Last research refresh: 2026-08-28.

Read this file for MiniMax H3, H3 Max Video, or H3 Reference. First identify the actual surface and its visible model names and input sockets; MiniMax's technical mode names do not necessarily appear as separate models in fal or Figma Weave.

## Figma Weave: choose between the two visible models

When the user's Weave model menu contains only **H3 Max Video** and **H3 Reference**, use this as the user-facing decision:

| Weave model | Choose it when | Determine from connected inputs |
| --- | --- | --- |
| **H3 Max Video** | Generating from text, animating a concrete first frame, or bridging a first and last frame | No frame = text-to-video; first frame = image-to-video; first and last frames = keyframe interpolation, but only if both sockets are present |
| **H3 Reference** | Preserving or borrowing subject identity, style, motion, voice, audio, editing, or continuation behavior from attached media | Map each attached image, video, or audio asset to one explicit role using the exact reference labels shown by the node |

T2VA, I2VA, FL2VA, L2VA, and Ref2VA are internal shorthand for prompt construction. They are not five models the user needs to find. Keep those acronyms out of the user-facing instructions unless they clarify a technical diagnosis.

If **H3 Max Video** exposes only text and a first-frame input, do not offer first-and-last-frame or last-frame-only prompting. If **H3 Reference** displays labels such as `Image 1`, `Video 1`, or `Audio 1`, cite those exact labels in the prompt rather than inventing angle-bracket labels.

Preserve the exact descriptive names the user has given the connected Weave nodes. At final hookup, create a **Reference binding map** with all four columns:

```text
Model slot | Weave node name | Prompt alias | Job
Image 1 | MAYA — CHARACTER IDENTITY | MAYA | identity and wardrobe
Video 1 | WALK CYCLE — MOTION | WALK MOTION | gait and pacing only
Audio 1 | MAYA — VOICE | MAYA VOICE | voice identity and delivery
```

The Weave node name is the durable production identity; the H3 slot is temporary and depends on connection order. In the prompt, establish each binding once, then use the concise alias consistently. Recheck the table whenever wires are reconnected or reordered. Do not assume a custom node title is automatically transmitted to H3.

## Do not conflate the contracts

- **MiniMax H3:** The official model family defines T2VA, I2VA, FL2VA, L2VA, and full-reference Ref2VA. Official MiniMax documentation may expose 4-15 second output, 768P or 2K resolution, multimodal reference inputs, and a 7,000-character prompt budget.
- **fal H3 Max:** This is fal's post-trained H3 variant. The current fal endpoints in the studied share set are `minimax/h3-max/text-to-video` and `minimax/h3-max/image-to-video`. Current fal API docs list 480P or 768P, an integer duration with a 5-second default, three prompt-expansion modes, and an optional first and last image on the image-to-video endpoint.
- **Weave or another product UI:** Use its displayed model name, inputs, limits, and controls as authoritative. Do not carry the 2K, reference count, duration, negative-prompt, or expansion assumptions from one surface to another.

The fal share corpus contains both the original seed prompt and, when prompt expansion was enabled, the `expanded_prompt` actually sent to H3 Max. Treat those as different artifacts.

## Translate the visible inputs into an internal mode

| Mode | Inputs | Prompt's main job |
| --- | --- | --- |
| T2VA | Text only | Establish the complete audiovisual timeline |
| I2VA | First image + text | Continue forward from the exact opening frame |
| FL2VA | First and last images + text | Define one achievable path between two concrete frames |
| L2VA | Last image + text | Infer a plausible earlier state and converge on the exact final frame |
| Ref2VA | Images, video, and/or audio as references | Assign reference roles, preservation strength, timing, motion, voice, editing, or continuation behavior |

On fal H3 Max, `image_url` is the first frame and `end_image_url` is the optional last frame. The output aspect ratio follows the first image. The current H3 Max API does not expose a last-frame-only or full-reference endpoint. On Weave, trust the sockets shown on **H3 Max Video** instead of assuming the fal API surface is identical.

## Prompt expansion on fal H3 Max

fal exposes:

- `disabled`: send the authored prompt without a separate fal rewrite;
- `balanced`: fast expansion, normally about one second;
- `quality`: richer expansion that may take up to roughly 30 seconds.

Choose deliberately:

- Use **balanced** for fast iteration from a compact natural-language seed.
- Use **quality** when the seed is intentionally under-specified and richer production interpretation is welcome.
- Prefer **disabled** when delivering an exact, fully structured H3 prompt and a second rewrite could change timing, dialogue, camera logic, or constraints.

When diagnosing a result made with expansion, inspect the returned `expanded_prompt` before changing the seed. A failure may come from the rewrite, not the user's original wording. Record the seed, expansion mode, expanded prompt, settings, and result separately.

## Native prompt structures

### T2VA, I2VA, FL2VA, and L2VA

Use the three native fields in this order:

```text
integrated_multimodal_description: [Shot 1] ...

overall_soundscape: ...

non_diegetic_music: ...
```

T2VA begins directly with these fields. Keyframe modes add the appropriate alignment instruction as the first line, followed by one blank line.

I2VA:

```text
For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.
```

FL2VA:

```text
How the reference pictures align with the target video — Picture 1 (from Shot 1) aligns with the 0.00-second mark of the target video; Picture 2 (from Shot N) aligns with the S.SS-second mark of the target video.
```

L2VA:

```text
How the reference pictures align with the target video — <Picture 1> (from [Shot N]) aligns with the S.SS-second mark of the target video.
```

Replace `N` with the actual final shot and `S.SS` with the effective duration to exactly two decimal places.

### Full-reference Ref2VA

When the actual surface supports full-reference H3, including **H3 Reference** in Weave, use:

```text
subject_definitions:
...

summary:
...

retention_analysis:
...

detailed_description:
...

overall_soundscape:
...

non_diegetic_music:
...
```

Use the reference labels exposed by the actual surface. If Weave shows `Image 1`, `Video 1`, and `Audio 1`, bind those slots to the exact Weave node names and concise prompt aliases before the structured prompt. When the interface accepts MiniMax's native structured labels, use:

- `<Subject N>` for reusable visible content such as identity, product, environment, style, action, or pose;
- `<Picture N>` only when an image is a concrete first frame, keyframe, last frame, storyboard, or composition anchor;
- `<Video N>` for an edited/continued source video or whole-video camera, cut, rhythm, or temporal structure;
- `<Audio N>` for audio that is copied or referenced.

Assign one explicit job to every reference. In `retention_analysis`, distinguish `fully_preserved`, `partially_preserved`, `attribute_transfer`, and `weak_reference`; for audio distinguish `fully_copy`, `partially_copy`, `reference`, and `weak_reference`. Do not create a standalone picture/video label when the asset merely defines a subject and will not be tracked independently.

## Timeline and shot grammar

- `[Shot 1]` has no timestamp.
- Start each later shot with a strictly increasing cut time inside the runtime: `[Shot 2] At 00:03.500, the camera cuts to...`.
- Add a shot only when the cut reveals new subject, space, state, viewpoint, or time information. Use camera motion for a modest distance or angle change.
- State cuts explicitly. For a continuous take, say it is one shot and describe the physically continuous camera corridor and action chain.
- Match the action load and spoken words to the actual duration. A five-second clip usually supports one clear event or a very short exchange, not a miniature trailer.
- Give difficult motion an observable start state, causal action, and end state. Preserve momentum, gravity, contact, occlusion, and object state when the mechanism depends on them.

Camera direction is strongest as a natural sentence containing the useful parts of:

```text
motion type + amplitude + speed + target/reveal
```

Examples include push/pull, zoom, pan, truck, tilt, pedestal, arc, tracking, static, shake, POV, and roll. Keep focal-length zoom distinct from a physical push or pull. Omit amplitude and speed when their ordinary values add no control.

## Dialogue, visible text, and audio

- Give every actual vocal source a stable `(S1)`, `(S2)`, and so on in order of first vocal event.
- Preserve exact dialogue inside `<d>` with a language tag: `<d>[English] What is the real?</d>`.
- Keep delivery, acting, identity, and lip behavior outside `<d>`.
- For voiceover, state `says in an off-screen voiceover` and say that the visible character's lips remain closed.
- Use `<scenetrans>` when a line continues across a cut and `<cutoff>` when the clip truncates speech.
- Put visible signs, labels, subtitles, and UI strings in double quotation marks and preserve spelling exactly.
- Put synchronized dialogue, singing, diegetic music, and shot-specific sounds in `integrated_multimodal_description` or `detailed_description`.
- Use `overall_soundscape` for a short summary of ambience, physical sounds, and non-verbal human sounds. Do not repeat dialogue there.
- Use `non_diegetic_music` only for audience-only score. Specify instrumentation, tempo/rhythm, and dynamic change; use `N/A` when there is none.

## T2VA prompting strategy

The fal examples span one-line seeds, compact time-coded directions, and long production briefs. Prompt length is not a quality target.

Choose one of two coherent approaches:

1. **Compact seed + expansion:** State the subject, one action chain, environment, camera behavior, capture/style language, and audio priority. Let balanced or quality expansion build the native structure.
2. **Authored native prompt:** Write the native fields and exact timeline directly, then disable expansion when possible.

Do not write a half-structured long seed and assume another expansion pass will preserve every detail. For a complex continuous action, prioritize the physical sequence and camera path over decorative world inventories. For game/UI footage, define the invariant mechanic, camera rule, obstacle/input relationship, and state changes before environmental variety.

## I2VA and FL2VA prompting strategy

For I2VA, let the image own appearance, composition, lighting, and static spatial relationships. In the prompt, reinforce only identity-critical or drift-prone details, then concentrate on:

- action onset and performance;
- subject, camera, and environmental motion;
- dialogue and synchronized audio;
- the visible end state.

Recommended I2VA progression:

```text
first-frame anchor → action onset → continuous development → result or reaction
```

For FL2VA, do not restate two static images. Describe the observable path that makes the first frame become the last. Prefer one continuous shot and compositionally compatible frames.

Recommended FL2VA progression:

```text
first-frame state → observable intermediate changes → narrowing differences → exact last-frame landing
```

If the two frames differ in camera angle, subject scale, lighting logic, or too many independent object states, repair the frames before adding more prompt prose.

## Constraint strategy

H3 examples respond to targeted negative direction, especially for preventing an adjacent genre, an unwanted transition, added text, or broken format. Use a concise constraint only when it protects a likely or observed failure:

- `one continuous shot; no cuts`;
- `static side-view camera; no zoom or rotation`;
- `no subtitles or added on-screen text`;
- `photoreal live action; no game-engine or 3D-render appearance`.

Prefer positive visible states for identity, camera, object geometry, and preservation. Avoid a long catalog of unrelated prohibitions.

## Fast iteration and QA

For every run, preserve the seed, expansion mode, expanded prompt when available, duration, resolution, aspect ratio or input-image dimensions, seed value, inputs, and result.

Change one control variable per comparison:

1. mode or keyframes;
2. prompt-expansion mode or expanded prompt;
3. timing/dialogue;
4. main physical mechanism or camera path;
5. identity/style preservation;
6. secondary audio or polish.

Use the same random seed for A/B comparisons when the surface exposes it. Judge the hardest requirement first. Return a complete self-contained replacement prompt for a fresh run, but do not accumulate every past repair sentence.

## Current primary sources

- MiniMax H3 prompt-writing skill and its base/full-reference guides: https://github.com/MiniMax-AI/MiniMax-H3/tree/main/skills/h3-prompt-writing
- fal H3 Max text-to-video API: https://fal.ai/models/minimax/h3-max/text-to-video/api
- fal H3 Max image-to-video API: https://fal.ai/models/minimax/h3-max/image-to-video/api
- fal H3 prompting guide and examples: https://fal.ai/learn/devs/minimax-h3-prompting-guide

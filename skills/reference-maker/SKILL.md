---
name: reference-maker
description: Plan and write copy-ready Figma Weave prompts, review criteria, and repair prompts for production reference images and reusable AI-video reference workflows, including locations, products, props, visual style, composition, blocking, first frames, end states, transition targets, and continuity anchors. Use when a workflow needs high-quality reference-image prompts or a branchable Weave graph that reduces spatial, material, lighting, or design ambiguity. Return prompts for the user to run in Weave, never generated media. Accept approved character assets from character-sheet-builder but do not create or redefine recurring character identity, wardrobe canon, turnarounds, or expression sheets. Pair with weave-video-producer through numbered prompt outputs, exact attribute ownership, and generation-ready handoffs.
---

# Reference Maker

Act as a reference-image director for generative video. Build images that constrain a specific production uncertainty. Optimize for downstream model legibility, control, and reuse rather than moodboard polish.

## Weave-only output contract

- Output copy-ready reference-generation prompts, input/source maps, dependency order, node manifests, QA criteria, and repair prompts for the user to run in Figma Weave.
- Never call image-generation or image-editing tools and never imply a reference was generated in ChatGPT.
- Review attached or Weave-generated outputs when supplied, then return a complete copy-ready Weave replacement or repair prompt incorporating the targeted changes. Include separate compositing instructions when that is the appropriate production path.
- Use stable descriptive production labels; do not invent proper names unless requested or narratively necessary.
- Preserve user-supplied Weave node names exactly. Otherwise, give every durable source and approved reference a concise canonical name using `[ASSET] — [REFERENCE JOB]`, such as `GARDEN — LOCATION`, `UMBRELLA — END FRAME`, or `MAYA + GARDEN — FIRST FRAME`. Do not add version numbers to Weave node names. Retry or repair work in the same node when practical; use temporary `ALT A` or `ALT B` suffixes only for simultaneous comparison branches, then rename the selected result to the clean canonical name.

## Copy-ready prompt contract

- Put each complete generation prompt in its own fenced `text` block. Keep the video/concept title, prompt title, `Weave node name:` line, version, revision summary, and workflow labels outside the copyable block. Never prepend or append labels such as `RERUN`, `REVISED PROMPT`, or `FINAL PROMPT` to the prompt itself.
- The block contains only instructions needed by the target model. Include a title as visible text or dialogue only when the user explicitly requests it in the generated content. Preserve functional reference bindings, subject aliases, and model-native section tags when they control generation; those are not prompt titles.
- For any requested tweak, including a change to just one line, section, reference, or constraint, return the entire updated prompt for each affected generation, ready to paste into Weave. Preserve all accepted decisions outside the requested change and reconcile any dependent timing, reference, or continuity changes.
- Never substitute a changed excerpt, diff, “same as before,” “keep everything else,” or instructions to splice text into an earlier prompt. A brief change summary may sit outside the block. Only return a partial patch when the user explicitly requests partial output; asking to change one part alone is not such a request.
- If the complete prior prompt is unavailable, obtain it before claiming to provide a complete replacement. For repairs using an existing image, name the required attached source and fully state the desired result and preserved attributes; a complete repair prompt need not discard approved assets.
- Before delivery, check the copyable block for stray titles or workflow labels, unresolved placeholders, missing source bindings, and references to earlier chat instructions.

## Ownership boundary

- Own location, set, product, hero object, prop, vehicle, style/look, composition, blocking, first-frame, end-state, transition-target, gesture-mechanics, and continuity references.
- Accept approved character assets and continuity rules from `$character-sheet-builder` when composing a character into a scene.
- Never invent, repair, or redefine a recurring character's face, body canon, wardrobe canon, smile, teeth, or turnaround. Delegate those tasks to `$character-sheet-builder`.
- Allow incidental background people only when their identities are explicitly free and they cannot compete with the hero character.
- Return reference assets to `$weave-video-producer`; leave story, timing, camera choreography, dialogue, performance direction, and final motion prompting to that skill.

## Core workflow

1. **Read the production need**
   - Identify the target image or video model, final aspect ratio, shot framing, intended camera path, action, duration, and which visible attributes cannot drift.
   - Ask only for missing information that changes reference selection or composition.
   - If Weave Video Producer supplied a reference brief, treat its shot requirements as authoritative.

2. **Define the reference contract**
   - For every required attribute, mark it **exact**, **preferred**, or **free**.
   - Assign every source image one responsibility. Use its exact existing Weave node name or propose a stable source name before prompting.
   - Resolve conflicts in geometry, lighting, color, scale, design variant, wardrobe, or style. State which source wins for each conflict.
   - Never rely on an image that will not be supplied to the generation request.

3. **Choose the smallest useful reference set**
   - Read `references/reference-types.md` when selecting or prompting reference types.
   - Read `references/filmmaking-for-references.md` for first frames, multi-shot coverage, screen geography, eyelines, blocking, or cinematographic continuity.
   - Give each reference one primary job. Combine jobs only when one image can represent them without ambiguity.
   - Start with character, product, and location assets independently. Combine them only after each source is approved.
   - Prefer one composed first frame when spatial relationships matter more than separate subject images.
   - Add an end-state reference only when the landing composition or transformation result is truly critical.

4. **Audit source quality**
   - Prefer sharp, well-lit, uncluttered inputs with useful scale and natural perspective.
   - Reject or flag blur, compression artifacts, clipped geometry, ambiguous materials, illegible branding, inconsistent design variants, heavy grading, and conflicting light directions.
   - If a scene source contains a person being replaced, mask or neutralize that person before adding the approved character.
   - If text or a logo must remain exact, require a clear source and flag that image generation may still need a compositing or typography pass.

5. **Design the image**
   - Specify subject placement, scale, orientation, eyeline if applicable, foreground/midground/background relationships, negative space, visible surfaces, prop state, light direction, and crop.
   - Make environment geometry navigable for the planned movement. Show entrances, exits, pathways, landmarks, depth, and obstacles that affect staging.
   - Keep reusable product and object references neutral enough to reveal true shape, material, color, labeling, and construction.
   - Use a rough sketch as composition control only; explicitly exclude its drawing style when realism is required.
   - Give motion a viable starting pose. Avoid frozen mid-action anatomy unless that exact state is the required anchor.
   - Remove visual motion cues that contradict the planned action, including incompatible motion blur, dust direction, body lean, hair direction, or vehicle attitude.
   - Define whether the frame is objective or tied to a specific character's emotional point of view. Let camera height, distance, eyeline proximity, and lens-to-subject relationship support that choice.
   - For moving cameras, build foreground, midground, and background layers that can produce useful parallax without blocking the subject or camera corridor.
   - For realism, describe physical evidence rather than relying on adjective stacks: surface wear, scratches, fingerprints, seams, fabric tension, small asymmetries, dust, edge softness, and signs of handling appropriate to the object and setting. Keep only evidence that the camera can actually see.

6. **Write copy-ready prompts**
   - State the reference's single job first.
   - Map every supplied image to the attributes it controls and the attributes to ignore.
   - Describe visible positive outcomes directly: composition, geometry, materials, lighting, capture, and required empty space.
   - Adapt negative constraints to the target image model. When negative prompting is weak or unsupported, express the desired positive state instead.
   - Keep the prompt self-contained and remove decorative language that does not improve control.

7. **Deliver the Weave prompt package**
   - Return one copy-ready prompt for each required reference, in dependency order.
   - Put a `Weave node name:` line immediately before each generation prompt so the user can name the resulting reference when it is created or approved.
   - Preserve exact supplied attributes and approved character continuity in the prompt mapping.
   - State which output the user should approve before running the next prompt.
   - For failed outputs, change one variable at a time, but deliver the complete updated Weave prompt with all preserved constraints and required sources.
   - Never generate or edit the media in ChatGPT.

8. **Run reference QA**
   - Inspect the primary job first: identity placement, environment geometry, product design, prop state, composition, or final state.
   - Check gaze and eyeline against the intended subject or action target; a plausible face looking at the wrong thing is a failed blocking reference.
   - Check perspective, scale, lighting direction, shadows, reflections, materials, text, hands, contact points, occlusion, and crop only as relevant.
   - Confirm the frame can physically lead into the planned motion and that the camera has room to execute its path.
   - Remove unintended people, duplicate objects, competing products, decorative labels, collages, and irrelevant details the video model might copy.
   - If a geometry-, hardware-, logo-, or typography-critical asset still drifts after one targeted repair, stop regenerating the full frame. Preserve the approved scene and use a masked composite, inpainting pass, exact typography layer, approved multi-view asset, or controllable 3D render; then relight and edge-match the inserted asset before approval.

9. **Approve and hand off**
   - Treat the approved still as a required checkpoint before motion generation.
   - Give every approved reference a stable number and canonical name without a version suffix.
   - Include its exact `Weave node name` in the handoff. Do not assign a permanent `Image 1`, `Image 2`, or other model slot here; the video-production skill assigns temporary slots from the final connection order.
   - Retry or repair in the same Weave node when practical. If comparison branches are necessary, promote the selected result to the clean canonical name and stop using the alternatives downstream.
   - Return attribute ownership, exact invariants, permitted variation, unsupported details, and any source-preparation steps.

## Figma Weave workflow design

When the user wants a reusable Weave workflow rather than only a prompt:

1. Create separate input nodes for character, product, location, style, composition, and motion references. Do not merge their responsibilities at intake.
   Name every source and approved output with the stable `[ASSET] — [REFERENCE JOB]` convention and use the same exact name in manifests and handoffs. Do not add version suffixes.
2. Convert style sources into editable attribute descriptions such as palette, texture, lighting, contrast, and composition. Keep style text separate from subject description.
3. Branch controlled variations from the same approved inputs. Change one major variable per branch and compare results side by side.
4. Route the selected result through masking, inpainting, compositing, relighting, or color repair before it becomes a video input. Never animate a still with known face, hand, text, geometry, or edge defects.
5. Freeze the approved result as a named canonical node. Downstream video branches must reference that node rather than an earlier draft.
6. Derive final-aspect-ratio versions from the approved master while preserving protected subject, look-room, and action-safe zones.
7. When a hero object must rotate or be seen from several angles, prefer approved multi-view inputs or a controllable 3D asset over repeated independent 2D reinterpretations.
8. When different elements move independently, preserve separate layers or masks and provide a dedicated motion reference for each important element when the target node supports it.

Return a short node manifest using this pattern:

```text
Inputs -> Attribute extraction -> Generation branches -> Comparison gate -> Repair/composite -> Approved reference -> Aspect-ratio outputs -> Video node
```

## Reference selection rules

### Location or world anchor

Use when geography, production design, scale, or lighting direction must persist. Favor clear navigable space over a beautiful but ambiguous mood image.

### Product, prop, or hero object

Use when shape, material, color, proportions, packaging, controls, typography, or damage state must remain exact. Add alternate views only for surfaces that will actually appear.

### Style or look anchor

Use sparingly. State exactly what it controls: palette, contrast, texture, capture medium, production-design density, or lighting character. Never let style override product or character canon.

### First-frame or blocking anchor

Use when composition and spatial relationships drive the shot. Lock subject position, orientation, starting pose, camera height, framing, props, geometry, light direction, and negative space.

### End-state or transition target

Use when a transformation, match cut, loop, product reveal, or landing configuration must resolve precisely. Confirm the duration permits a plausible path between start and end.

### Mechanics or difficult-detail reference

Use for a critical hand position, grip, contact point, machine state, liquid behavior, or action silhouette. Let it control mechanics only; do not allow it to redefine character identity or scene style.

### Multi-view or 3D geometry anchor

Use when the camera or object reveals substantially different surfaces. Generate or supply consistent front, back, left, and right views, then use a controllable 3D or multi-view workflow when available. A single beautiful angle is not sufficient evidence for unseen geometry.

## Output modes

### Planning

Return:

1. **Reference brief** - exact, preferred, and free attributes.
2. **Reference plan** - numbered images and one job per image.
3. **Dependency order** - what must be approved before composition.
4. **Material risks** - only meaningful generation risks.

### Prompt delivery

Return:

1. **Input checklist**
2. **Source map**
3. **Weave node names and generation order**
4. **Copy-ready Weave prompt** for each reference
5. **QA checklist** tailored to each reference's job

### Review or repair

Return:

1. **Diagnosis**
2. **Keep / remove / replace** decisions
3. **Complete copy-ready replacement or repair prompt**; any separate edit instructions supplement it
4. **Revised reference map**

### Production handoff

Use this format:

```text
Reference [number] - [stable canonical name]
Weave node name: [exact node title]
Model slot: unassigned until final video-node hookup
Primary job: [one sentence]
Controls exactly: [attributes]
May vary: [attributes]
Ignore from source: [irrelevant source attributes]
Use in shots: [shot numbers or phases]
Unsupported: [details not established]
```

## Non-negotiable principles

- Use the fewest references that remove the important uncertainty.
- Give every reference one primary job and explicit attribute ownership.
- Separate subject design, location design, and composition until each is approved.
- Do not let a scene reference compete with an approved character identity.
- Build spatially useful first frames, not merely attractive key art.
- Preserve true product geometry and materials before adding style.
- Prefer staged, testable reference building over one overloaded generation.
- Never claim a detail is locked when no supplied or approved source establishes it.

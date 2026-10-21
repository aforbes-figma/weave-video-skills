# Seedance 2.5 Prompting Notes

Last research refresh: 2026-08-19.

These notes summarize current public guidance for Seedance 2.5. Model behavior and platform limits can change; browse for current guidance when the task depends on exact capabilities.

## Current working assumptions

An August 2026 prompting guide describes Seedance 2.5 as supporting clips up to 30 seconds, native audio, multimodal references, and native output up to 1080p. Treat these as platform/model facts to re-check if a user asks about current limits.

The current guide recommends structuring complex prompts with labeled sections in roughly this order:

1. GLOBAL STYLE
2. SCENE
3. CHARACTERS
4. LOCATION
5. FIRST FRAME AND BLOCKING
6. shot-by-shot breakdown
7. OPTICS
8. CAMERA
9. PHYSICS
10. LIGHTING
11. AUDIO

The exact labels can be adapted, but keep the conceptual order: lock the world and starting state before describing motion.

## Reference discipline

- Use one deliberate reference per element that truly needs consistency: identity, product, location, style, or keyframe.
- Fewer purposeful references are often better than a cluttered reference set.
- If a reference already locks character appearance, avoid repeatedly redescribing the same attributes unless reinforcement is necessary.
- Explicitly map each reference to its job and state what should be ignored when a reference contains irrelevant background/style information.
- For Seedance character sheets, provide one canonical visible face total. Remove facial features from secondary full-body panels so they constrain body, wardrobe, silhouette, and pose without introducing competing face renders.

When Seedance is the reference-driven branch of a broader workflow:

- map only assets that will actually be attached to the Seedance run;
- let approved references own appearance, composition, geometry, palette, and lighting instead of repeating them in prose;
- give the most uncertain visual state, often the first frame or end state, a dedicated reference rather than compensating with a longer prompt;
- keep a separate reference-free MiniMax H3 prompt free of reference maps when the assets will not be attached there.

## First-frame blocking

For continuity-sensitive clips, explicitly define the first frame:
- subject positions;
- facing direction;
- camera position/framing;
- important props;
- seating/standing geometry;
- screen direction.

This gives the motion model a fixed physical state before events begin.

## Multi-shot prompting

For each shot:
- label it clearly;
- give a time range when pacing matters;
- state framing/camera position;
- describe the action and end point;
- state `HARD CUT.` when a cut occurs.

Do not let a new angle appear implicitly inside the same shot description.

For 30-second scenes, segment the runtime deliberately. Longer prompts are acceptable when the scene genuinely needs them; clarity matters more than brevity.

## Camera

Specify physical camera behavior. If a move matters, define path, direction, speed, and stabilization. Lens choice changes spatial compression and light behavior independently of movement.

Use direct camera vocabulary when appropriate: push/dolly, pull back, truck, arc/orbit, crane, handheld follow, locked, POV, etc.

For POV, explicitly prevent unwanted behavior when necessary, such as no cuts or no zoom, and describe natural head/body movement.

## Physics and continuity

Seedance responds better when repeated mechanics are described as stable rules rather than vague effects. For transformations, action, vehicles, weather, or object interactions, define causal physical behavior.

Continuity instructions are particularly useful for:
- identity and wardrobe;
- screen direction;
- seat/location geometry;
- object state progression;
- weather/light persistence;
- product spelling/shape;
- when an effect starts and stops.

## Audio

Treat audio as part of the production, not an afterthought. Put it after visual/camera instructions so the scene is already spatially defined.

Specify:
- dialogue text and timing;
- voice qualities only when useful;
- ambience;
- foley tied to actions;
- music presence/absence;
- intentional silence;
- when speech must finish.

## Prompt hygiene

Prefer:
- stable nouns and repeated naming for persistent entities;
- explicit time ranges;
- observable action;
- one physical rule per important effect;
- concise high-value negative constraints.

Avoid:
- contradictory camera terms;
- too many simultaneous actions;
- vague location changes;
- references that fight the written prompt;
- generic adjective stacks;
- endless negative lists.

Reference-driven does not mean verbose. A short scene can still use a lean timeline after the reference map and first-frame state are locked.

## Authority hierarchy for complex clips

Use a compact hierarchy so the model does not have to reconcile several competing versions of the same instruction:

1. Reference map: which asset owns identity, environment, product imagery, or voice.
2. Global rules: the few properties that persist for the entire clip.
3. Shot schedule: only what changes, when it changes, and what triggers it.
4. Exact dialogue and audio: the spoken wording, delivery, ambience, and cues.

Avoid restating the same constraint in the global block, schedule, every shot, and an `AVOID` list. Put each rule in its strongest home and repeat only a critical binding at the moment it is used.

## Literal image and UI inserts

When a supplied screenshot or product frame must appear literally rather than inspire a new design:

- bind it with all three identifiers at first mention: model slot, exact Weave node name, and a short stable alias;
- call it a literal 2D insert, not a style or design reference;
- repeat the slot, node name, and alias in the exact shot where it appears;
- assign it to one shot or beat instead of asking it to persist through several camera changes;
- preserve its crop, layout, typography, element count, and internal spacing;
- allow only whole-image transforms such as uniform scale, translation, opacity, or a simple mask reveal;
- keep it flat and screen-locked, and do not animate, redraw, or reinterpret its internal UI.

If exact pixels remain essential after one focused retry, generate the live-action plate without the insert and composite the original asset afterward.

## Exclusive overlay lifecycle

For sequential text cards or product inserts, define one overlay channel with a strict lifecycle:

`complete entrance -> stable hold -> complete exit to zero opacity -> short visibly empty interval -> next entrance`

Use a blank interval of roughly 0.2-0.3 seconds when runtime allows. State that a new overlay cannot begin while the previous one remains visible or ghosted. After an overlay-stacking failure, avoid crossfades. For exact text, prefer a precomposed graphic card over asking the video model to construct letterforms.

## Human dialogue and performance

Solve identity, voice, and performance separately:

- one character reference is the facial identity authority;
- the uploaded audio owns timbre, accent, and vocal character, but not the old wording or timing;
- the performance block owns breath, gaze, expression, posture, gesture timing, and reactions.

Write dialogue in speakable thoughts with breaths at clause or sentence boundaries. Put hard cuts inside silence rather than in the middle of phonemes. Use phrase-level emphasis and a few asymmetrical human cues: a preparatory inhale, eyes leading the head turn, a smile that evolves instead of switching on, one hand staying quiet while the other gestures, gestures that slightly lead or trail speech, and a return to rest between gestures. Favor occasional irregular blinks and small posture adjustments over constant mechanical micro-motion.

More character references do not automatically improve performance. When several references show a face, declare one identity authority and narrowly scope the others.

## Locked coverage as a repair strategy

If an intended pan, orbit, or handheld move wanders, replace it with two or three locked camera positions and explicit `HARD CUT.` transitions. Place cuts after completed phrases or breaths. Preserve room geography, identity, wardrobe, lighting, prop state, screen direction, and room tone across every angle.

When browsing newer sources, favor official model/platform documentation and recent tested prompting guides over old prompt libraries.

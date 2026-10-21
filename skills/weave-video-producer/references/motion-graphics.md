# Motion Graphics and Presenter Overlays

Read this reference when a video uses on-screen typography, product screens, data, tracked callouts, graphic transitions, or a deliberate mixture of live action, 3D, and 2D design.

Motion graphics are opt-in. Do not add them simply because a clip is a product launch, advertisement, explainer, or presenter video. If the user has not requested them and the approved concept does not depend on them, keep the image clean and do not load the rest of this reference.

## Contents

- Choose the production path first
- Declare one coordinate space per element
- Define a compact design system
- Separate dialogue, pronunciation, and display copy
- Use readable beat grammar
- Design transitions as physical or editorial mechanisms
- Block presenter interaction
- Preflight dense graphics
- Graphics cue sheet
- Repair by symptom

## Choose the production path first

Choose how each graphic will be made before describing its animation:

- **Generate in-model** when the element is expressive, approximate, short-lived, or must participate organically in scene depth and lighting.
- **Supply a precomposed asset** when typography, casing, alignment, layout, branding, or UI structure must remain exact but the asset can move as one rigid image.
- **Composite over a generated plate** when exact pixels, charts, numbers, real product UI, or several sequential overlays are delivery-critical. Generate clean footage with reserved negative space, stable timing, and gestures aimed at known screen coordinates.

After one focused retry fails on critical text or UI, change the production method instead of expanding the prompt indefinitely.

For a composite workflow, keep the stage boundary explicit. The video-model prompt describes only the clean plate, its timing, and reserved space. The graphics cue sheet describes when the supplied asset is added afterward. Never tell the video model to reveal, cut to, or preserve a finishing asset that is not attached to its run.

## Declare one coordinate space per element

Assign every graphic to exactly one spatial behavior:

- **Screen-locked:** fixed to frame coordinates while footage moves behind it.
- **Depth-composited:** fixed to the frame but occluded by the presenter or foreground objects, creating a behind-subject layer.
- **Object-tracked:** attached to a named physical anchor and moving with its parallax.
- **Surface-bound:** printed, projected, plotted, or otherwise attached to an in-world plane or object.
- **Full-frame graphic:** the entire composition is a flat designed frame; camera language does not apply unless an actual virtual camera is intended.

Do not describe the same element as both screen-locked and object-tracked. Specify the anchor, occlusion order, and whether the element receives scene lighting.

## Define a compact design system

When a design reference is attached, map it to reusable components rather than copying its layout. Name only the components needed for the clip, such as `HEADLINE`, `OUTLINE WORD`, `PILL`, `CARD`, `UNDERLINE`, or `BADGE`, and state what to ignore from the source.

Define only consequential properties:

- type category, weight, case, tracking, and alignment;
- box shape, padding, corner behavior, and internal centering;
- palette and contrast rules when color accuracy matters;
- shadow, outline, glow, texture, and dimensionality;
- entrance, settle, hold, and exit behavior.

If an exact font file is unavailable to the generation workflow, specify a broad type category and precompose the graphic when exact letterforms are important.

For mixed 2D and 3D work, define the render contract for each layer. Flat elements remain flat unless a physical interaction is intentional; lit 3D elements retain material, reflection, and shadow behavior. Interaction does not imply that the layers exchange rendering properties.

## Separate dialogue, pronunciation, and display copy

Maintain three independent text authorities:

1. **Exact written dialogue:** the canonical words the script contains.
2. **Performance pronunciation:** phonetic guidance used only to shape speech.
3. **Exact display copy:** strings rendered on screen, preserving spelling, case, punctuation, and intended line breaks.

Never place phonetic spellings in the display-copy list. Never let an overlay become an unintended subtitle.

For exact display text, include one canonical **COPY LIST** and state that no other words, numbers, labels, captions, watermarks, or stray letterforms appear. In each timed beat, refer back to the exact string rather than introducing a variant. Prefer precomposed cards when the copy is brand-critical.

## Use readable beat grammar

Give every overlay a complete lifecycle:

`entrance -> settle -> readable hold -> complete exit -> visibly empty interval`

Only then may the next exclusive overlay enter. Use one dominant visual focus per beat and avoid asking the presenter, camera, text, and product insert to perform equally complex actions simultaneously.

- Tie entrances to a semantic word or completed phrase, never an unrelated timestamp alone.
- Let the gesture lead or trail the spoken phrase slightly instead of landing mechanically on every syllable.
- Keep the assembled graphic stable during its reading window.
- Animate motion blur on moving layers only; restore crisp edges on landing.
- End important compositions with a deliberate hold, including still lighting and camera when required for editing.

For dense informational graphics, introduce one concept at a time. Charts and percentage bars should appear already correct when numerical fidelity is critical; do not count, redraw, or morph them unless that motion carries the story and remains verifiable.

## Design transitions as physical or editorial mechanisms

Name the transition and define its source, bridge, and destination:

- **Hard cut:** a deliberate viewpoint or composition change.
- **Shape match:** a source silhouette aligns with a target silhouette across the cut.
- **Motion match:** the outgoing movement vector continues into the incoming shot.
- **Color bridge:** one element expands or wipes to become the next background.
- **In-world transformation:** material changes travel through named geometry rather than appearing everywhere at once.

For a continuous take, every transformation must have a visible causal path. State what remains persistent after the change. Use a persistence lock when an accumulating object or layered construction must only grow and never lose prior parts.

## Block presenter interaction

Reserve graphic zones during shot design, not after it:

- keep critical text clear of the face, eyes, mouth, hands, laptop, and product;
- name the side and approximate frame region for each overlay;
- define which hand gestures, the gesture's target, and its return to rest;
- state whether the hand passes in front of the graphic, points beside it, or never overlaps it;
- maintain consistent screen direction across angle cuts;
- use depth occlusion only when the foreground mask is reliable and narratively useful.

Add short edit handles before and after hard cuts when runtime allows. Place cuts during breaths or silence rather than inside words.

## Preflight dense graphics

Before video generation, approve a still storyboard or a small set of representative design frames. Check:

- hierarchy and mobile readability;
- exact copy and product spelling;
- safe zones and occlusion;
- reference-to-element mapping;
- first frame, transition targets, and final lockup;
- whether every element has one coordinate space and one owner;
- whether the amount of dialogue leaves enough time to read the graphics.

## Graphics cue sheet

For a complex graphics clip, prepare this table before the final prompt:

| Time | Exact asset or copy | Coordinate space | Entrance / hold / exit | Occlusion or interaction |
|---|---|---|---|---|

The cue sheet and prompt must share one timeline. Keep stable rules in the global graphics block and use timed beats only for entrances, changes, exits, and interaction cues.

## Repair by symptom

| Symptom | Likely cause | First repair |
|---|---|---|
| Misspelled or invented text | Model constructing letterforms | Use one copy list and a precomposed asset |
| Product screen is redesigned | Screenshot treated as inspiration | Bind it as a literal rigid insert or composite it |
| Previous overlay remains | Incomplete lifecycle | Require zero-opacity exit and a visibly empty interval |
| Graphic swims during camera motion | Coordinate space is ambiguous | Declare screen-lock or one physical tracking anchor |
| Callout detaches from a product | Weak tracking definition | Name an exact anchor and preserve parallax |
| Presenter gesture feels robotic | Over-synchronized action | Use one gesture per thought, slight lead/lag, then rest |
| Face or hand is covered | Safe zone decided too late | Reserve the overlay region in the first-frame blocking |
| Transition feels arbitrary | No shared visual mechanism | Use a shape, color, or motion match with an explicit bridge |
| Hybrid style becomes muddy | Layer render rules are mixed | Restate separate 2D and 3D material contracts |
| Final frame is unusable | No terminal state or hold | Define the exact lockup and freeze camera, light, and graphics |

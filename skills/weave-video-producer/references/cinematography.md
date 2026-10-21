# Cinematography and Film Grammar

Use this reference to choose intentional filmmaking language. Do not apply every option; choose the few that serve the beat.

## Shot size and narrative use

- **Extreme wide / establishing:** geography, isolation, scale, spectacle.
- **Wide / full:** body mechanics, choreography, relationship to environment.
- **Medium:** interaction, gesture, conversational clarity.
- **Medium close-up:** performance with some spatial context.
- **Close-up:** decision, recognition, tactile detail, emotional emphasis.
- **Extreme close-up / insert:** a single decisive detail; use sparingly.

## Camera angle

- **Eye level:** neutral, intimate, observational.
- **Low angle:** scale, threat, confidence, monumentality.
- **High angle:** vulnerability, pattern, spatial clarity.
- **Ground level:** speed, texture, impact, environmental scale.
- **Overhead:** choreography, graphic composition, disorientation when unexpected.
- **Dutch/canted:** instability; avoid as generic shorthand for intensity.

## Lens character

Treat focal length as spatial storytelling rather than a prestige keyword.

- **Ultra-wide (~14-20mm FF equivalent):** exaggerated depth, speed, distortion, close immersive action.
- **Wide (~21-32mm):** environmental intimacy, kinetic movement, strong parallax.
- **Normal (~35-55mm):** natural perspective, grounded observation, versatile dialogue/action.
- **Short tele (~65-105mm):** portrait isolation, flatter space, elegant compression.
- **Long tele (135mm+):** strong compression, surveillance/distance, graphic layering.

If exact focal length adds no value, describe the field-of-view character instead.

## Camera movement

Always define what moves, where, and why.

- **Locked:** tension, precision, deadpan comedy, observation, allowing internal movement to dominate.
- **Pan / tilt:** reframe or reveal while camera remains in place.
- **Dolly / push / pull:** physical camera translation; changes perspective and parallax.
- **Truck / lateral track:** follows movement or reveals spatial relationships side-to-side.
- **Arc / orbit:** shifts relationship between subject and background; strong for reveals or hero moments.
- **Crane / jib:** changes height and scale; useful for reveal or emotional release.
- **Handheld:** embodied instability; specify subtle, documentary, urgent, or violent rather than merely saying handheld.
- **Steadicam / gimbal:** fluid following; useful for immersive movement without chaotic shake.
- **POV:** lock perspective rigorously; specify whether cuts/zoom are forbidden and how head/body motion behaves.

Distinguish **zoom** from **dolly**. A zoom changes focal length; a dolly changes camera position.

## Movement specification

For critical moves, specify:
- start and end positions;
- direction in screen space and world space;
- approximate path, distance, height, and orbit radius when relevant;
- pace;
- acceleration/deceleration or easing;
- whether the subject leads, follows, or is revealed;
- relationship to the subject and expected parallax;
- settle or hold behavior at the end;
- stabilization / shake behavior;
- focus behavior during the move.

When the generation interface exposes dedicated camera, lens, aperture, or lighting controls, use those controls as the authoritative specification. Keep prompt language compatible and avoid restating a conflicting move in prose.

## Blocking and continuity

Before motion, establish:
- where each subject is;
- which way they face;
- dominant screen direction;
- eyelines;
- object positions and states;
- entrances/exits.

Across cuts:
- avoid unexplained left/right flips;
- preserve relative geography;
- maintain action continuity;
- use motivated axis crossings if deliberately changing screen direction.

## Editing grammar

- **Hard cut:** clearest way to signal a new camera setup in a generated multi-shot prompt.
- **Match on action:** cut during a continuous movement to preserve energy.
- **Reaction cut:** emotional punctuation after an event.
- **Insert:** clarify a critical prop/detail, but ensure prop state matches surrounding shots.
- **Montage:** compress time; use clear, short, distinct beats.
- **Oner / continuous take:** excellent when geography and choreography are simple enough to execute reliably.

Do not imply a cut by suddenly changing lens or camera position. State the cut.

## Lighting grammar

Describe physical light, not only mood.

Useful dimensions:
- key direction and height;
- hard vs soft source;
- contrast ratio / fill level;
- practical sources visible in frame;
- back/rim light;
- color temperature relationship;
- atmospheric interaction;
- continuity through movement.

Examples of functional language:
- large soft window key from camera-left, low fill, warm practicals in depth;
- hard noon sun from high camera-right, deep crisp shadows, hot specular highlights;
- cool overcast skylight, low contrast, wet surfaces carrying broad reflections.

## Performance direction

Use visible behavior instead of abstract emotion alone.

Weak: "she is nervous."
Strong: "she keeps her shoulders still, inhales through her nose, glances once toward the exit, then forces eye contact before speaking."

Give actors playable beats:
- notice;
- hesitate;
- decide;
- conceal;
- react;
- release.

Avoid stacking multiple contradictory emotions in one second.

## Physics and material behavior

Specify only what matters to believability:
- real weight transfer in walking/running;
- acceleration/deceleration for vehicles;
- cloth lag and settle;
- hair response to wind/body motion;
- impact compression/rebound;
- liquid flow/splashes;
- smoke/dust inertia;
- reflections tied to camera/light movement;
- object state changes that persist.

The goal is causal behavior: action -> physical consequence -> settle.

For difficult human or object motion, define:

1. the precise starting state;
2. the force, decision, or contact that initiates motion;
3. weight transfer, momentum, resistance, and environmental reaction;
4. the precise ending state and settle.

Use contrasting physical registers when useful—stillness to release, tension to impact, slow to fast—rather than undirected constant motion.

## Prompt failure patterns

- Too many shots for the duration.
- Camera changes without explicit cuts.
- Conflicting lens/movement instructions.
- Vague geography and blocking.
- A character or product re-described differently in different shots.
- Props resetting state after being opened, consumed, broken, moved, or transformed.
- Generic "cinematic" adjectives without spatial or physical instructions.
- Every element moving at once, giving the model no hierarchy.
- Excessive negative prompting that competes with positive direction.

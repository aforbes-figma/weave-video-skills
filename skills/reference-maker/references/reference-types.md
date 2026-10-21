# Reference-Type Prompt Patterns

Use only the pattern needed for the current production. Replace brackets and remove irrelevant clauses.

## Location anchor

```text
Create one high-resolution production location reference for [project/shot]. Its sole job is to establish [geometry / design / scale / lighting direction].

SCENE: [specific environment and period]. Show [entrances, exits, pathways, fixed landmarks, foreground, midground, background, ceiling/sky, floor/terrain]. Preserve clear navigable depth and physically plausible scale for [planned action or camera path].

CAMERA AND COMPOSITION: [aspect ratio], [framing], camera at [height/angle], looking [direction]. Reserve [negative-space requirement].

LIGHTING: [source direction, quality, color relationship, practicals, shadow behavior].

CAPTURE: sharp, coherent perspective, realistic materials, no motion blur, no people unless specified.

REQUIRED ABSENCES: [elements that would create continuity conflicts].
```

## Product or hero-object anchor

```text
Using [source name] as the exact design reference, create one high-resolution production reference of [object]. Its sole job is to lock [shape, proportions, material, color, labeling, controls, wear state].

Show [primary view] with [specific surfaces] unobstructed and large enough to inspect. Preserve exactly [critical attributes]. Use neutral low-distortion capture, honest material response, crisp edges, and lighting that reveals the true color and construction.

Do not redesign, simplify, add accessories, change the variant, invent text, hide required surfaces, or let reflections obscure the design.
```

## Style or look anchor

```text
Create one visual look reference for [project]. It controls only [palette / contrast / texture / capture medium / lighting character / production-design density].

Depict [simple representative subject or environment] with [specific visual treatment]. Keep character identity, product design, location geometry, and story details deliberately generic so this image cannot override their dedicated references.
```

## First-frame or blocking anchor

```text
Compose the exact first frame for [shot]. Use [approved character/product/location sources] with these responsibilities: [source map].

FRAME: [aspect ratio and framing]. Camera at [height, angle, distance, field-of-view character]. Place [subject A] at [position, orientation, eyeline, starting pose] and [subject/object B] at [position and state]. Establish [foreground/midground/background relationships], [clear travel corridor], and [negative space].

VISUAL LOGIC: [objective / subjective to named character] point of view. Preserve [screen axis, eyeline direction, horizon, entry/exit room, look room, action room]. Include foreground, midground, and background depth suitable for [planned camera move or locked shot].

CONTINUITY: preserve exactly [identity, wardrobe, product, geometry, prop states, light direction]. The pose is stable and physically ready to begin [action].

CAPTURE: [lighting and realism/style]. Produce one coherent frame, not a collage, storyboard, split screen, or labeled diagram.
```

## Coverage reference set

```text
Using the approved geography, character, product, and lighting sources, create [number] separate production reference images for one continuous scene. Each image is a standalone frame, not a multi-panel sheet.

GLOBAL CONTINUITY: preserve the same set geometry, screen axis, subject positions, eyeline directions, wardrobe and product canon, motivated key-light direction, time of day, lens family, horizon, and color logic.

FRAME 1 - GEOGRAPHY ANCHOR: [objective composition and spatial job].
FRAME 2 - HERO FIRST FRAME: [primary shot composition, point of view, starting pose, action room].
[FRAME 3 - REACTION OR SUBJECTIVE FRAME: named viewpoint and emotional job.]
[FRAME 4 - INSERT OR DETAIL: exact prop/product/contact state.]
[FRAME 5 - END STATE: precise landing composition.]

Generate each frame as an individual output. Do not create a collage, contact sheet, captions, camera diagrams, or text labels.
```

## End-state or transition target

```text
Create the exact final-state reference for [shot/transformation]. It controls the landing composition and final physical state only.

Preserve [elements unchanged from approved sources]. Resolve [subject/object/environment] to [precise final position, orientation, configuration, material state, expression if supplied by character reference, and framing]. Maintain continuity of geometry, lighting direction, scale, and camera axis from the approved start frame unless a specified camera move changes them.

Show a physically achievable settled state with no extra transformation stages, duplicate objects, or unintended design changes.
```

## Mechanics or difficult-detail anchor

```text
Create one high-resolution mechanics reference whose sole job is to establish [grip / hand position / contact point / machine state / action silhouette / material interaction].

Show [precise start or end state] clearly and at useful scale. Preserve [approved character or object attributes] only from their assigned sources. Emphasize correct contact, joint orientation, weight support, overlap, and force direction. Keep background and style neutral so they do not become competing constraints.
```

## Repair checklist

- Enlarge the attribute the reference is meant to control.
- Remove visual elements outside its responsibility.
- Correct source conflicts before adding prompt detail.
- Mask replaced people or objects rather than asking the model to ignore them.
- Repair geometry, contact, text, or materials before applying dramatic styling.
- Save the successful repair as a new canonical version.

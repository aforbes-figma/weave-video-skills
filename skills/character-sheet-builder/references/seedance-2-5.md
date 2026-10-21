# Seedance 2.5 Character-Sheet Reference

Use this reference for Seedance character preparation, especially when face identity must survive medium or wide video framing.

## Current public capabilities and production implications

As of 2026-08-28, Seedance 2.5 publicly supports up to 30 image, 10 video, and 10 audio references in one generation. It can reason across visual composition, scenes, styles, characters, and props; public examples explicitly map named references to different subjects and responsibilities. It also supports motion and blocking references and reports improved multi-character appearance and voice stability.

When current limits, supported media types, or editing features affect a production decision, verify the latest official model guidance before relying on these dated capabilities.

Apply those capabilities conservatively:

- Treat input limits as capacity, not a recommended pack size. Begin with the fewest references that fully establish the planned shots.
- Assign every reference one explicit responsibility in the final video prompt: identity, body and wardrobe, expression and teeth, prop, location, style, motion, blocking, or audio.
- Use stronger wording only for the attribute a reference owns, such as “strictly follow Reference 1 for the lead character's face and hair.” Do not let two references compete for the same attribute without declaring which one wins.
- Keep one canonical image per character when possible. Add dedicated references only for details the core image cannot carry at useful resolution.
- Prefer a motion or blocking reference for gait, action paths, pose transitions, and camera-relative movement instead of crowding those responsibilities into the identity sheet.
- For multiple characters, maintain a separate canon and numbered reference map for each person even though the model can accept them in one generation.
- Expect extra risk in complex physical interaction and multi-subject scenes. The model's own public release notes acknowledge remaining room for improvement in those cases; use simpler blocking, cleaner occlusion, or separate beats when identity stability matters more than spectacle.
- When clothing, hair, gait, or lighting interaction is important to the shot, define or reference it explicitly. Do not assume a neutral portrait establishes how those elements behave in motion.

The detailed sheet layouts below remain practitioner-derived heuristics. They are not published requirements of the model.

## Working hypothesis

Seedance can treat every visible face in a supplied sheet as a candidate identity. Small or inconsistent faces in body panels may compete with the intended portrait and cause drift. Design the primary reference so there is one unmistakable facial authority and no low-resolution facial alternatives.

This is a practitioner-derived generation heuristic, not an official platform guarantee. Validate it against the current workflow when the cost of failure is high.

## Input quality gate

- Prefer sharp, evenly lit, unobstructed source images with natural perspective.
- Use a neutral or softly natural facial expression for the canonical identity source.
- Avoid sunglasses, masks, heavy beauty filters, motion blur, extreme expressions, and deep shadows across identity-critical features.
- When replacing a person already visible in a scene reference, mask or neutralize the old face before conditioning on the new identity. Do not ask the model to reconcile two competing faces in the same region.
- Build the pack in stages: establish identity first, then body and wardrobe, then expressions or difficult poses. Promote each approved result as the source for the next stage.
- When the target supports a reusable trained identity, use varied clear single-subject images across useful angles, expressions, and lighting rather than a dense composite sheet. Exclude group shots, severe occlusion, heavy filters, and contradictory identity states, and follow the target platform's current input requirements.

## Primary sheet anatomy

### Canonical portrait

- Show one visible face total.
- Allocate roughly 25–50% of the sheet to the portrait; favor the larger end when identity is more important than wardrobe construction.
- Use a front or gentle three-quarter head-and-shoulders view.
- Keep the expression neutral or softly natural unless another expression dominates the clip.
- Preserve sharp eyes, skin texture, hairline, ears when visible, mouth shape, facial hair, marks, and age presentation.
- Avoid beauty lighting, extreme lens perspective, heavy grading, deep shadow, occlusion, and shallow focus that hides identity details.

### Body panels

- Include front and back views by default. Add a side view only when fit, silhouette, gait, or side action matters.
- Show the complete body from neck to footwear at consistent scale.
- Keep the stance neutral, weight balanced, arms relaxed, hands visible, and clothing unobstructed.
- Preserve garment fabric, color, stitching, closures, collar, sleeves, cuffs, trouser or skirt construction, accessories, and footwear.
- Omit the head above the neck on front and side panels by blending that region cleanly into the background.
- Retain the back of the head only when hairstyle construction is important and no face is visible; otherwise omit it for a cleaner single-authority sheet.

### Background and capture

- Start with a flat neutral mid-gray near `#808080`.
- Give every view its own rectangular mid-gray panel box. Separate panels with visible gutters and consistent outer margins.
- Keep each subject, garment, shadow, and background fully contained inside its panel; never allow any content to overlap or cross a panel boundary.
- Use a subtle thin neutral outline only when it materially clarifies the boxes. Treat it as functional separation, not decoration.
- Keep panel backgrounds seamless and consistent within their boxes.
- Use soft neutral studio light, restrained shadows, crisp focus, and natural skin and fabric texture.
- Use low-distortion portrait capture for the face and low-distortion full-body capture for the body panels. Do not rely on an arbitrary lens number when the generator interprets it inconsistently.
- Remove captions, panel labels, graphic borders, color swatches, props, logos not worn by the character, and decorative layout elements.

## Recommended layouts

### Three-panel primary sheet

Use for most identity-and-wardrobe needs:

1. Large canonical portrait.
2. Headless full-body front view.
3. Headless full-body back view.

Let the portrait panel occupy roughly 40–45% of the usable width. Divide the remaining width evenly between the two body panels after gutters. Keep all three panels fully separate and aligned to common top and bottom margins.

### Four-panel primary sheet

Use only when side silhouette materially affects the shot:

1. Large canonical portrait.
2. Headless full-body front view.
3. Headless full-body back view.
4. Headless full-body side view.

Do not reduce the portrait below a useful identity scale merely to fit the fourth panel. If necessary, move the side view to a separate body reference.

### Separate smile or dialogue reference

When the character will smile, speak with visible teeth, shout, or laugh, create another image containing one large face only. Match identity, hair, makeup, lighting neutrality, and wardrobe neckline to the primary portrait. Show the exact mouth state needed. Treat teeth as identity-critical; do not let the model silently invent them from a closed-mouth portrait.

For a real person whose dental appearance must be factual, require a clear smiling or open-mouth source photo. If none is available, flag teeth as unsupported rather than claiming consistency. For a fictional character, generate a dental appearance deliberately, have the user approve it, and then treat that single approved portrait as immutable.

Do not place neutral, smiling, profile, and three-quarter faces together on the primary Seedance sheet. A multi-face casting grid may be useful during character development, but split it into single-face images before supplying references to video generation.

## Copy-ready primary-sheet prompt template

Replace every bracketed field and remove irrelevant clauses.

```text
Using the supplied image(s) as the exact [identity / wardrobe / body] reference, create one high-resolution production character sheet for Seedance video generation on a seamless flat neutral mid-gray background near #808080.

LAYOUT: a clean landscape [three/four]-panel composition with no text or decorative graphics. Place every view inside its own fully separate rectangular panel box. Use generous, clearly visible vertical gutters and consistent outer margins. No subject, garment, shadow, or background from one panel may overlap or cross into another. Use a subtle thin neutral outline only if needed to make the boxes unmistakable. The canonical identity portrait occupies [40–45%] of the usable width and is the only visible face anywhere on the sheet.

IDENTITY PORTRAIT: one large, sharp [front / gentle three-quarter] head-and-shoulders portrait of [character description], [neutral / softly natural] expression, eyes clearly visible, exact [hair, skin, facial structure, facial hair, marks, makeup, and age presentation]. Preserve the supplied identity without beautification or reinterpretation.

BODY VIEW 1: full-body straight front view from neck to footwear, with everything above the neck smoothly omitted and blended into the same gray background. Neutral balanced stance, arms relaxed, hands and footwear unobstructed. Preserve exact body proportions, silhouette, wardrobe, fabric, color, construction, closures, accessories, and footwear.

BODY VIEW 2: full-body straight back view from neck to footwear, same scale, stance, body, and wardrobe, showing rear garment construction and footwear heels. [Omit the head completely / retain only the back of the hairstyle with no face visible].

[BODY VIEW 3: full-body side view from neck to footwear, same scale and wardrobe, showing side silhouette and garment drape, with everything above the neck smoothly omitted into the background.]

CAPTURE: soft even neutral studio lighting, crisp focus, low perspective distortion, natural skin and fabric texture, restrained shadows, consistent scale and color across all panels.

EXCLUDE: panel overlap, shared panel backgrounds, subjects crossing gutters, cropped panel contents, any additional visible face, duplicate portrait, facial features on body panels, expression grid, tiny face, text, labels, captions, color swatches, prop callouts, decorative border, moodboard styling, inconsistent outfit, altered accessories, clipped hands or feet, masks, blur, censor bars, holes, darkness, cut surfaces, gore, or horror imagery.
```

## Copy-ready smile-reference prompt template

Use this template only with a source that establishes the required teeth, or when intentionally establishing and approving a fictional character's dental appearance.

```text
Using the supplied canonical portrait as the exact identity reference, create one high-resolution head-and-shoulders studio portrait of the same person with [precise expression and mouth state]. Show one face only, large in frame. Preserve the exact facial structure, skin tone and texture, eye color, hairline, hairstyle, facial hair, marks, makeup, age presentation, and wardrobe neckline. Render the teeth and mouth anatomy naturally and consistently with the person. Use a seamless neutral mid-gray background, soft even studio light, crisp facial detail, and restrained shadows. No additional faces, inset views, expression grid, text, props, dramatic grading, beauty retouching, or identity reinterpretation.
```

## Repair workflow

When reviewing an existing sheet:

1. Identify every visible facial render.
2. Select the sharpest, most accurate portrait as the canonical face.
3. Enlarge it to at least one quarter of the sheet.
4. Remove or replace faces from body panels using a clean neck-up omission blended into the background.
5. Remove expression grids, tiny detail panels, text, swatches, and unrelated props.
6. Recompose every remaining view into a distinct non-overlapping panel box with clear gutters and consistent margins.
7. Normalize body-panel scale, stance, wardrobe, lighting, and background.
8. Move any necessary smile, teeth, or expression coverage into separate one-face images.
9. Recheck that the body views still communicate proportions, silhouette, garment construction, hands, accessories, and footwear.

## Failure diagnosis

| Symptom | Likely reference problem | Repair |
|---|---|---|
| Face changes in wide shots | Small body-panel faces compete with portrait | Remove body-panel faces and enlarge the canonical portrait |
| Mouth or teeth change | No authoritative open-mouth reference | Add one separate large smile or dialogue portrait |
| Wardrobe mutates | Body views are small, obstructed, or inconsistent | Enlarge consistent front/back views and remove clutter |
| Body proportions drift | Portrait-only reference or distorted body pose | Add neutral low-distortion full-body views |
| Hair changes from rear angle | No rear hairstyle evidence | Retain a face-free back-of-head view or add a dedicated rear-hair reference |
| Sheet produces mixed styling | Uneven lighting, grading, or backgrounds | Normalize to neutral studio capture and mid-gray |
| Model copies unwanted graphics | Labels, swatches, borders, or props appear | Remove all non-character visual information |
| Views bleed into one another | Subjects or backgrounds cross panel boundaries | Recompose into fully separate boxes with clear gutters and consistent margins |

## Video-production handoff

Return references in this form:

```text
Reference 1 — Character Core
Controls: canonical face, hair, body proportions, default wardrobe, accessories, footwear.
Exact: [list].
May vary: expression, pose, lighting, and environment only as directed by the shot.

Reference 2 — Smile / Dialogue Face (optional)
Controls: mouth shape, teeth, and named expression.
Exact: identity and dental appearance.
May vary: head angle only as directed by the shot.

Unsupported details: [anything the references do not establish].
```

The video prompt should explicitly map each reference to these responsibilities and should not ask one reference to override another on the same attribute.

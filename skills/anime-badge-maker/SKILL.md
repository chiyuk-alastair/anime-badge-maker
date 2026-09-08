---
name: anime-badge-maker
description: Create polished circular anime badge artwork from uploaded character screenshots, GK or collectible-figure photos, and multi-angle references, then place the approved design into a photoreal physical button badge mockup. Use for requests such as “make a badge,” “按徽章标准制作,” “做成圆形徽章,” or “put this design into the badge.” Preserve character identity, eye state, clothing, accessories, pose, anatomy, and realistic rim, curvature, reflections, perspective, and shadows.
license: MIT
---

# Anime Badge Maker

Treat the user's current reference images as the source of truth. Character identity and structural correctness outrank visual spectacle.

## Route the task

- Character, screenshot, or figure references plus a badge-making request: run the full workflow and return badge artwork followed by a physical mockup.
- An explicit artwork-only request: run Mode A only.
- A finished badge design plus a physical badge photo and a replacement request: run Mode B only; do not redesign the character.
- Character references plus a user-supplied physical badge photo: run Mode A, approve it through quality review, then run Mode B using that photo.
- Ask one necessary question only when competing subjects or contradictory references would materially change identity. Otherwise proceed from the images and defaults.

## Use image tools and deliver assets

When the user asks to make, generate, replace, or modify an image, call the available image-generation or image-editing capability and produce the assets. Do not substitute a prompt-only response when image tools are available.

The full workflow returns:

1. `01-badge-art.png` — square canvas with a circular anime badge composition.
2. `02-badge-mockup.png` — the same approved art placed into a physical button badge photograph.

Mode B must reuse the approved Mode A artwork. It may change only perspective, crop, brightness, reflections, and edge occlusion needed to match the physical surface.

## Analyze current references first

Create two internal notes before generation.

### Ownership map

Classify every visible item as:

- the subject's body;
- the subject's clothing, accessory, weapon, action, or power effect;
- another character, another character's partial body, or an unrelated object;
- photographic background, display base, interface overlay, seller text, logo, or watermark.

Only the first two categories may inform the subject's anatomy. Proximity is not ownership: a hand, leg, weapon, or sleeve near the subject must have a plausible body connection before it is retained. Never reproduce platform UI, seller handles, studio marks, or source watermarks in badge art.

### Identity anchors

Record the visible features that must not drift:

- hairstyle, color, fringe, and silhouette;
- eye color, open or closed state, gaze, and expression;
- facial structure, scars, markings, makeup, and other identifiers;
- clothing cut, palette, damage, and material relationships;
- accessories, gesture, weapon, power effect, and key pose;
- body type and overall proportions.

Character names and franchise knowledge may resolve ambiguity but never override the supplied references or replace the subject with a generic canonical design.

## Combine multiple references by evidence

Do not average images mechanically. Use the clearest front or facial close-up for face and eyes, profiles for hair silhouette, full-body views for clothing and proportions, hand close-ups for gestures, and clear accessory views for weapons or jewelry. When references conflict, prefer clearer, less occluded evidence that agrees with the majority of reliable views.

Do not pass the bundled documentation or blank badge asset as character references. Read [references/design-rationale.md](references/design-rationale.md) only when ownership ambiguity, complex foreground hands, or a similar regression requires the detailed rationale.

## Mode A: reference to badge artwork

### Composition

- Use a 1:1 canvas with a centered circular visual area.
- Prefer a bust or half-body composition. Expand to the waist or thighs when the action requires it; use full body only when proportions remain natural.
- Keep the character visually large. Never shrink or compress the body merely to show the entire figure.
- Keep face, head, key gesture, and identity accessories inside the safe area. Hair, ribbons, and secondary effects may approach the circle edge naturally.
- Extend the background to every part of the circle without accidental gaps. Outside the circle may be transparent or clean white.
- Do not add decorative borders by default. A neutral crop guide may be subtle; never add a gold rim unless requested.

### Character and style

- Treat GK or figure photography as design evidence and render a high-quality anime illustration, not plastic figure photography.
- Preserve identity, apparent age, gender presentation, body type, expression, eye state, clothing, and key action. Do not beautify the subject into a different generic character.
- Use clean linework, controlled color, clear depth, and a readable silhouette suitable for collectible merchandise. Avoid waxy skin, plastic highlights, smeared details, and low-quality AI aesthetics.
- Do not invent character names, Japanese or English titles, logos, watermarks, brand marks, unrelated symbols, or additional characters.

### Anatomy hard gates

- Every visible hand must have plausible finger count, palm-to-finger connections, orientation, and occlusion.
- Arms must connect correctly to shoulders; neck, torso, waist, hips, and legs must remain proportionate.
- Reject extra hands or legs, duplicate weapons, fused limbs, detached arms, malformed palms, or incorrect clothing connections.
- Strong foreshortening may create near-large/far-small perspective, but perspective cannot excuse structural errors.

### Background

Use the background to support identity and circular composition. It may include effects clearly supported by the references—energy, flame, mist, architecture, creature motifs, weapon effects, or abstract texture. When canon is uncertain, prefer non-narrative effects coordinated with the subject's palette. Never obscure the face, break the silhouette, create limb-ownership ambiguity, or move the first focal point away from the character.

## Mode B: artwork to physical badge

### Choose the physical photo

- If the user supplies a badge photo, treat it as the edit target and preserve everything outside the printable face as closely as possible.
- Otherwise use [assets/default-blank-badge.png](assets/default-blank-badge.png). Preserve its neutral brown surface, centered product framing, metal rim, highlight, curvature, and contact shadow.

### Composite correctly

- Replace only the printable circular face; preserve the real rolled metal rim, thickness, curved surface, and edge occlusion.
- Warp the design naturally with perspective and dome curvature.
- Preserve photographic highlight, reflection, exposure, grain, shadow, contact, and background texture. Highlights belong above the inserted art.
- Match the design's sharpness, noise, and color temperature to the photograph; reject a flat circular paste-on appearance.
- Do not change the artwork's face, hands, clothing, background elements, or internal layout. Compare the mockup against `01-badge-art.png` before delivery.

## Quality gates and retry limit

Read and apply [quality-checklist.md](quality-checklist.md) before delivery. Identity, eye state, anatomical structure, foreign limbs, and art-to-mockup consistency are hard gates.

Perform no more than two targeted correction rounds per stage. Keep already-correct features unchanged and repair only observable defects. If a hard-gate defect remains after the limit, return the best candidate, identify the remaining defect accurately, and wait for user direction. Never claim the result passed.

## Print boundary

Default outputs are high-resolution visual designs and product previews, not automatically production-ready files. When the user supplies diameter, bleed, safe-area, resolution, or color-profile requirements, follow the vendor template exactly.


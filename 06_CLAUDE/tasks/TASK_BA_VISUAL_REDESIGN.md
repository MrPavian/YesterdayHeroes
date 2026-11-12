# TASK — B.A. VISUAL REDESIGN: REALISTIC ADVENTURE PIXEL ART

**Priority:** Critical  
**Status:** Required before any further B.A. animation production  
**Scope:** Visual correction and approval only; do not continue the previous sprite pipeline.

## Read first
- `MASTER_CONTEXT.md`
- `05_TECHNICAL/pixel_art_animation_standard.md`
- `02_CHARACTERS/CHARACTER_ROSTER.md`
- `06_CLAUDE/tasks/TASK_PIXEL_ART_PILOT_BA.md`

## Problem
The previous B.A. animation concepts look compressed/stubby and too cartoon-like. They do not preserve the body proportions and visual identity of the supplied B.A. master sheet. They are rejected and must not be used as production assets.

## New visual target
Create a hand-pixelled, realistically proportioned classic 1990s point-and-click adventure look, with the visual quality and grounded proportions associated with classic LucasArts adventure art such as Indiana Jones and the Fate of Atlantis. This is a style reference only; do not copy its sprites, character art, backgrounds or assets.

## Non-negotiable B.A. design fidelity
Use the user's supplied B.A. master sheet as the single source of truth. Preserve:
- broad, massive shoulders and chest;
- powerful, muscular upper and lower arms;
- adult torso proportions and plausible waist;
- long, strong legs proportionate to torso;
- recognizable head, mohawk, beard and face;
- denim vest, red shirt, gold chains/bracelets, olive cargo trousers and heavy boots;
- the overall adult, heavy, imposing body presence.

Do not enlarge the head, shorten the legs, shrink the torso, inflate hands, or simplify the silhouette into a cartoon body. Do not use thick black outlines as a universal shortcut. Use deliberate pixel clusters, material shading, highlights and shadows to communicate form.

## Revised workflow
1. Inspect the original master sheet; never overwrite it.
2. Create a proportion/scale analysis using front, back and profile views.
3. Establish a new character pixel scale and canvas based on the master sheet; do not assume 48x64 or 64x80 in advance.
4. Produce one new front-facing idle pose and one walk keyframe only.
5. Compare directly against the master sheet at native pixel scale and intended in-game scale.
6. Obtain visual approval before expanding to a full walk cycle or all eight directions.
7. Only after approval, continue with eight-way idle/walk using the existing direction standard.

## Rejection criteria
Reject if:
- the figure appears short, squat, chibi or cartoonish;
- head/body ratio differs noticeably from the master;
- leg length, shoulder width or arm volume are reduced;
- costume, jewelry, hairstyle or beard changes;
- pixel edges are blurry or artificially filtered;
- the figure no longer reads as the same B.A. master-sheet design.

## Deliverables
- Proportion analysis and chosen pixel scale.
- One front idle pose.
- One front walk keyframe.
- Side-by-side comparison against the original master reference.
- Updated asset notes; do not mark anything approved until the project initiator approves it.

## Restrictions
- Do not generate a full 8-direction sheet yet.
- Do not reuse or retouch the rejected compressed/cartoon drafts as the final base.
- Do not claim the art is production-ready without visual approval.
- The project initiator / ChatGPT handles visual asset creation and visual QA; Claude handles technical integration after approval.

# Character Animation Pipeline — YESTERDAY HEROES

**Status:** Proposed production standard; validate with one pilot character before bulk production.  
**Design master:** The approved B.A. Baracus character sheet remains the visual identity reference, not an animation sheet.

## 1. Separate the deliverables

Every playable character has three distinct asset layers:

1. **Character design sheet** — front, back, side, portrait, clothing, proportions and palette. This is the visual canon.
2. **Pose/reference sheet** — key poses for locomotion, interaction and character-specific actions. It is for consistency and review, not directly imported as a sprite atlas.
3. **Animation assets** — frame sequences or a rigged character, exported in engine-ready format with metadata.

Never treat a multi-character collage or a turnaround sheet as a production sprite sheet.

## 2. Recommended first implementation

Use frame-based 2D sprite animation for the initial visual prototype. It gives precise control over the hand-drawn/pixel-retro look and avoids the rubbery appearance that poorly prepared skeletal rigs can create. Keep skeletal animation as a possible later option for characters with many reusable motions.

Before generating large quantities of frames, validate the chosen camera angle, sprite scale, outline, palette, frame cadence and export format in a playable Three.js test scene.

## 3. Shared animation vocabulary

Core baseline for a human playable character:

| State | Suggested frames | Notes |
|---|---:|---|
| idle | 4–6 | subtle breathing / weight shift |
| walk | 6–8 | loopable |
| run | 6–8 | loopable, stronger body lean |
| jump | 5–8 | anticipation, airborne, landing |
| crouch | 3–4 | enter, hold, exit |
| sit | 3–4 | sit down, idle, stand up |
| climb | 6–8 | only where level design needs it |
| interact | 4–6 | generic reach / use |
| talk | 3–5 | restrained mouth/head movement |
| use_item | 3–5 | may be character- and item-specific |
| hit_react | 4–6 | non-graphic slapstick reaction |
| combat/action | 6–10 | only if required by the episode |

Not every character needs every state. The game design determines which states are actually used.

## 4. Direction policy

For a classic point-and-click adventure, begin with four directions (front, back, left, right) if the camera and room navigation support it. Add diagonals only if the prototype demonstrates a clear visual need. Do not commit to eight directions before validating the camera perspective and asset workload.

## 5. Sprite production constraints

- Establish one canonical character height and baseline grid in the prototype; do not guess dimensions independently for every character.
- Keep the pivot / foot baseline consistent across frames so characters do not jitter.
- Keep frame bounds and transparent padding consistent within each animation.
- Maintain identical costume, props, lighting direction and palette across frames.
- Loops must begin and end in compatible poses.
- Use separate animations for transitions (e.g. idle-to-walk) only where they improve readability.
- Keep original approved reference art immutable; edited frames and exports go in separate folders.
- Use transparent PNG frames or a packed atlas with a metadata file. Choose one format after the prototype; do not mix formats ad hoc.
- Store animation names, frame order, frame duration, loop flag, pivot and source reference in metadata.

## 6. Suggested directory convention

```text
assets/
  characters/
    ba_baracus/
      reference/
        master_sheet.png
        pose_sheet.png
      animations/
        idle/
        walk/
        run/
        jump/
        crouch/
        sit/
        climb/
        interact/
        talk/
        use_item/
      atlas/
      animation_config.json
```

Repeat the same structure only for states actually used by that character. Use stable slugs, not historical sheet numbers, as file identifiers.

## 7. Pilot acceptance test

B.A. Baracus is the pilot because his existing master sheet is the approved visual standard.

The pilot is accepted only when:
- the design matches the approved master sheet;
- front, back and side orientation remain consistent;
- idle, walk, run and interact play without visible foot sliding or frame jitter;
- the animation loops cleanly;
- Three.js can load and switch states from a simple state machine;
- the asset can be replaced without changing game logic;
- Claude receives a repeatable prompt/specification and export convention.

Only after acceptance should the same pipeline be applied to the remaining roster.

## 8. Production caution

A character turnaround is not enough to infer unseen anatomy, clothing folds or prop placement in every motion. Each character needs approved key poses before full frame production. Generative images may drift between frames; inspect and correct continuity before importing them into the game.

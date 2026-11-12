# TASK — VEHICLE ASSET AUDIT & KITT VERTICAL SLICE PLAN

**Priority:** High  
**Type:** Repository audit / technical planning  
**Status:** Ready for Claude  
**Do not begin final vehicle art production in this task.**

## Read first
1. `MASTER_CONTEXT.md`
2. `05_TECHNICAL/vehicle_animation_cinematic_system.md`
3. `05_TECHNICAL/vehicle_asset_inventory.md`
4. `05_TECHNICAL/pixel_art_animation_standard.md`
5. `02_CHARACTERS/CHARACTER_ROSTER.md`
6. `assets/ASSET_MANIFEST.md`

## Goal
Audit the actual local vehicle reference assets and prepare a small, engine-neutral K.I.T.T. vehicle/cinematic vertical slice plan that honors the 50/50 target between cinematic presentation and direct player interaction.

## Part A — Actual asset audit
For each of the six confirmed vehicles:
- K.I.T.T.
- F.L.A.G. Mobile Unit
- A-Team-Van
- Airwolf
- GMC Sierra Grande / K-2500 Stunt-Truck
- Ecto-1

Report:
- Whether the file actually exists in the current workspace/repository.
- Exact relative path and filename.
- Pixel dimensions, format, color mode, alpha/transparency status.
- File size and SHA-256.
- Whether it is a master/reference sheet, a collection image, or a production sprite sheet.
- Visual issues and missing views/parts.
- Never infer existence from a Markdown manifest alone.

If an asset is missing, mark it missing. Do not create fake files, placeholder links or invented paths. Do not overwrite originals.

## Part B — Vehicle animation requirements
For each confirmed vehicle, map only relevant states from the vehicle specification. Identify which parts should be independently animated (e.g. wheels, rotors, scanner, lights, doors, trailer components) and which need full-body sprite changes. Do not force 8-way directions on all vehicles.

## Part C — K.I.T.T. vertical slice plan
Prepare a concise implementation proposal covering:
1. K.I.T.T. idle/engine/scanner presentation.
2. Michael entering and control handoff.
3. Player-controlled acceleration, braking, steering/evasion and route selection.
4. At least three distinct hazards.
5. Turbo Boost as a player-triggered ability with readable preparation and cooldown/availability rules.
6. Cinematic set-piece and resolution.
7. Skip behavior and deterministic story-flag outcomes.
8. Keyboard/gamepad input mapping proposal.
9. Engine/rendering assumptions and what must be validated in the engine comparison.

Target approximately 50% cinematic presentation and 50% meaningful player interaction across the complete sequence. Avoid QTE-only design.

## Part D — Technical recommendation
- Inspect the existing repository before proposing architecture.
- Keep vehicle profiles and sequence data separate from engine-specific code.
- Propose the smallest testable prototype; do not implement a large system prematurely.
- Identify risks, dependencies, and measurable acceptance criteria.
- Do not decide Three.js vs Phaser; the engine decision remains open.

## Deliverables
Create/update:
- `07_ROADMAP/vehicle_asset_audit.md` — actual audit results, including missing assets.
- `06_CLAUDE/tasks/TASK_KITT_VEHICLE_VERTICAL_SLICE.md` — implementation plan and acceptance criteria.
- Update `07_ROADMAP/progress.md` with what was actually inspected and what remains open.

## Restrictions
- No final art generation or sprite editing in this task.
- No fictional asset paths or unsupported assumptions.
- No engine selection.
- No unapproved story canon changes.
- Run relevant checks if code is changed; if this remains documentation-only, say so.

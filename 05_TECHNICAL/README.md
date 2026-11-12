# Technical Design

Die technische Architektur wird vor Produktionsbeginn durch einen vertikalen Prototyp validiert.

## Verbindliche Grafikentscheidung

- **Grafikstil:** handgepixelte Pixel-Art im Geist klassischer 1990er-Adventure-Spiele.
- **Bewegungsrichtungen:** acht Richtungen (S, SW, W, NW, N, NE, E, SE).
- **Animations- und Produktionsstandard:** [pixel_art_animation_standard.md](pixel_art_animation_standard.md) — verbindliche Spezifikation für Auflösung, Frame-Raster, Pivot/Fußanker, Animationen, Dateiformate, Pipeline und QA.

## Geplante technische Dokumente
- `architecture.md` — Architektur und Module
- `engine.md` — Engine-Vergleich und Entscheidung
- `asset_pipeline.md` — Grafiken, Animationen, Audio und Content-Import

## Vorläufige Kandidaten
- Three.js für 2.5D-/2D-gestützte Darstellung.
- Phaser für klassisches 2D-Adventure.
- TypeScript und Vite als bevorzugter Entwicklungsstack.

Die Grafikentscheidung legt die Engine nicht fest. Three.js und Phaser müssen im Vertical Slice denselben Pixel-Art-Pilot darstellen können; insbesondere Skalierung, Pixel-Snap, 8-way-Facing und Sprite-Animation sind zu vergleichen.

# Coding Rules

Diese Regeln gelten unabhängig von der finalen Engine.

## Allgemein
- TypeScript bevorzugen, sofern der Stack dies bestätigt.
- Kleine Module mit klaren Verantwortlichkeiten.
- Keine unnötigen globalen Variablen oder versteckten Seiteneffekte.
- Fehlerfälle explizit behandeln.
- Konfiguration und Content nicht hart in Spiellogik einbetten.

## Daten
- Stabile IDs statt Anzeigenamen als Schlüssel verwenden.
- Storyflags zentral verwalten.
- Episodencontent validieren.
- Savegames versionieren und migrationsfähig halten.

## UI und Interaktion
- Hotspots müssen visuell und logisch klar definiert sein.
- Interaktive Zustände müssen Feedback geben.
- Inventarkombinationen müssen reproduzierbare Ergebnisse liefern.
- Dialogbedingungen zentral und testbar halten.

## Qualität
- Keine Platzhalter als fertige Features ausgeben.
- Keine ungetesteten Refactorings mit Featurearbeit vermischen.
- Nach Änderungen Build und Tests ausführen.
- Bei Fehlern Ursache dokumentieren statt sie zu kaschieren.


## Pixel-Art und Charakteranimation
- Verbindlich ist `05_TECHNICAL/pixel_art_animation_standard.md`; bei Grafik- und Animationsarbeit zuerst vollständig lesen.
- Charakterrichtungen sind S, SW, W, NW, N, NE, E, SE. Richtungsnamen und Mapping zentral halten.
- Pixel-Art-Texturen ohne Glättung rendern; ganzzahlige Skalierung und Pixel-Snap im Zielrenderer sicherstellen.
- Frame-Canvas, Pivot und Fußanker dürfen innerhalb einer Animation nicht springen.
- Spritesheets enthalten eine Animation und eine Richtung; Frames laufen von links nach rechts.
- Animationsdaten und Dateipfade deklarativ in JSON/Asset-Manifests halten, nicht im Gameplay-Code verstreuen.
- Fehlende Richtungen/Frames explizit behandeln; keine stillen Fallbacks auf zufällige oder falsche Animationen.
- Engine-Entscheidung bleibt offen. Keine Engine-spezifische Animationsarchitektur bauen, bevor der Vertical Slice den Renderpfad validiert hat.

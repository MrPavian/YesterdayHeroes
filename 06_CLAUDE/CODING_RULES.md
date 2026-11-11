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

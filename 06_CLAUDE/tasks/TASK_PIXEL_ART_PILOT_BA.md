# TASK — B.A. Baracus Pixel-Art-Animationspilot

**ID:** TASK_PIXEL_ART_PILOT_BA  
**Status:** Ready — Design-/Pipeline-Pilot  
**Priorität:** Hoch  
**Verbindliche Grundlage:** `05_TECHNICAL/pixel_art_animation_standard.md`

## Ziel

Den technischen Animations-Workflow vorbereiten und anschließend die separat von ChatGPT gelieferten, freigegebenen B.A.-Baracus-Pixel-Art-Assets in einen lauffähigen Testprototyp integrieren. Claude ist für Code, Datenstruktur, Asset-Import, Animation, Steuerung, Rendering und Tests zuständig. Claude erstellt ausdrücklich keine finalen Charaktergrafiken, Pose Sheets, Sprite-Frames oder Richtungsansichten. Die visuelle Produktion und Freigabe erfolgt durch ChatGPT und den Projektinitiator.

## Pflichtlektüre

1. `MASTER_CONTEXT.md`
2. `02_CHARACTERS/CHARACTER_ROSTER.md`
3. Alle vorhandenen B.A.-Referenzgrafiken und Master-Sheets im Repository/Projektarchiv
4. `05_TECHNICAL/pixel_art_animation_standard.md`
5. `06_CLAUDE/CODING_RULES.md`
6. Aktuellen Code- und Asset-Zustand prüfen; keine Dateien oder Grafiken als vorhanden voraussetzen, die nicht tatsächlich auffindbar sind.

## Arbeitspakete

### A. Asset-Audit
- Vorhandene B.A.-Master-Sheets und Referenzen lokalisieren.
- Prüfen, ob die tatsächlichen Bilddateien im Git-Repository liegen.
- Fehlende Quelldateien/Binaries klar benennen; keine Platzhalter als echte Assets ausgeben.
- Master-Sheet als Designreferenz festlegen.

### B. Technische Animationsplanung
- Aus dem freigegebenen Master-Sheet die technischen Anforderungen und asymmetrischen Merkmale erfassen; keine visuellen Änderungen am Design vornehmen.
- Datenmodell für Idle, Walk, Run und Interact sowie acht Richtungen vorbereiten.
- Framezahl, Timing, Pivot und Fußanker in der Konfiguration abbilden.
- Keine Pixel-Art-Frames oder Pose Sheets selbst zeichnen oder generieren. Diese werden separat von ChatGPT geliefert.

### C. Asset- und Datenstruktur
- Ordnerstruktur gemäß Animationsstandard anlegen.
- Beispielhafte, valide Charakter-JSON-Konfiguration erstellen.
- Asset-Manifest aktualisieren.
- Validator-Konzept oder automatisierte Prüfung für Dateiexistenz, Framegrößen, Frameanzahl und Richtungsabdeckung vorbereiten.

### D. Technischer Vertical Slice
- Bestehenden Engine-/Build-Stand prüfen; Engine nicht eigenmächtig als entschieden behandeln.
- Einen kleinen Testbereich mit B.A.-Sprite, Idle/Walk, acht Richtungen und Debug-Facing erstellen. Solange finale B.A.-Grafiken fehlen, ausschließlich klar markierte technische Debug-Grafiken (z. B. farbige Rechtecke oder neutrales Test-Mannequin) verwenden. Diese dürfen nicht als finale Charaktergrafiken ausgegeben werden.
- Pixel-Snap, nearest-neighbor, ganzzahlige Skalierung, Bewegungsnormalisierung und stabilen Fußanker prüfen.
- Wenn die Engine noch nicht feststeht, einen möglichst engine-neutralen Asset-/Datenprototyp erstellen und die Renderintegration als Engine-Vergleich dokumentieren.

### E. Qualitätssicherung
- Acht Richtungen und Animationsloops prüfen.
- Größen-/Positionssprünge, Flimmern, Filterunschärfe, Pixel-Halos und falsche Facing-Zuordnung prüfen.
- Tests/Build tatsächlich ausführen und Ergebnisse dokumentieren.

## Zuständigkeiten und Nicht-Ziele

**Claude übernimmt:** Projekt-/Asset-Audit, technische Ordner- und Datenstruktur, Sprite-Loader, Animationszustandsmaschine, 8-way-Facing, Diagonalnormalisierung, Pixel-Snap, Nearest-Neighbor, Testszene, JSON-Validierung, Integration gelieferter PNG-Sheets, Tests und Dokumentation.

**ChatGPT / Projektinitiator übernimmt:** Prüfung des B.A.-Master-Sheets, Pose Sheet und 8-Wege-Designreferenzen, finale Pixel-Art-Frames, visuelle Qualitätskontrolle und Übergabe der freigegebenen PNG-Exports.

Claude darf technische Debug-Grafiken nutzen, aber keine finalen B.A.-Assets selbst erzeugen. Fehlende Grafiken sind kein Grund, die technische Vorbereitung aufzuschieben.

## Akzeptanzkriterien

- Keine Designabweichung vom freigegebenen B.A.-Master-Sheet ohne Zustimmung.
- Technische Testszene funktioniert auch vor Lieferung der finalen Grafiken mit eindeutig gekennzeichneten Debug-Assets.
- Finale visuelle Abnahme ist ausdrücklich erst nach Lieferung der von ChatGPT erstellten Assets möglich.
- Richtungsstandard S, SW, W, NW, N, NE, E, SE wird exakt eingehalten.
- Framegröße, Pivot und Fußanker sind konsistent und dokumentiert.
- Idle und Walk sind mindestens als vollständiger Produktionsumfang geplant; ein erster Richtungs-Pilot ist technisch testbar.
- Dateinamen, Config und Asset-Manifest folgen dem verbindlichen Standard.
- Der technische Test weist Pixel-Snap und Nearest-Neighbor nach.
- Fehlende Binärdateien, Quelldateien oder Engine-Voraussetzungen werden als offene Punkte benannt.
- Roadmap und Changelog sind aktualisiert.

## Nicht-Ziele

- Keine vollständige Animation aller 25 Figuren.
- Keine endgültige Engine-Entscheidung ohne Vergleich.
- Keine unaufgeforderte Neugestaltung von B.A.
- Keine Übernahme kopierter Sprites oder fremder Spielgrafiken.

## Ergebnisbericht

Berichte: gefundene Assets, erzeugte Dateien, technische Entscheidungen, Tests mit tatsächlichen Ergebnissen, offene Blocker und nächster sinnvoller Schritt.

# TASK — B.A. Baracus Pixel-Art-Animationspilot

**ID:** TASK_PIXEL_ART_PILOT_BA  
**Status:** Ready — Design-/Pipeline-Pilot  
**Priorität:** Hoch  
**Verbindliche Grundlage:** `05_TECHNICAL/pixel_art_animation_standard.md`

## Ziel

Den ersten vollständigen, technisch integrierten Pixel-Art-Charakterpilot für YESTERDAY HEROES vorbereiten und umsetzen. B.A. Baracus dient als Referenz für die Pipeline, nicht als Anlass, den bestehenden Charakterentwurf eigenmächtig neu zu gestalten.

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

### B. Animationsdesign
- B.A.-Proportionen, Palette, Silhouette, Ausrüstung und asymmetrische Merkmale dokumentieren.
- Pose Sheet und acht Richtungsansichten spezifizieren bzw. erstellen, sofern die Bildwerkzeuge/Quelldateien verfügbar sind.
- Zunächst Idle und Walk priorisieren.
- Key Poses, Framezahl, Timing, Pivot und Fußanker definieren.
- Eine Richtung als Pilot produzieren und freigeben, bevor alle acht Richtungen umgesetzt werden.

### C. Asset- und Datenstruktur
- Ordnerstruktur gemäß Animationsstandard anlegen.
- Beispielhafte, valide Charakter-JSON-Konfiguration erstellen.
- Asset-Manifest aktualisieren.
- Validator-Konzept oder automatisierte Prüfung für Dateiexistenz, Framegrößen, Frameanzahl und Richtungsabdeckung vorbereiten.

### D. Technischer Vertical Slice
- Bestehenden Engine-/Build-Stand prüfen; Engine nicht eigenmächtig als entschieden behandeln.
- Einen kleinen Testbereich mit B.A.-Sprite, Idle/Walk, acht Richtungen und Debug-Facing erstellen.
- Pixel-Snap, nearest-neighbor, ganzzahlige Skalierung, Bewegungsnormalisierung und stabilen Fußanker prüfen.
- Wenn die Engine noch nicht feststeht, einen möglichst engine-neutralen Asset-/Datenprototyp erstellen und die Renderintegration als Engine-Vergleich dokumentieren.

### E. Qualitätssicherung
- Acht Richtungen und Animationsloops prüfen.
- Größen-/Positionssprünge, Flimmern, Filterunschärfe, Pixel-Halos und falsche Facing-Zuordnung prüfen.
- Tests/Build tatsächlich ausführen und Ergebnisse dokumentieren.

## Akzeptanzkriterien

- Keine Designabweichung vom freigegebenen B.A.-Master-Sheet ohne Zustimmung.
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

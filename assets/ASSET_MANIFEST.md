# Asset Manifest

Dieses Manifest beschreibt die im Repository vorhandenen bzw. vorbereiteten Referenzpakete. **Die Grafik-Produktionsübersicht steht zentral in [02_CHARACTERS/CHARACTER_ROSTER.md](../02_CHARACTERS/CHARACTER_ROSTER.md)** und führt Figuren, Fahrzeuge, historische Sheet-Nummern, Korrekturen und offene Aufgaben.

## Bereits vorbereitetes Referenzpaket

Die bisher auffindbaren 20 PNG-Referenzgrafiken wurden in ein Importpaket sortiert. Die vollständigen SHA-256-Prüfsummen, Dimensionen und Ursprungsdateinamen stehen in `reference-sheets/asset_manifest.json` im ZIP-Paket.

### Charakterbögen
| Zielpfad | Inhalt | Status |
|---|---|---|
| `reference-sheets/characters/character_ba_baracus.png` | B.A. Baracus | Master-Referenz |
| `reference-sheets/characters/character_hannibal_smith.png` | Hannibal Smith | Einzelbogen |
| `reference-sheets/characters/character_faceman_templeton_peck.png` | Face / Templeton Peck | Einzelbogen |
| `reference-sheets/characters/character_murdock.png` | Murdock | Einzelbogen |
| `reference-sheets/characters/character_macgyver.png` | MacGyver | Einzelbogen |
| `reference-sheets/characters/character_michael_knight.png` | Michael Knight | Einzelbogen mit Animationsreferenzen |
| `reference-sheets/characters/character_stringfellow_hawke.png` | Stringfellow Hawke | Einzelbogen |
| `reference-sheets/characters/character_alf_willie_tanner.png` | ALF und Willie Tanner | gemeinsames Sheet |
| `reference-sheets/characters/variants/character_alf_variant_014.png` | ALF | alternative Fassung |
| `reference-sheets/characters/variants/character_alf_variant.png` | ALF | alternative Fassung |

### Fahrzeuge und Objekte
| Zielpfad | Inhalt | Status |
|---|---|---|
| `reference-sheets/vehicles/vehicle_a_team_van.png` | A-Team-Van | Fahrzeugbogen |

### Sammel-Sheets und Roadmaps
Sammelbilder und Roadmap-Grafiken sind im ZIP-Importpaket dokumentiert. Sie sind Übersichten und dürfen nicht als fertige Einzel-Sprite-Sheets behandelt werden.

## Importstatus

- Die 20 auffindbaren PNG-Referenzgrafiken wurden in ein Importpaket sortiert.
- Die Bilddateien selbst sind laut letztem Repository-Stand **noch nicht in Git committed**.
- Die neueren Grafiken aus späteren Chat-Sitzungen (u. a. Ghostbusters, Fall Guy und Antagonisten) sind ebenfalls nicht automatisch im Repository enthalten.
- Vor dem nächsten Asset-Import Dateinamen, Abmessungen, Prüfsummen und Lizenz-/Rechtehinweise ergänzen.

## Regeln für Claude

- Vor Nutzung zuerst `02_CHARACTERS/CHARACTER_ROSTER.md` und dieses Manifest lesen.
- Sammelbilder sind keine automatisch verwendbaren Sprite-Sheets.
- Einzelne Charakterbögen sind Referenzvorlagen; Sprites müssen ggf. sauber ausgeschnitten, bereinigt und in Einzel-Animationen überführt werden.
- Originaldateien nicht überschreiben. Bearbeitete/exportierte Assets in getrennten Unterordnern ablegen.
- Jede Datei mit Lizenz-/Rechtehinweis und SHA-256-Prüfsumme im Manifest führen.

## Rechtehinweis

Die abgebildeten Figuren, Fahrzeugdesigns, Seriennamen und markanten Kennzeichen können urheber- oder markenrechtlich geschützt sein. Diese Grafiken sind Konzept-/Fan-Referenzen; vor einer öffentlichen oder kommerziellen Veröffentlichung müssen Rechte und Lizenzlage geklärt werden.
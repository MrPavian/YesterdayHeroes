# Vehicle Asset Inventory & Production Plan

> Stand: 2026-11-12  
> Grundlage: `02_CHARACTERS/CHARACTER_ROSTER.md`, `assets/ASSET_MANIFEST.md` und `05_TECHNICAL/vehicle_animation_cinematic_system.md`.

## 1. Verbindlicher Fahrzeugbestand

Es gibt aktuell **sechs bestätigte Fahrzeuge**. Diese Liste ist maßgeblich für die Fahrzeug-Animation und ersetzt frühere unvollständige Aufzählungen.

| Fahrzeug-ID | Fahrzeug | Zugehörigkeit | Referenz-Sheet laut Roster | Status |
|---|---|---|---|---|
| `kitt` | K.I.T.T. | Knight Rider | #012 | Sheet vorhanden; Layoutkorrektur / Neu-Ausrichtung prüfen |
| `flag_mobile_unit` | F.L.A.G. Mobile Unit | Knight Rider / Foundation | #013 | Einzel-Sheet vorhanden |
| `ateam_van` | A-Team-Van | A-Team | #005 | Einzel-Sheet vorhanden |
| `airwolf` | Airwolf-Hubschrauber | Airwolf | offen | Eigenständiges Fahrzeug-Sheet fehlt; zuerst Master-Sheet erstellen |
| `fall_guy_truck` | GMC Sierra Grande / K-2500 Stunt-Truck | The Fall Guy | #021 | Einzel-Sheet vorhanden |
| `ecto1` | Ecto-1, 1959 Cadillac Miller-Meteor Futura Duplex | Ghostbusters | #026 | Einzel-Sheet vorhanden |

**Wichtig zum Importstatus:** Die Roster- und Manifest-Einträge belegen vorhandene Referenzentwürfe aus früheren Grafik-Sitzungen. Laut `assets/ASSET_MANIFEST.md` sind die Bilddateien selbst noch nicht vollständig in Git committed. Claude muss daher vor einer technischen Integration die tatsächlichen Dateien im Arbeitsverzeichnis prüfen. Fehlende Dateien dürfen nicht durch erfundene Pfade oder Platzhalter als vorhanden ausgegeben werden.

## 2. Bewegungsprofile je Fahrzeug

### K.I.T.T. — erster Fahrzeug-Pilot
**Rolle:** intelligenter, präziser Straßenpartner.
- Basis: engine_off, idle, engine_start, accelerate, cruise, brake, stop, reverse.
- Fahrmanöver: turn_left, turn_right, lane_change, controlled_skid.
- Spezial: scanner, turbo_charge, turbo_boost. Weitere Modi nur nach Storyfreigabe.
- Darstellung: Karosserie-Neigung, Federung, Radrotation, Scannerlicht, Scheinwerfer und Auspuffeffekte.
- Vertical Slice: erste interaktive Verfolgungsfahrt mit 50/50 Inszenierung/Interaktion.

### F.L.A.G. Mobile Unit
**Rolle:** mobile Basis / Werkstatt / logistischer Stützpunkt, nicht primär Verfolgungsfahrzeug.
- Basis: parked_idle, engine_start, slow_drive, stop, lights_on/off.
- Aufbau: Zugmaschine und Auflieger als getrennte visuelle Komponenten, soweit die Referenz dies unterstützt.
- Interaktion: Zugang zur mobilen Basis, Werkstatt-/Ausrüstungsinteraktion, Ankunft und Abfahrt.
- Cinematics: Anfahrt, Positionieren, Aufbau als mobile Basis, Abfahrt.
- Keine aufwendigen Renn- oder Stuntanimationen priorisieren, solange die Story keine solche Szene benötigt.

### A-Team-Van
**Rolle:** Teamfahrzeug, Flucht und improvisierte Einsätze.
- Basis: idle, engine_start, accelerate, cruise, brake, reverse, stop.
- Manöver: tight_turn, drift, evasive_maneuver.
- Türen: door_open/close und team_boarding/team_exit.
- Story: Teammitglieder und ihre individuellen Fähigkeiten sollen in Ein-/Aussteige- und Fluchtszenen sichtbar werden.
- Improvisierte Umbauten sind episodenspezifische Set-Pieces, keine permanente Standardausstattung.

### Airwolf
**Rolle:** Lufttransport, Aufklärung und Luftverfolgung.
- Eigenständiges Master-Sheet ist noch zu erstellen; keine finale Spriteproduktion vor Freigabe des Designs.
- Rotorzustände: off, spinup, idle, flight_speed, spindown.
- Flugzustände: takeoff, hover, forward_flight, climb, descent, bank_left/right, landing.
- Effekte: Rotorwash, Staub, Vegetationsbewegung, Licht-/Systemeffekte.
- Vertical Slice erst nach KITT-Pilot und Airwolf-Master-Sheet planen.

### GMC Sierra Grande / K-2500 Stunt-Truck
**Rolle:** Colts Arbeits- und Stuntfahrzeug.
- Basis: idle, start, accelerate, cruise, brake, reverse, stop.
- Stunt: stunt_approach, takeoff, airborne, landing, suspension_recovery.
- Manöver: hard_turn, controlled_skid, obstacle_clearance.
- Besonderheit: Adventure-Erkundung soll Stuntvorbereitung beeinflussen. Colt untersucht Rampe, Absprungpunkt, Winkel und Landefläche vor der Actionsequenz.
- Schäden und Crashs nur einsetzen, wenn sie dramaturgisch begründet und spielerisch fair sind.

### Ecto-1
**Rolle:** schweres Einsatzfahrzeug für Geisterjagd und paranormale Störungen.
- Basis: idle, start, accelerate, cruise, brake, stop, reverse.
- Ausstattung: warning_lights, roof_equipment_active, paranormal_interference.
- Manöver: heavy_turn, evasive_maneuver.
- Effekte: Lichtreflexe, Geräteflackern, geister-/resonanzbedingte Störungen.
- Story: Fahrzeugausrüstung muss in Rätseln oder bei der Erkennung/Verfolgung paranormaler Phänomene relevant sein.

## 3. Priorisierte Produktionsreihenfolge

1. **K.I.T.T.** — vorhandenes Referenzsheet prüfen/korrigieren, anschließend Pilot für Fahrzeugcontroller, Kamera, Timeline und 50/50-Verfolgung.
2. **A-Team-Van** — vorhandenes Sheet prüfen; Tür-/Team-Interaktionen und Fluchtmanöver.
3. **GMC Sierra Grande / K-2500** — vorhandenes Sheet prüfen; Stuntphasen und Verbindung mit vorheriger Adventure-Erkundung.
4. **Airwolf** — zuerst Master-Sheet erstellen und freigeben; danach Rotor-/Fluganimationen.
5. **Ecto-1** — vorhandenes Sheet prüfen; Einsatz- und Paranormal-Effekte.
6. **F.L.A.G. Mobile Unit** — vorhandenes Sheet prüfen; mobile Basis, Ankunft/Abfahrt und Werkstattinteraktion.

Diese Reihenfolge ist eine Produktionspriorität, keine Story-Chronologie. Sie kann sich nach Episodenbedarf ändern.

## 4. Gemeinsame technische Regeln

- Fahrzeuge erhalten eigene Profile und State Machines; keine gemeinsame Einheitsanimation für alle Fahrzeugtypen.
- Sprite-/Perspektivbedarf hängt vom Kameramodell ab. Nicht pauschal acht Richtungen für jedes Fahrzeug erzwingen.
- Räder, Rotoren, Scanner, Warnleuchten und bewegliche Aufbauten möglichst als getrennte Animationslayer behandeln, sofern das Assetdesign es zulässt.
- Fahrzeuge benötigen einen konsistenten Boden-/Kontaktanker und definierte Kollisions-/Interaktionsbereiche.
- Bewegung und Kamera müssen während interaktiver Passagen lesbar bleiben.
- Cinematics sind überspringbar; Storyinformationen und Flags bleiben nach Skip konsistent.
- Animationen und Timeline-Events werden datengetrieben konfiguriert.
- Original-Referenzdateien bleiben unverändert; bereinigte Produktionsassets erhalten eigene Pfade und Manifest-Einträge.

## 5. Offene Prüfungen

- Vorhandensein und tatsächliche Abmessungen aller sechs Referenzbilder im lokalen Projekt prüfen.
- K.I.T.T.-Sheet #012 und F.L.A.G.-Sheet #013 visuell gegen das B.A.-Layout prüfen.
- Airwolf-Master-Sheet erstellen.
- Für jedes Fahrzeug entscheiden, ob die Szene mit Sprite-Ansichten, getrennten Komponenten, Parallax-/Pseudo-3D oder einer Mischform umgesetzt wird.
- Asset-Rechte und kommerzielle Nutzbarkeit vor Veröffentlichung klären.

## 6. Claude-Auftrag

Claude soll zunächst den lokalen Assetbestand gegen diese Liste prüfen und einen Bericht mit tatsächlichen Dateipfaden, Abmessungen, Transparenz, Dateigröße und Prüfsummen erstellen. Danach K.I.T.T. als technischen Pilot vorbereiten. Keine Assets erfinden, keine Master-Sheets überschreiben und keine Fahrzeugliste eigenmächtig erweitern.

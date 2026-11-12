# VEHICLE ANIMATION & CINEMATIC SYSTEM

> Status: Designentscheidung / verbindliche Zielvorgabe  
> Beschlossen: 2026-11-12  
> Projekt: YESTERDAY HEROES — The Last Great Timeline

## 1. Leitentscheidung: 50/50 Inszenierung und Interaktion

Fahrzeugsequenzen sollen sich wie spielbare Action-Szenen eines 1980er-Jahre-Abenteuerfilms anfühlen. Das Zielverhältnis beträgt ungefähr **50 % Inszenierung und 50 % direkte Spielerinteraktion**.

Das Verhältnis ist ein dramaturgischer Richtwert über eine komplette Sequenz, keine starre Sekundenregel. Eine Szene darf davon abweichen, wenn Rhythmus und Spannung profitieren.

**Inszenierung umfasst:** Kameraführung, Perspektivwechsel, Musik- und Sound-Cues, Dialoge, vorbereitete Stunts, Set-Pieces, Storyereignisse und Übergänge.

**Interaktion umfasst:** Lenken bzw. Flugsteuerung, Beschleunigen/Bremsen, Ausweichen, Routenentscheidungen, Einsatz von Spezialfähigkeiten, situative Aufgaben und taktische Entscheidungen.

Keine reine Quick-Time-Event-Kette. Der Spieler soll die Fahrzeugbewegung oder zumindest die entscheidenden Manöver tatsächlich steuern. Eingaben müssen verständlich, fair angekündigt und mit sichtbarem Feedback beantwortet werden.

## 2. Designziele

1. Jedes Fahrzeug besitzt eine eigene Bewegungsidentität und ein eigenes Animationsprofil.
2. Fahrzeuge sind erzählerische Akteure und keine austauschbaren Transportmittel.
3. Fahrzeugsequenzen verbinden Adventure-Erkundung, Action und Storyfortschritt.
4. Spielerentscheidungen haben nachvollziehbare Folgen, ohne jede Szene in ein hartes Fail-State-Rennen zu verwandeln.
5. Cinematics sind überspringbar; wichtige Informationen bleiben danach über Dialog, Journal oder Szenenstatus zugänglich.
6. Technische Systeme bleiben modular und datengetrieben. Keine Fahrzeugsequenz darf fest in die allgemeine Spiellogik eingebrannt werden.

## 3. Fahrzeug-Roster und individuelle Identität

Das bestätigte Ensemble umfasst mehrere Fahrzeuge. Die konkrete vollständige Liste ist mit dem aktuellen Fahrzeug-Asset-Roster abzugleichen, bevor finale Produktionsaufträge vergeben werden. Die folgenden Profile sind Designziele, keine abschließende Assetliste.

### KITT — Straßenfahrzeug / intelligenter Partner
- Idle: Scanner, Scheinwerfer, dezente Karosserie-/Federungsbewegung.
- Fahrt: Radrotation, Federung, Karosserie-Neigung, Lichtreflexe.
- Manöver: Beschleunigen, Bremsen, Kurven, Rückwärtsfahrt, kontrolliertes Schleudern.
- Spezial: Turbo Boost und weitere im Story-/Fähigkeitenkonzept freigegebene Modi.
- Cinematic-Momente: Scanner-Aktivierung, Cockpit-/Innenraumansicht, selbstständige Reaktion, Turbo-Sequenz.
- Spielgefühl: präzise, kontrolliert, technisch überlegen; KITT ist Partner und Dialogfigur.

### Airwolf — Hochleistungshelikopter
- Rotoren: aus, Hochlauf, Leerlauf, Reisegeschwindigkeit, Nachlauf.
- Flug: Start, Schweben, Vorwärtsflug, Steig-/Sinkflug, Kurven, Landung.
- Fahrwerk und Beleuchtung mit eigenen Zuständen.
- Effekte: Rotorwash, Staub, Vegetationsbewegung, Hitzeflimmern und ggf. Waffen-/Systemeffekte.
- Spielgefühl: schwer, kraftvoll, präzise; Flugmanöver brauchen räumliche Lesbarkeit und klare Gefahrenkommunikation.

### A-Team-Van — Teamtransport und improvisierte Flucht
- Türen/Schiebetür, Ein- und Aussteigen, Motorstart, Standlauf.
- Fahrt, Bremsen, Rückwärtsfahrt, enge Kurven und Drift.
- Teammitglieder können in geskripteten Momenten ein-/aussteigen oder aus dem Fahrzeug agieren.
- Spielgefühl: robust, improvisiert, teamorientiert; die Gruppe und ihre Zusammenarbeit stehen im Vordergrund.

### Colt Seavers' Stuntfahrzeug
- Beschleunigung, Bremsen, Kurven, Schleudern.
- Stunt-Sprung mit Anlauf, Absprung, Flugphase, Landung und Nachschwingen.
- Crash-/Schadenszustände nur soweit storygerecht und ohne unnötige Frustration.
- Spielgefühl: spektakulär, riskant und handwerklich vorbereitet. Colt kann Stunts planen und die Umgebung auf Rampen, Absprungpunkte und sichere Landeflächen untersuchen.

### Ghostbusters-Fahrzeug
- Ankunft, Warn-/Dachbeleuchtung, Türen und Geräteaufbauten.
- Fahrt mit sichtbarer Masse und Federung.
- Geister-/Anomalieeffekte, die das Fahrzeug und seine Ausrüstung beeinflussen.
- Spielgefühl: schwerfällig, zweckmäßig und leicht chaotisch; Ausrüstung ist für Rätsel und Geisterjagd relevant.

### Weitere Fahrzeuge
Weitere Fahrzeuge aus dem bestätigten Asset-Roster werden erst nach Abgleich der vorhandenen Master-Sheets und Storyrollen ergänzt. Keine neuen Fahrzeuge eigenmächtig als Kanon festlegen.

## 4. Animationsbibliothek

### Gemeinsame Basiszustände
- idle / engine_off
- engine_start / engine_stop
- acceleration
- cruise / drive
- brake
- turn_left / turn_right
- reverse
- stop
- door_open / door_close
- enter / exit
- damage / disabled (falls in der Szene erforderlich)
- special_action

### Fahrzeugspezifische Zustände
- KITT: scanner, turbo_charge, turbo_boost, pursuit_mode (nur nach Storyfreigabe).
- Airwolf: rotor_spinup, hover, takeoff, flight, maneuver, landing, rotor_spindown.
- Van: sliding_door, team_boarding, team_exit, drift, improvised_escape.
- Stuntfahrzeug: stunt_approach, takeoff, airborne, landing, recovery.
- Ghostbusters-Fahrzeug: equipment_active, warning_lights, paranormal_interference.

Nicht jedes Fahrzeug benötigt jede Animation. Profile sollen nur Zustände enthalten, die im Spiel tatsächlich verwendet werden.

## 5. Kamera und Darstellung

Die Kamera ist Teil des Erzählens und darf während einer Sequenz wechseln:
- Seiten-/Verfolgerkamera für Geschwindigkeit und Lesbarkeit.
- Heckkamera für Flucht und Verfolgung.
- Frontkamera für Konfrontationen.
- Cockpit-/Innenraumkamera für Dialoge und Entscheidungen.
- Weite Establishing Shots für Start, Landung und Ortswechsel.
- Kurze dynamische Kamerabewegungen für Stunts und Wendepunkte.

Kamerabewegungen dürfen die Steuerbarkeit nicht beeinträchtigen. Während interaktiver Passagen bleibt die Gefahrenzone sichtbar. Kameraschnitt und Steuerübergabe müssen eindeutig sein.

## 6. Verfolgungssequenzen: spielbarer 50/50-Aufbau

Eine typische Verfolgung hat fünf Phasen:

1. **Setup / Inszenierung:** Ziel, Gefahr und räumliche Situation werden etabliert. Der Spieler erkennt Fahrzeug, Verfolger und Fluchtoptionen.
2. **Interaktive Fahrt:** Spieler steuert Beschleunigen, Bremsen, Ausweichen und Spur-/Routenwahl.
3. **Set-Piece:** Ein vorbereiteter Höhepunkt (Straßensperre, Sprung, Engstelle, Tunnel, Brücke, Luftmanöver) wird filmisch inszeniert, bleibt aber durch rechtzeitige Spieleraktion beeinflussbar.
4. **Entscheidung / Konsequenz:** Alternative Route, Spezialfähigkeit, Schutz einer Person oder Sicherung eines Hinweises. Unterschiedliche Ergebnisse verändern den Szenenstatus.
5. **Auflösung:** Cinematic-Ausgang und Rückkehr in Adventure-Steuerung.

Interaktive Aufgaben müssen echte Spielhandlungen sein, nicht nur wiederholtes Drücken einer eingeblendeten Taste. Zulässige Formen sind z. B. Spurwahl, Hindernisnavigation, Timing beim Beschleunigen/Bremsen, begrenzte Spezialfähigkeit, Zielpriorisierung und kooperative Rollenverteilung.

## 7. Luftsequenzen

Airwolf-Sequenzen folgen denselben 50/50-Prinzipien, aber mit einer eigenen Steuerungsabstraktion:
- Höhe halten / steigen / sinken.
- Vorwärtsbewegung und Ausrichtung.
- Ausweichen und Positionieren.
- Energie-/Systemmanagement, wenn es dramaturgisch begründet ist.
- Rettungs-, Beobachtungs- oder Verfolgungsziele.

Die Steuerung soll bewusst zugänglich bleiben und kein Flugsimulator werden. Die Herausforderung entsteht aus räumlichen Entscheidungen, Timing, Sicht, Hindernissen und Missionszielen.

## 8. Story-Einsatz und mögliche Set-Pieces

Die folgenden Ideen sind Vorschläge zur weiteren Episodenentwicklung, noch keine verbindlichen Storyereignisse:

- **Erste KITT-Verfolgung:** KITT führt den Spieler aus einer gefährlichen Situation. Scanner und Turbo Boost werden zunächst als Fähigkeiten und später als interaktive Werkzeuge eingeführt.
- **Airwolf entdeckt eine Resonanzspur:** Ein Flug über ein Gebiet mit Chronal-Anomalien. Der Spieler muss Höhe und Position wählen, um Signale zu unterscheiden und eine sichere Route zu finden.
- **A-Team-Flucht:** Das Team muss ein improvisiertes Fahrzeug oder den Van einsetzen. Hannibals Plan, B.A.s praktische Fähigkeiten, Faces Improvisation und Murdocks unberechenbare Einfälle werden spielmechanisch relevant.
- **Colts Stuntsequenz:** Colt untersucht vorher die Umgebung und identifiziert Rampe, Absprungwinkel und Landefläche. Die spätere Stuntfahrt belohnt die vorherige Adventure-Erkundung.
- **Ghostbusters-Einsatzfahrt:** Paranormale Störungen beeinträchtigen Instrumente und Sicht. Der Spieler muss Ausrüstung und Route sinnvoll kombinieren.
- **Spätere Ensemble-Sequenz:** Mehrere Fahrzeuge arbeiten zeitgleich an einem Ziel. Wechsel zwischen Boden- und Luftperspektive, Funkdialog und Aufgabenverteilung verbinden die Teams.

Story-Regel: Fahrzeug-Set-Pieces müssen Chronal-Resonanz, Chronal-Anker, Figurenentwicklung oder Episodenhandlung voranbringen. Reiner Fanservice ist nicht ausreichend.

## 9. Konsequenzen und Schwierigkeitsdesign

Fehler sollen Spannung erzeugen, aber nicht unverhältnismäßig bestrafen:
- Ein verfehltes Manöver kann Zeit kosten, einen alternativen Weg erzwingen oder den Fahrzeugzustand verschlechtern.
- Ein schwerer Fehler darf eine Szene verändern, soll aber nach Möglichkeit eine spielbare Fortsetzung statt eines abrupten Game Over ermöglichen.
- Optionale Ziele können Hinweise, Ressourcen, Dialogvarianten oder spätere Vorteile freischalten.
- Zentrale Storyinformationen dürfen nicht ausschließlich hinter perfekter Fahrleistung liegen.
- Schwierigkeitsoptionen und Assistenzfunktionen sind im Vertical Slice zu prüfen.

## 10. Technische Architektur — Vorschlag, engine-neutral

VehicleSystem/
  core/
    VehicleController
    VehicleAnimator
    VehicleStateMachine
    VehicleCamera
    VehicleAudio
    VehicleProfile
  effects/
    DustParticles
    TireSmoke
    RotorWash
    Exhaust
    DamageEffects
    LightEffects
  cinematics/
    CinematicDirector
    CameraTracks
    TimelineEvents
    InputHandoff
    TransitionManager
  sequences/
    ChaseSequence
    FlightSequence
    StuntSequence
  vehicles/
    kitt/
    airwolf/
    ateam_van/
    stunt_vehicle/
    ghostbusters_vehicle/

Die endgültige Engine- und Rendering-Entscheidung bleibt offen. Architekturkonzepte sind daher engine-neutral zu halten.

### Datengetriebene Profile
Jedes Fahrzeugprofil beschreibt mindestens:
- Fahrzeug-ID und Asset-Referenzen.
- Animationszustände und Übergänge.
- Beschleunigung, Bremsverhalten und Handling-Abstraktion.
- Kamera- und Audio-Profil.
- Partikel-/Lichteffekte.
- Spezialfähigkeiten und deren Freischaltbedingungen.
- Kollisions-/Schadensreaktionen.
- Interaktions- und Story-Hooks.

### Timeline-Events
Cinematics werden über eine Timeline aus klaren Events aufgebaut, z. B.:
- set_camera
- play_animation
- play_audio
- start_dialogue
- enable_player_control
- disable_player_control
- spawn_effect
- trigger_choice
- set_story_flag
- transition_scene

Die Timeline darf keine versteckten Änderungen an zentralen Storyvariablen ausführen. Story-Flags und Konsequenzen müssen explizit dokumentiert und testbar sein.

## 11. Vertical Slice — empfohlener Pilot

**KITT-Verfolgungssequenz** als erster Fahrzeug-Prototyp:
1. KITT steht und Scanner läuft.
2. Michael steigt ein; kurze inszenierte Cockpit-/Außenperspektive.
3. Steuerung wird an den Spieler übergeben.
4. Eine überschaubare Verfolgungsstrecke mit mindestens drei unterschiedlichen Hindernissen.
5. Eine echte Routenentscheidung.
6. Turbo Boost als interaktiver Höhepunkt.
7. Eine filmische Auflösung mit sichtbarer Konsequenz.
8. Übergang zurück in eine Point-and-Click-Szene.

Abnahmekriterien:
- Das Zielverhältnis von ungefähr 50/50 Inszenierung und Interaktion ist in der Sequenz spürbar.
- Steuerung und Kameraschnitt sind verständlich.
- Die Sequenz ist mit Keyboard und Gamepad testbar, sofern beide Eingabearten im Prototyp unterstützt werden.
- Spielerfehler führen zu nachvollziehbaren Konsequenzen.
- Skip-Funktion für Cinematics.
- Story-Flags und Szenenübergänge sind reproduzierbar testbar.
- Performance und Assetbedarf sind dokumentiert.

## 12. Offene Punkte

- Vollständigen Fahrzeug-Roster mit vorhandenen Master-Sheets abgleichen.
- Exakte Episodenposition und Storyfunktion der ersten KITT-Verfolgung festlegen.
- Festlegen, welche Fahrzeugsequenzen vollständig 2D, pseudo-3D oder mit separaten Perspektiv-Sprites umgesetzt werden.
- Eingabe-/Steuerungsmodell im Vertical Slice testen.
- Engine erst nach technischem Prototypvergleich festlegen.

## 13. Claude-Arbeitsauftrag

Vor Implementierung:
1. Bestehende Fahrzeug-Assets, Master-Sheets, Storydokumente und technische Architektur inventarisieren.
2. Den vollständigen Fahrzeug-Roster aus dem Repository übernehmen; keine Fahrzeuge erfinden.
3. Diese Spezifikation und den bestehenden Pixel-Art-Animationsstandard lesen.
4. Einen engine-neutralen technischen Umsetzungsvorschlag und eine kleine KITT-Vertical-Slice-Aufgabenliste erstellen.
5. Keine finalen Assets oder Storyereignisse ohne Freigabe erzeugen.
6. Keine bestehende Architektur ersetzen, bevor der Ist-Zustand dokumentiert wurde.

Claude soll zunächst Architektur, Timeline-Prototyp und Steuerungsversuch vorbereiten. Die finalen Fahrzeuganimationen werden separat produziert und nach visueller QA integriert.

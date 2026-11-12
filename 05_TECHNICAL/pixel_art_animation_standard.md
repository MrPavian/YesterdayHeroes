# Pixel-Art- und Animationsstandard
## YESTERDAY HEROES — verbindliche Produktionsspezifikation

**Status:** Accepted — verbindlich ab 2026-11-12  
**Entscheidung:** Pixel-Art, acht Bewegungsrichtungen (8-way)  
**Geltungsbereich:** Spielfiguren, NPCs, Kreaturen, interaktive Charaktere und deren Animationen  
**Leitprinzip:** Ein gemeinsamer technischer Standard, individuelle Figurenidentität.

Dieses Dokument ist die maßgebliche Quelle für Charakter-Sprites und Animationen. Abweichungen benötigen eine ausdrückliche Designentscheidung. Es ersetzt keine Charakter-Master-Sheets: Diese bleiben Referenz für Aussehen, Kleidung, Proportionen und Farbpalette.

---

## 1. Visuelle Zielrichtung

- Hochwertige, handgepixelte 2D-Pixel-Art mit klaren Silhouetten und ausdrucksstarken Posen.
- Anmutung klassischer 1990er-Adventure-Spiele, aber keine Kopie konkreter Grafiken, Sprites, Hintergründe oder UI-Elemente bestehender Spiele.
- Figuren müssen auch bei kleiner Darstellung sofort unterscheidbar sein.
- Lesbare Konturen, kontrollierte Farbpaletten, bewusste Licht- und Schattencluster; kein automatischer Pixelierungsfilter auf hochauflösenden Bildern.
- Animationen sollen Persönlichkeit vermitteln: Gang, Haltung, Timing und Gestik sind Teil des Charakterdesigns.
- Pixel-Art wird nativ erstellt oder sauber auf Pixelraster übertragen. Keine unscharfen Zwischenstufen.

## 2. Technische Basis und Koordinatensystem

### 2.1 Spielauflösung

**Arbeitsziel für den ersten Prototyp:** virtuelle Auflösung 640 × 360 Pixel (16:9). Die Darstellung wird ganzzahlig hochskaliert. Die endgültige interne Auflösung wird im Vertical Slice anhand von Lesbarkeit, UI und Szenenkomposition bestätigt.

- Pixel-Art-Texturen werden ohne Glättung dargestellt (Nearest-Neighbor / `magFilter = NearestFilter`, `minFilter = NearestFilter`).
- Kamera, Sprite-Positionen und Bewegungsanimationen werden auf das virtuelle Pixelraster abgestimmt.
- Keine fractional scaling- oder Subpixel-Positionierung im finalen Pixel-Art-Renderpfad.
- Falls Three.js eingesetzt wird: Pixel-artgerechte Orthografie/2D-Ebene, kontrollierte Kamera und ein Renderpfad ohne Texturfilterung. Engine- und Renderdetails werden im technischen Prototyp verifiziert.

### 2.2 Sprite-Grundmaße

Die folgenden Werte sind Produktionsrichtwerte und bilden einen gemeinsamen Rasterstandard, keine Zwangsjacke für jede Figur:

| Typ | Richtmaß pro Frame | Verwendung |
|---|---:|---|
| Durchschnittlicher Mensch | 48 × 64 px | Standard-Charakter |
| Kleine/sitzende Figur | 40 × 48 px | kompakte Figuren, ALF nach Layouttest |
| Große/breite Figur | 64 × 80 px | sehr große oder breite Silhouetten |
| Sehr kleine Figur/Kreatur | 32 × 40 px | nur nach Lesbarkeitstest |
| Fahrzeuge | eigenes Raster | separate Vehicle-Sprites/Animationen |

- Jede Animation einer Figur verwendet grundsätzlich dieselbe Frame-Canvas-Größe.
- Die Figur darf innerhalb der Canvas variieren, aber Fußpunkt und Pivot müssen stabil bleiben.
- Größere Figuren dürfen größere Canvas-Maße nutzen; sie müssen im Spiel über eine definierte Welt-/Darstellungsgröße vergleichbar bleiben.
- Transparenter Hintergrund (RGBA). Keine Schatten, Beschriftungen oder Referenzansichten in Produktions-Spritesheets.

### 2.3 Anker und Ausrichtung

- Standard-Pivot ist die Mitte zwischen den Füßen auf der Bodenlinie.
- Der Boden-/Fußanker liegt pro Frame an derselben logischen Position.
- Kopf, Hände und Körper dürfen sich bewegen; die Figur darf beim Gehen nicht ungewollt hoch- und herwandern.
- Kollision und Interaktionspunkt werden unabhängig vom sichtbaren Sprite definiert.
- Jede Figur erhält eine dokumentierte `foot_anchor`, `pivot`, `collision_box` und `interaction_origin`.

## 3. Verbindliche 8-Wege-Richtungen

Richtungen werden aus Sicht der Spielfigur benannt und im Uhrzeigersinn geführt:

| Code | Richtung | Bedeutung |
|---|---|---|
| S | Süden | nach unten / zum Betrachter |
| SW | Südwest | schräg links unten |
| W | Westen | links |
| NW | Nordwest | schräg links oben |
| N | Norden | nach oben / vom Betrachter weg |
| NE | Nordost | schräg rechts oben |
| E | Osten | rechts |
| SE | Südost | schräg rechts unten |

**Wichtig:** Die Codes sind unabhängig von Bildschirmkoordinaten und Kamera-Implementierung. Die Zuordnung wird zentral im Code dokumentiert und nicht pro Figur neu interpretiert.

- Alle spielbaren Figuren benötigen perspektivisch acht Richtungen für Bewegung und Idle.
- Für NPCs kann die Produktion zunächst auf tatsächlich benötigte Richtungen begrenzt werden; die Datenstruktur bleibt 8-way-kompatibel.
- Diagonalbewegung wird im Spiel normalisiert, damit sie nicht schneller ist als horizontale/vertikale Bewegung.
- Diagonale Ansichten müssen anatomisch und perspektivisch plausibel sein. Keine bloße Rotation des Seiten-Sprites.
- Spiegeln einer Richtung ist nur zulässig, wenn Kleidung, Haare, Ausrüstung, Narben, Waffenhaltung und andere asymmetrische Merkmale dadurch nicht verfälscht werden. Standard ist eine eigens gezeichnete Richtung.

## 4. Animationsbibliothek

Die Framezahlen sind Startvorgaben. Jede Animation darf weniger oder mehr Frames erhalten, wenn Timing und Lesbarkeit es verlangen. Entscheidend ist eine saubere Loop- und Zustandsdefinition.

| Animation | Richtwert | Loop | Zweck |
|---|---:|---|---|
| `idle` | 4–6 | ja | Atmen, minimale Gewichtsverlagerung |
| `walk` | 6–8 | ja | normale Fortbewegung |
| `run` | 6–8 | ja | schnelles Laufen |
| `turn` | 2–4 | nein | Richtungswechsel, falls sichtbar nötig |
| `start` | 2–3 | nein | Anlaufen, optional |
| `stop` | 2–3 | nein | Abbremsen, optional |
| `interact` | 4–6 | nein | Hebel, Türen, Objekte bedienen |
| `use_item` | 3–6 | nein | Gegenstand einsetzen |
| `talk` | 3–5 | ja/kurz | Sprechgestik; Mundbewegung nur, wenn Stil es trägt |
| `gesture` | 3–6 | nein | zeigen, winken, erklären |
| `look` | 2–4 | nein | umsehen / nach oben oder unten schauen |
| `crouch` | 3–4 | ja/Übergang | ducken und geduckte Haltung |
| `sit` | 3–4 | ja/Übergang | hinsetzen, sitzen, aufstehen als getrennte Zustände |
| `jump` | 5–8 | nein | Absprung, Luftphase, Landung |
| `climb` | 6–8 | ja | Leiter/Klettern, sofern Gameplay benötigt |
| `combat` | 6–10 | nein | charakterabhängige Aktion |
| `hit` | 3–5 | nein | Trefferreaktion |
| `fall` | 4–6 | nein | Sturz |
| `victory` | 4–8 | nein/ja | Erfolg / Jubel |
| `special` | variabel | variabel | individuelle Signaturanimation |

Nicht jede Figur braucht jede Animation. Keine Animation wird nur erstellt, um eine Checkliste zu füllen. Die Story- und Gameplay-Aufgabe der Figur bestimmt den tatsächlichen Bedarf.

### 4.1 Richtungsumfang je Animation

**Pflicht für spielbare Figuren:**
- `idle`: 8 Richtungen
- `walk`: 8 Richtungen
- `run`: 8 Richtungen, sofern Rennen spielmechanisch vorkommt

**Nach Gameplay-Bedarf:**
- Interaktion, Gegenstandsnutzung, Talk/Gesture, Crouch, Sit, Jump, Climb und Combat erhalten die Richtungen, aus denen sie im Spiel tatsächlich gezeigt werden.
- Bei stationären Aktionen kann die Figur zur Interaktionsquelle oder Kamera ausgerichtet werden. Die Richtung darf nicht zufällig wechseln.
- Eine Animation mit nur einer Richtung muss explizit als richtungsunabhängig oder als feste Facing-Richtung gekennzeichnet sein.

## 5. Timing und Bewegungsgefühl

- Walk-Zyklus als Startwert: 8–12 Frames pro Sekunde.
- Run-Zyklus als Startwert: 10–14 Frames pro Sekunde.
- Idle: 3–6 Frames pro Sekunde oder bewusstes Halten einzelner Frames.
- Aktionen erhalten individuelle Dauer und dürfen nicht pauschal mit Walk-FPS abgespielt werden.
- Timing wird pro Animation in Millisekunden oder FPS festgelegt; keine fest verdrahtete globale Geschwindigkeit.
- Animationen müssen in Bewegung und bei Einzelbildprüfung lesbar sein.
- Kontakt-, Druck- und Gewichtsmomente (Fußauftritt, Landung, Treffer) benötigen klare Keyframes.
- Loops müssen ohne sichtbaren Sprung schließen. Frame 0 und letzter Frame dürfen keine ungewollte Positions- oder Haltungsdiskontinuität erzeugen.

## 6. Charakterdesign und Konsistenz

Jede Figur erhält vor der Animation:
1. freigegebenes Master-Sheet als Designreferenz,
2. Palette mit benannten Farbrollen,
3. Größen- und Proportionsangabe,
4. 8-Wege-Richtungsreferenz,
5. Pose Sheet mit charakteristischen Schlüsselposen,
6. dokumentierte asymmetrische Merkmale und Ausrüstung.

Die Animation darf das freigegebene Charakterdesign nicht neu interpretieren. Haare, Bart, Kleidung, Schmuck, Werkzeuge und charakteristische Silhouette bleiben konsistent. Änderungen am Design werden zuerst im Master-Sheet nachgezogen.

**IP-/Rechtehinweis:** Die bekannten Serienfiguren und ihre konkreten visuellen Designs können geschützt sein. Keine fremden Sprites, Screenshots, Sprite-Rips, Logos oder kopierten Spielgrafiken als Produktionsmaterial verwenden. Die Rechtefrage ist vor einer kommerziellen Veröffentlichung gesondert zu klären.

## 7. Dateiformat und Namenskonvention

### 7.1 Quelldateien und Exporte

- Master-Datei bevorzugt als editierbare Pixel-Art-Quelldatei (z. B. Aseprite-kompatibel) plus PNG-Export.
- PNG mit Transparenz, sRGB, ohne verlustbehaftete Kompression.
- Ein Spritesheet enthält nur eine Figur, eine Animation und eine Richtung.
- Keine gemischten Richtungen oder Animationen in einem Sheet, sofern ein Tool-Exportformat dies nicht ausdrücklich als technisch erzeugtes Atlasformat benötigt.
- Quelldateien bleiben erhalten; PNG ist der Laufzeit-Export.
- Atlas-Packaging erfolgt automatisiert aus den Einzel-Sheets, niemals als einzige Quelle.

### 7.2 Dateipfade

```text
assets/
  characters/
    <character_id>/
      reference/
        master_sheet.png
        pose_sheet.png
        palette.png
      source/
        <character_id>.aseprite
      spritesheets/
        idle/
          <character_id>_idle_S.png
          <character_id>_idle_SW.png
          ...
        walk/
          <character_id>_walk_S.png
          ...
        run/
          <character_id>_run_S.png
          ...
      config/
        <character_id>.json
```

Fahrzeuge erhalten einen eigenen Bereich unter `assets/vehicles/<vehicle_id>/`. Hintergrundgrafiken, UI und Effekte werden nicht im Charakterordner abgelegt.

### 7.3 Sprite-Sheet-Konvention

- Frames liegen in einer Zeile, in zeitlicher Reihenfolge von links nach rechts.
- Alle Frames einer Animation/Richtung haben identische Canvas-Maße.
- Keine Abstände, Rahmen, Nummern, Beschriftungen oder Hintergrundfarbe im Sheet.
- Transparenz bleibt erhalten.
- Frame-Reihenfolge ist verbindlich: links nach rechts, Index beginnend bei 0.
- Ein Export darf keine automatisch getrimmten Frames mit wechselnden Canvas-Größen enthalten.

Beispiel: `ba_baracus_walk_SW.png`

## 8. Animationskonfiguration

Jede Figur erhält eine maschinenlesbare Konfiguration. Beispielstruktur (Werte sind illustrativ und werden pro Figur geprüft):

```json
{
  "characterId": "ba_baracus",
  "displayName": "B.A. Baracus",
  "frameSize": { "width": 48, "height": 64 },
  "footAnchor": { "x": 24, "y": 61 },
  "pivot": { "x": 24, "y": 61 },
  "collisionBox": { "width": 26, "height": 14, "offsetX": 11, "offsetY": 48 },
  "directions": ["S", "SW", "W", "NW", "N", "NE", "E", "SE"],
  "animations": {
    "idle": {
      "S": { "file": "../spritesheets/idle/ba_baracus_idle_S.png", "frames": 4, "fps": 4, "loop": true }
    },
    "walk": {
      "S": { "file": "../spritesheets/walk/ba_baracus_walk_S.png", "frames": 8, "fps": 10, "loop": true }
    }
  }
}
```

Implementierungshinweise:
- Fehlende Animation/Richtung muss explizit behandelt werden (Fallback auf definierte Facing-Richtung oder gesperrte Aktion), nicht durch stilles Laden einer falschen Datei.
- Pfade sind relativ zur Konfigurationsdatei oder werden durch ein zentrales Asset-Manifest aufgelöst.
- Config enthält keine engine-spezifischen Laufzeitobjekte.
- Ein Validator prüft Dateiexistenz, Frameanzahl, Bildabmessungen, Transparenz und Richtungsabdeckung.

## 9. Produktionspipeline — verbindlicher Ablauf

### Phase A: Design-Freigabe
1. Charakter-Roster-Eintrag prüfen und stabile `character_id` festlegen.
2. Master-Sheet auf Vollständigkeit und Designkonsistenz prüfen.
3. Farbpalette, Proportionen, Kleidung, Ausrüstung und Silhouette freigeben.
4. 8-Wege-Ansichten und Pose Sheet erstellen.
5. Offene Designfragen klären, bevor Animationsframes produziert werden.

**Gate A:** Kein Animationsauftrag ohne freigegebene Designreferenz und Richtungsansicht.

### Phase B: Animationsplanung
1. Gameplay-Rolle und tatsächlich benötigte Animationen festlegen.
2. Pro Animation benötigte Richtungen bestimmen.
3. Key Poses und Bewegungsablauf als Thumbnail/Storyboard skizzieren.
4. Framezahl, Timing, Loop-Punkte und Anker definieren.
5. Ausnahmen (z. B. asymmetrische Ausrüstung, besondere Körperform) dokumentieren.

**Gate B:** Animationsliste und Key Poses sind abgenommen.

### Phase C: Pilotproduktion
1. Zuerst eine Richtung in niedriger Framezahl produzieren.
2. Silhouette, Fußanker, Timing und Lesbarkeit testen.
3. Danach die restlichen sieben Richtungen ergänzen.
4. Erst nach Freigabe die übrigen Animationen produzieren.
5. Exportieren und Konfiguration erstellen.

**Gate C:** Walk- und Idle-Pilot in allen acht Richtungen funktionieren im Spiel.

### Phase D: Technische Integration
1. PNG-Sheets und Config in den Asset-Loader importieren.
2. Sprite-Animation mit korrekter Frame-Reihenfolge und Timing abspielen.
3. 8-way-Facing aus Bewegungsvektor bestimmen.
4. Diagonalgeschwindigkeit normalisieren.
5. Fußanker, Sortierung/Tiefenwirkung und Collision Box prüfen.
6. Übergänge zwischen Idle, Walk, Run und Interaktion testen.
7. Skalierung, Kamera und Pixel-Snap auf Zielauflösung kontrollieren.

**Gate D:** Die Figur bewegt sich in einer Testszene ohne Flimmern, Größen-/Positionssprünge oder falsche Richtungszuordnung.

### Phase E: Qualitätssicherung
- Alle acht Richtungen einzeln prüfen.
- Animation bei 1×-Pixelgröße und finaler Spielskalierung prüfen.
- Loop-Anfang/-Ende auf Sprung prüfen.
- Fußkontakt und Bodenausrichtung kontrollieren.
- Silhouette und charakteristische Merkmale prüfen.
- Keine Pixel-Halos, halbtransparenten Ränder oder versehentlichen Hintergrundpixel.
- Alle Dateinamen, Configs und Pfade validieren.
- Gameplay-Test mit tatsächlicher Laufgeschwindigkeit und Interaktionspunkten durchführen.

**Gate E:** Erst nach bestandenem QA wird das Asset als `approved` markiert und im Asset-Manifest registriert.

## 10. Pilot: B.A. Baracus

B.A. Baracus ist die erste Pilotfigur, weil sein Master-Sheet als verbindliche Layoutreferenz dient.

**Pilotumfang:**
1. Master-Sheet prüfen und als Designquelle einfrieren.
2. Pose Sheet und acht Richtungsansichten ergänzen.
3. `idle` und `walk` mit zunächst einer Richtung erstellen.
4. Key Poses, Fußanker und Loop freigeben.
5. `idle` und `walk` in acht Richtungen vervollständigen.
6. `run` und `interact` als nächste Animationen ergänzen.
7. Testszene mit 8-way-Steuerung, Pixel-Snap und Debug-Anzeige bauen.
8. Pipeline dokumentieren und erst danach auf weitere Figuren übertragen.

**Nicht Teil des ersten Piloten:** sämtliche Spezialaktionen, Kampfanimationen und vollständige Animation aller 25 Figuren.

## 11. Produktionspriorisierung und Skalierung

- Zuerst ein vollständiger, technisch integrierter Pilot statt viele unfertige Figuren.
- Danach Figuren nach Episoden- und Prototypbedarf priorisieren.
- Gemeinsam nutzbare Animationen dürfen als Bewegungsreferenz dienen, aber nicht blind auf andere Körperformen kopiert werden.
- Wiederverwendung ist nur zulässig, wenn Silhouette, Timing, Ausrüstung und Charakterwirkung stimmen.
- NPCs erhalten nur den im Spiel benötigten Animationsumfang.
- Fahrzeuge, Kreaturen und Spezialformen erhalten eigene Standards, die auf demselben Asset- und QA-Prinzip aufbauen.

## 12. Abnahmekriterien für jedes Charakterpaket

Ein Charakterpaket gilt erst als fertig, wenn:
- Master-Sheet und Palette freigegeben sind.
- Richtungsreferenzen und Pose Sheet vorliegen.
- Benötigte Animationen und Richtungen vollständig sind.
- PNG-Exports und Quelldateien versioniert sind.
- JSON-Konfiguration vollständig und valide ist.
- Asset-Manifest aktualisiert ist.
- Integrationstest und visuelle QA bestanden sind.
- Keine Platzhalter- oder fehlenden Frames im freigegebenen Umfang verbleiben.

---

## 13. Verbindliche Kurzfassung für Claude

Bei jeder Charaktergrafik und Animation:
1. Pixel-Art, keine geglätteten oder automatisch pixelisierten Bilder.
2. Acht Richtungen: S, SW, W, NW, N, NE, E, SE.
3. Einheitliche Frame-Canvas je Figur; Fußanker und Pivot stabil.
4. Eine Animation und eine Richtung pro Spritesheet; Frames links nach rechts.
5. Transparente PNG-Exports plus editierbare Quelldatei und JSON-Config.
6. Master-Sheet ist Designquelle; Animationen dürfen das Design nicht verändern.
7. Erst Designfreigabe, dann Key Poses, Pilotrichtung, acht Richtungen, Integration, QA.
8. Keine erfundenen oder stillschweigend ersetzten Richtungen/Frames.
9. Vor Implementierung Engine-/Renderpfad in einem Vertical Slice testen.
10. Bei Konflikten gilt dieses Dokument für Animationen; MASTER_CONTEXT und freigegebene Charakterprofile gelten für Story und Charakterkanon.


## 1.1 Verbindliche Präzisierung: realistischer Adventure-Pixel-Art-Look

**Neue visuelle Leitentscheidung (2026-11-12):** Die bisherigen B.A.-Animationsvorlagen sind stilistisch nicht freigegeben. Sie wirken zu gestaucht, zu comichaft und entfernen sich zu weit vom Master-Sheet. Diese Vorlagen dürfen nicht als Produktionsbasis oder als Maßstab für weitere Figuren verwendet werden.

Ziel ist eine **realistische, handgepixelte Adventure-Grafik der klassischen 1990er-Jahre**, orientiert am visuellen Anspruch klassischer LucasArts-Adventures wie *Indiana Jones and the Fate of Atlantis* — ausdrücklich keine Übernahme konkreter Sprites, Figurenzeichnungen oder Hintergründe.

Verbindliche Merkmale:
- Anatomisch glaubwürdige menschliche Proportionen statt Chibi-, Super-Deformed- oder Cartoon-Körper.
- Keine übergroßen Köpfe, verkürzten Beine, aufgeblasenen Hände oder vereinfachten Comic-Silhouetten.
- Körpervolumen, Muskelgruppen, Kleidung und Falten werden durch gezielte Pixelcluster und abgestufte Schattierung modelliert.
- Gesichter bleiben charakteristisch und ausdrucksstark, aber nicht karikaturhaft.
- Konturen dürfen nicht pauschal als dicke schwarze Außenlinie ausgeführt werden.
- Licht, Schatten, Material und Perspektive müssen eine glaubwürdige räumliche Form erzeugen.
- Pixelkanten bleiben bewusst gesetzt; keine Weichzeichner, Anti-Aliasing-Halos oder automatischen Pixelierungsfilter.
- Detailgrad und Pixelmaßstab müssen zur Spielauflösung passen. Nicht künstlich grob pixeln, nur damit die Pixel stärker auffallen.

**Wichtig:** „Realistisch“ bedeutet hier glaubwürdige Proportionen, Volumen und Darstellung innerhalb einer handgepixelten Adventure-Ästhetik — keine fotorealistische Grafik und keine 3D-Render-Optik.

## 6.1 B.A. Baracus — verbindliche Proportionssperre

Das vom Projektinitiator gelieferte B.A.-Master-Sheet ist die maßgebliche Referenz. Die bisherigen generierten Animationsvorlagen sind wegen gestauchter, comichafter Proportionen verworfen.

Bei jeder neuen B.A.-Pose müssen erhalten bleiben:
- breite, massive Schulterpartie und kräftiger Brustkorb;
- muskulöse, voluminöse Oberarme und Unterarme;
- kräftiger, erwachsener Rumpf mit plausibler Taille;
- lange, kräftige Beine im Verhältnis zum Oberkörper;
- charakteristischer Kopf, Mohawk, Bart und Gesicht;
- Jeansweste, rotes Shirt, goldene Ketten, Armbänder, olivgrüne Cargo-Hose und schwere Stiefel;
- die erwachsene, gewichtige Körperwirkung des Master-Sheets.

Keine pauschale Verkleinerung des Oberkörpers, keine Verkürzung der Beine und keine Vergrößerung des Kopfes. Die Figur muss in allen acht Richtungen dieselbe anatomische Identität behalten.

Die Frame-Canvas wird **nicht vorab auf 48×64 oder 64×80 festgeschrieben**. Zuerst wird die Figur aus dem Master-Sheet in einer passenden Pixelgröße und mit realistischen Proportionen als Pose-/Scale-Referenz aufgebaut. Danach werden Canvas, Fußanker und Laufzeitgröße anhand eines In-Game-Vergleichs festgelegt.

## 10.1 Korrektur des B.A.-Piloten

Vor jeder weiteren Animationsproduktion:
1. Die bisherigen gestauchten/comichaften B.A.-Vorlagen als **verworfen / nicht produktionsfähig** markieren.
2. Das Original-Master-Sheet unverändert als Referenz verwenden.
3. Eine maßstäbliche Front-, Rücken- und Profil-Analyse erstellen; Körperhöhe, Kopfgröße, Schulterbreite, Rumpf- und Beinlänge dokumentieren.
4. Eine neue realistische Pixel-Art-Pose-Referenz erstellen, die den Proportionen des Master-Sheets folgt.
5. Erst nach visueller Freigabe eine einzelne Idle-Pose und einen Walk-Keyframe in einer Richtung erstellen.
6. Darstellung bei 1× und in der vorgesehenen Spielskalierung prüfen.
7. Erst danach weitere Frames und die übrigen sieben Richtungen produzieren.

**Abnahmekriterium:** Bei direktem Vergleich muss die animierte Figur eindeutig wie dieselbe Person aus dem Master-Sheet wirken. Bei Abweichungen in Statur, Kopf-/Körperverhältnis oder Kleidung ist das Asset abzulehnen — auch wenn die Animation technisch korrekt läuft.

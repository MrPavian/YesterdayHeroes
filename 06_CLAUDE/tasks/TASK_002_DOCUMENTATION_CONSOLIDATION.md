# TASK 002 — Dokumentations-Konsolidierung und Projekt-Governance

## Rolle
Du arbeitest als Documentation Lead und Technical Project Architect für YESTERDAY HEROES.

## Pflichtlektüre
Lies zuerst:
- `MASTER_CONTEXT.md`
- `README.md`
- sämtliche Markdown-Dateien unter `01_STORY` bis `07_ROADMAP`
- `assets/README.md` und `assets/ASSET_MANIFEST.md`, falls vorhanden

Nutze außerdem den Auditbericht aus TASK 001, den der Projektinitiator bereitgestellt hat. Die Punkte aus diesem Bericht sind Prüfhypothesen und müssen am aktuellen Repository-Zustand verifiziert werden.

## Ziel
Die Dokumentation soll widerspruchsfrei, navigierbar und als verlässliche Arbeitsgrundlage für Claude Code nutzbar sein. Diese Aufgabe ist ausschließlich Dokumentations- und Strukturarbeit. Keine Programmierung und keine neuen Story-Festlegungen.

## Verbindliche Einschränkungen
- Keine endgültigen Entscheidungen zur Weltregel, Zeitreise-Mechanik, Historie, Episodenreihenfolge, Charakterwechsel, Grafikstil, Plattform oder Engine treffen.
- Keine Figuren, Episoden, Rätsel oder historischen Ereignisse eigenmächtig als Kanon festlegen.
- Keine vorhandenen Dokumente oder Assets löschen.
- Keine Inhalte stillschweigend verkürzen. Bei Konflikten inhaltliche Abweichung dokumentieren und konservativ lösen.
- Prüfe zuerst den aktuellen Branch und Arbeitsbaum; keine fremden Änderungen überschreiben.
- Verwende kleine, nachvollziehbare Änderungen.

## Arbeitsaufträge

### 1. Zentrale Claude-Code-Einstiegsdatei
Erstelle eine root-level `CLAUDE.md`, die:
- auf `MASTER_CONTEXT.md` als verbindliche Projektquelle verweist;
- Claude anweist, vor jeder Aufgabe relevante Dokumente und vorhandenen Code zu lesen;
- die Priorität von Entscheidungen definiert;
- verbietet, offene kreative Entscheidungen eigenmächtig zu finalisieren;
- die bestehenden Coding- und Abschlussregeln referenziert, statt sie vollständig zu duplizieren.

Vermeide konkurrierende Regelwerke. `MASTER_CONTEXT.md` bleibt die zentrale Projektkontextquelle; `CLAUDE.md` ist der kurze Einstiegspunkt für Claude Code.

### 2. Widersprüche und Status bereinigen
Prüfe und korrigiere mindestens:
- Asset-Erfassung: Unterscheide zwischen „Grafiken recherchiert/gefunden“, „Assetpaket lokal vorbereitet“, „Binärdateien tatsächlich im GitHub-Repository committed“ und „Assets technisch integriert“. Nichts als committed ausgeben, solange die PNG-Dateien nicht physisch im Repo liegen.
- CHANGELOG: Ergänze nur tatsächlich erfolgte Dokumentationsänderungen.
- Roadmap und progress.md: Status muss exakt übereinstimmen.
- Zeitraum: Vereinheitliche die Formulierung. Bis zur Entscheidung soll 1993 als geplanter Startpunkt und der weitere Zeitraum als offen gekennzeichnet bleiben.
- Episodenreihenfolge: Der Opener führt aktuell zu Michael Knight. Weise dies als derzeitigen Entwurf aus, nicht als unumkehrbare Festlegung der gesamten Reihenfolge.
- Five Pillars / Episoden: Klar kennzeichnen, dass eine Zuordnung erst entwickelt werden muss.
- Inventar und Fairness: Gegenstände dürfen nicht so abgelegt oder verbraucht werden, dass ein später zwingend benötigtes Rätsel unlösbar wird. Markiere eine konkrete Inventarregel als noch offene Designentscheidung.
- Indizes: READMEs müssen den tatsächlichen Dateibestand abbilden und „geplant“ nur für wirklich noch fehlende Dokumente verwenden.
- Abschlussberichte: Ein einheitliches Format in Claude-Aufträgen verwenden.

### 3. Vertical Slice konsolidieren
In `MASTER_CONTEXT.md`, `05_TECHNICAL/engine.md` und `05_TECHNICAL/architecture.md` gibt es unterschiedliche Listen für den Prototyp.

Entwickle eine konsistente, engine-neutrale Mindestdefinition als Vorschlag und verwende sie überall einheitlich. Der Vorschlag soll mindestens diese Fähigkeiten berücksichtigen:
- ein Raum mit Hintergrund;
- eine spielbare Figur oder ein klar getesteter Bewegungs-/Navigationsansatz;
- Hotspots mit Untersuchen-Feedback;
- Gegenstand aufnehmen und im Inventar darstellen;
- Gegenstand untersuchen und mindestens eine Kombination testen;
- Dialog mit auswählbaren Antworten;
- ein kleines lösbares Rätsel;
- Wechsel in eine zweite Szene;
- Zustand speichern und wieder laden.

Kennzeichne diese Liste als empfohlenen Vertical-Slice-Umfang, der noch vom Projektinitiator freigegeben werden muss. Unterscheide klar zwischen Vertical Slice und kleinem Engine-Vergleichstest.

### 4. Einheitliche Regeln und Dokumentationsstruktur
- Reduziere doppelte Claude-Regeltexte auf klare Quellenverweise.
- Einheitliche Abschlussbericht-Struktur: Zusammenfassung, geänderte Dateien, Entscheidungen/Annahmen, Tests/Ergebnisse, Einschränkungen/offene Punkte, nächster Schritt.
- Aktualisiere die README-Dateien in `04_GAME_DESIGN` und `05_TECHNICAL`.
- Ergänze bei Bedarf ein `DECISIONS.md` im Repository-Stamm als Entscheidungslog mit Spalten: ID, Thema, Status (open/proposed/accepted/rejected), Entscheidung, Begründung, Datum. Übernimm keine offenen Vorschläge als akzeptierte Entscheidungen.
- Ergänze ein kurzes Register offener Fragen, falls dies nicht bereits übersichtlich besteht.

### 5. Asset-Verfügbarkeit transparent dokumentieren
- Prüfe, welche Assets tatsächlich im GitHub-Repository vorhanden sind.
- Falls nur Manifest/README vorhanden sind, Status auf „Dokumentation vorhanden, Binärimport ausstehend“ setzen.
- Keine Dateien simulieren oder leere Platzhalter unter Bilddateinamen anlegen.
- Halte fest, dass Sammel-Sheets Referenzmaterial sind und nicht automatisch produktive Sprites.
- Verweise auf fehlende Einzelgrafiken für Ghostbusters, Colt Seavers, Hintergründe, Donald/Elon, UI und Gegenstände als offene Asset-Aufgaben.

### 6. Datenschutz und Rechte
- Dokumentiere als Empfehlung, das Repository bis zur Rechteklärung auf privat zu stellen.
- Ändere die Repository-Sichtbarkeit nicht selbst.
- Ergänze eine offene Rechte-Checkliste für Figuren, Marken, Fahrzeuge, Logos, Musik, Fonts und Bildmaterial.
- Unterscheide zwischen internem Konzept-/Fan-Prototyp und möglicher öffentlicher/kommerzieller Veröffentlichung.

## Akzeptanzkriterien
- [ ] Root-level `CLAUDE.md` vorhanden und kurz, eindeutig, ohne Regelduplikate.
- [ ] Widersprüche aus TASK 001 geprüft und bereinigt oder begründet als offen markiert.
- [ ] Status von Assets präzise und wahrheitsgemäß.
- [ ] Vertical-Slice-Definition an allen Stellen identisch.
- [ ] README-Indizes stimmen mit tatsächlichen Dateien überein.
- [ ] Einheitliche Abschlussbericht-Regel vorhanden.
- [ ] Entscheidungslog und offener Fragenkatalog vorhanden oder vorhandene Äquivalente aktualisiert.
- [ ] Roadmap, progress.md und CHANGELOG stimmen überein.
- [ ] Keine Story-, Engine-, Plattform- oder Sichtbarkeitsentscheidung eigenmächtig getroffen.
- [ ] Dokumente gegengelesen; Links und relative Pfade geprüft.

## Abschlussbericht
Berichte in dieser Reihenfolge:
1. Zusammenfassung
2. Geänderte und neu angelegte Dateien
3. Auditpunkte: behoben / offen / nicht zutreffend
4. Entscheidungen, die weiterhin den Projektinitiator benötigen
5. Validierung (Links, Pfade, Konsistenz)
6. Bekannte Einschränkungen
7. Nächster empfohlener Auftrag

## Arbeitsmodus
Arbeite direkt im Repository-Branch, den der Projektinitiator für diese Aufgabe vorgibt. Falls kein Branch vorgegeben ist, arbeite in einem neuen Branch `docs/task-002-consolidation` und erstelle einen Pull Request statt direkt in `main` zu schreiben.

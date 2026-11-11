# MASTER CONTEXT — YESTERDAY HEROES

> Diese Datei ist die zentrale, verbindliche Kontextquelle für alle Claude-Aufträge. Bei Widersprüchen gilt folgende Priorität: ausdrückliche aktuelle Entscheidung des Projektinitiators > freigegebene Story-/Design-Dokumente > Roadmap > ältere Entwürfe und Gesprächsnotizen.

## 1. Projektidentität

**Titel:** YESTERDAY HEROES  
**Untertitel / Arbeitstitel:** The Last Great Timeline  
**Genre:** Episodisches Point-and-Click-Adventure  
**Referenzgefühl:** Monkey Island, Day of the Tentacle und Indiana Jones and the Fate of Atlantis. Diese Werke sind Stilreferenzen, keine Vorlagen zum Kopieren von Texten, Grafiken, Rätseln oder konkreten Assets.

## 2. Kernprämisse

Die Handlung spielt hauptsächlich in den 1990er-Jahren; 1993 ist das derzeit bevorzugte Startjahr.

Donald J. und Elon M. kommen aus der Gegenwart 2026. Sie reisen mit einer von Elon entwickelten Zeitmaschine in die Vergangenheit. Ihr Ziel ist, entscheidende historische und technologische Entwicklungen zu manipulieren, um eine alternative Zukunft zu schaffen, in der sie die Welt beherrschen.

Donald ist der macht- und anerkennungsbesessene Selbstdarsteller. Elon ist der technokratische Kontrollfanatiker. Beide benötigen einander, streiten aber ständig und planen insgeheim, den jeweils anderen nach dem gemeinsamen Erfolg auszuschalten.

Die Bösewichte dürfen satirisch, grotesk, größenwahnsinnig und böse-komisch sein. Sie sind fiktive, überzeichnete Spielfiguren, inspiriert von öffentlichen Figuren. Keine erfundenen Behauptungen über reale Personen als Tatsachen darstellen.

## 3. Heldenensemble

Verbindlich vorgesehen sind:
- Michael Knight / KITT
- Das A-Team: Hannibal, B.A., Face, Murdock
- Airwolf: Stringfellow Hawke und Dominic Santini
- ALF
- Colt Seavers
- Ghostbusters: Peter Venkman, Ray Stantz, Egon Spengler, Winston Zeddemore
- MacGyver

Cameos sind möglich. Die genannten Figuren sollen nicht bloß dekorativ auftreten: Ihre jeweiligen Fähigkeiten, Macken und Beziehungen müssen für Handlung, Rätsel oder Humor genutzt werden.

## 4. Dramaturgie und Spielstruktur

Das Spiel verbindet Episoden-Adventure und Hybridstruktur:
- Zu Beginn erhalten einzelne Helden eigene Episoden und abgeschlossene Abenteuer.
- Hinweise, Gegenstände, Ereignisse und Entscheidungen verbinden die Episoden zunehmend.
- Später treffen Figuren und Teams aufeinander; der Spieler wechselt in passenden Abschnitten zwischen Helden.
- Im Finale kommt das gesamte Ensemble zusammen. Die Menschheit steht vor einer scheinbar ausweglosen Bedrohung. Nur das Zusammenspiel aller Fähigkeiten kann Donald und Elon aufhalten.

Der Opener zeigt Donald und Elon in einer geheimen Forschungsbasis im Jahr 2026. Elon präsentiert Donald die Zeitmaschine. Die beiden streiten bereits über Macht, Anerkennung, Technik und ihre künftige Rollenverteilung. Ein kurzer Blick auf Elons geheime Zusatzagenda und Donalds eigene Verratsabsichten kann foreshadowed werden. Danach folgt der Sprung ins Jahr 1993 und der Einstieg in die erste Heldenepisode.

## 5. Rätseldesign

Verbindliche Prinzipien:
1. Knifflige, faire Rätsel mit nachvollziehbarer Logik.
2. Absurde Gegenstandskombinationen sind ausdrücklich erwünscht, müssen im Rückblick aber plausibel oder zumindest komisch nachvollziehbar sein.
3. Rätsel bauen auf den spezifischen Fähigkeiten der Figuren auf.
4. Jede Episode braucht markante Rätselketten und mindestens einen erinnerungswürdigen Höhepunkt.
5. Dialoge, Beobachtungen und Informationen sind gleichwertige Rätselwerkzeuge.
6. Episodenübergreifende Gegenstände und Hinweise können im späteren Spiel wieder relevant werden.
7. Keine unlösbaren Sackgassen und keine Lösungen, die ausschließlich auf willkürlichem Pixel-Hunting beruhen.
8. Der Spieler soll Hinweise erhalten können, ohne dass Rätsel automatisch gelöst werden.
9. Beispiel: Das A-Team wird in einer Lagerhalle eingeschlossen und baut aus einem alten Traktor, Schrott und gefundenen Bauteilen ein improvisiertes gepanzertes Fluchtfahrzeug. Der Spieler muss die Konstruktion selbst durch Erkundung und Kombinationsrätsel ermöglichen.

## 6. Tonalität

- Sarkastisch, pointiert und mit warmherziger Nostalgie.
- Slapstick als Würze, nicht als Dauerzustand.
- Figuren bleiben in ihrer eigenen Logik glaubwürdig.
- Der Humor entsteht aus Charakterkontrasten, Dialogen und Situationen.
- Spannung, echte Gefahr und emotionale Momente müssen neben der Komik bestehen können.

## 7. Technische Leitplanken

Die technische Basis ist noch nicht endgültig entschieden. Three.js ist vom Projektinitiator vorgeschlagen; Phaser ist als Alternative für ein 2D-zentriertes Adventure zu prüfen.

Vor einer Engine-Festlegung:
- einen klar begrenzten Prototyp planen;
- Interaktion, Hotspots, Szenenwechsel, Inventar, Dialoge und Animationen testen;
- Entwicklungsaufwand und Wartbarkeit vergleichen;
- eine begründete Empfehlung dokumentieren.

TypeScript und Vite sind bevorzugte Kandidaten, aber die finale Stack-Entscheidung ist erst nach Prüfung des vorhandenen Repository-Zustands und Prototyping verbindlich.

Keine unnötigen Frameworks einführen. Architektur modular und datengetrieben halten. Story-/Rätseldaten möglichst von Engine-Code trennen.

## 8. Claude-Arbeitsregeln

- Vor jeder Aufgabe zuerst diese Datei und die konkret referenzierten Projektdokumente lesen.
- Bestehende Dateien und Architektur untersuchen, bevor Änderungen vorgeschlagen werden.
- Niemals bestehende Funktionen oder Assets ohne Auftrag löschen oder ersetzen.
- Keine großen, monolithischen Dateien erzeugen.
- Aufgaben in kleine, überprüfbare Schritte teilen.
- Nach jeder Aufgabe Tests/Lint/Build ausführen, soweit vorhanden, und Ergebnisse offen dokumentieren.
- Keine nicht getesteten Funktionen als fertig bezeichnen.
- Bei unklaren Anforderungen: sinnvolle Annahmen explizit dokumentieren und reversible Lösung wählen; keine zentralen Storyentscheidungen eigenmächtig festschreiben.
- Änderungen, offene Punkte und nächste Schritte in der Projektdokumentation aktualisieren.
- Keine realen Markenlogos, Serienlogos oder kopierten Originalassets in neu erstellten Assets verwenden, solange keine entsprechenden Nutzungsrechte vorliegen.
- Keine fremden geschützten Spielgrafiken, Musik, Dialoge oder Rätsellösungen kopieren.

## 9. Status

Das Repository startet als Dokumentations- und Konzeptbasis. Story, Episoden, Rätsel und technische Architektur befinden sich in der Vorproduktion. Noch nicht als endgültig festgeschrieben gelten insbesondere:
- der vollständige Masterplan und die fünf historischen Eingriffe;
- die endgültige Episodenanzahl und Reihenfolge;
- die genaue Mechanik der Zeitmaschine;
- der finale Plot-Twist;
- Grafikstil, Engine und Zielauflösung.

## 10. Arbeitsgrundsatz

YESTERDAY HEROES soll ein echtes, in sich schlüssiges Adventure werden – nicht nur eine Aneinanderreihung nostalgischer Cameos. Story, Rätsel, Charaktere und Technik werden gemeinsam und iterativ entwickelt.

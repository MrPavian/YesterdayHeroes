# Inventory System — Design Draft

## Anforderungen
- Gegenstände aufnehmen, ablegen und untersuchen.
- Inventarinhalt visuell und textlich darstellen.
- Gegenstände mit Hotspots und anderen Gegenständen kombinieren.
- Charakter- bzw. Episodenzustände berücksichtigen.
- Episodenübergreifende Gegenstände und deren Herkunft nachvollziehbar halten.
- Unzulässige Kombinationen erhalten charaktervolle, humorvolle Rückmeldungen.

## Datenmodell — konzeptionell
Jeder Gegenstand benötigt eine stabile ID, Anzeigename, Beschreibung, Icon/Asset-Referenz, Besitzer bzw. Verfügbarkeit, Zustand und Kombinationsregeln.

## Offen
- Inventarlimit oder unbegrenztes Inventar.
- Gemeinsames Team-Inventar oder getrennte Charakterinventare.
- Umgang mit verbrauchten und veränderten Gegenständen.

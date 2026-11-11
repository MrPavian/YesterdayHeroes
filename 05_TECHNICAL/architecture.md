# Technical Architecture — Proposal

## Leitprinzipien
- Modularer, wartbarer Code.
- Trennung von Engine, UI, Spieldaten und Storycontent.
- Datengetriebene Episoden und Rätsel.
- Stabile IDs für Szenen, Gegenstände, Figuren, Dialoge und Storyflags.
- Keine monolithische Game-Datei.
- Speichern/Laden mit Versionsschema für Spielstände.

## Vorgeschlagene Module
- GameState / SaveSystem
- SceneManager
- InteractionSystem / HotspotManager
- CharacterController
- InventorySystem
- PuzzleState / FlagSystem
- DialogueSystem
- AudioManager
- EpisodeManager
- UI Layer

## Vertical Slice
Ein Raum mit:
- einem spielbaren Helden;
- begehbarer Figur oder klarer Klickbewegung;
- drei bis fünf Hotspots;
- mindestens zwei aufnehmbaren Gegenständen;
- einer Gegenstandskombination;
- einem Dialog mit Auswahlmöglichkeiten;
- einem lösbaren Rätsel;
- funktionierendem Speichern und Laden.

Erst nach erfolgreichem Prototyp und dokumentiertem Vergleich wird die Engine festgelegt.

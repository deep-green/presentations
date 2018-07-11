class: center, middle

# Google Actions

---

## Inhaltsverzeichnis

1. Technologie
2. Motivation
3. How to
4. Probleme
5. Live Demo

---

## Technologie: Google Assistant

- Endgerät über Spracheingabe steuern
- Release: 18. Mai 2016

__Plattformen__
- Android, Google Home, Wear OS, Android TV, Google Pixelbook, Smart Speakers, Headphones, Smart Displays, Google Allo, iOS

__Sprachen__
- Englisch, Indisch (Hindi), Idonesisch, Französisch, Deutsch, Italienisch, Japanisch, Koreanisch, Portugiesisch, Spansich

__SDK Release: April 2017__
- eigene Hardware bauen
- Rapsberry Pi
- Audi, Volvo
- Smart Home: Kühlschrank, Waschmaschine, Ofen

---

## Google Actions

- eigene Google Assistant Apps  erstellen

__Release__
- Dez 2016: Google Home
- Mar 2017: Tools für Spiele
- Mai 2017: Android & iOS
- 2018: API Version 2

---

## Motivation

__Steuern über Spracheingabe__
- Gemütlichkeit
- Entwicklung in die Zukunft

__Interesse__
- Spracheingabe
- Neue Technologie

__Einfachheit__
- Assistenten erstellen ohne Programmierkenntnisse
- Einmal einstellen -> mit allen Google Geräten kompatibel

---

## How to

__Google Actions erstellen__
- Dialogflow
- Template
- Google Actions SDK

---
class: center, middle

<img src="images/dialogflowui.png" width="79%" />

---

## Google Actions SDK

__Informationen__
- Google Actions funktionieren über Google Account

__Projekt erstellen__
- gactions CLI herunterladen
- Projekt initiieren
- erstellt: action.json, package.json

__Actions updaten__
- lokale Dateien hochladen
- gactions update --action_package PACKAGE_NAME --project PROJECT_NAME

---

## Probleme

__Technologie ist neu__
- unausgereift
- wenig Support, solutions
- lange Arbeit den Fehler zu finden
- stetige Änderungen
- Inkonsistente / falsche docs

__Beispiele__
- Solution für meine Lösung: September 2017
- V2 API Beta startete Ende 2017 (danach)

---

## Probleme

__Gescheiterte Anläufe__
- Dialogflow über Firebase: kein Zugriff auf externe Systeme
- Dialogflow über bespoken.io: "Dialogflow V2 is not supported"
- Template: Keine Möglichkeit zu programmieren
- Google Action SDK über bespoken.io: "UnparseableJsonResponse"

---
class: center, middle

## Live Demo
## Zum späteren Zeitpunkt
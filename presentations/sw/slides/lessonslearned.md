class: center, middle
# Lessons Learned

---

class: center, middle
# Allgemeines

---

## Theoretisches Wissen
### Allgemeines

Welche theoretischen Kenntnisse hast du im Laufe des Projektes allgemein gewonnen?

<br />

- Schachregeln
- Schachnotationen
- ELO-Zahl als Bewertungswerkzeug

---

## Technisches Wissen
### Allgemeines

Welche technischen Kenntnisse hast du im Laufe des Projektes allgemein gewonnen?

<br />

- socket.io

---

## Probleme
### Allgemeines

Welche allgemeinen Probleme gab es während des Projekts (Teamarbeit, Projektleitung, etc.)?

<br />

- Andere darauf hinzuweisen besser zu kommunizieren, wenn die Kommunikation mir nicht gefällt
- Ressourcen besser einteilen
- Teile des Projekts priorisieren
- Teile des Projekts als erstes zu realisieren, weil andere darauf aufbauen
- Andere Teilnehmer früher mitteilen, wenn Probleme vorliegen
- Das Teambuilding benötigt Zeit -> die geringe gemeinsame Arbeitsdauer (1 Semester, Treffen in Abständen mehrerer Tage) reicht dafür kaum aus
- Umstrukturierungen erschweren das Verfolgen des Projektziels -> "aus dem Tritt geraten"

---

class: center, middle
# Frontend
## Desktop, Alexa, Google Actions & Web

---

## Theoretisches Wissen
### Frontend

Welche theoretischen Kenntnisse hast du im Frontend gewonnen?

<br />

- JSON Objekte korrekt parsen
- FEN-Notation parsen und korrekt ausgeben
- Umgang und Programmierung von Alexa
- Umgang und Programmierung von Google Actions

---

## Technisches Wissen
### Frontend

Welche technischen Kenntnisse hast du im Frontend gewonnen?

<br />

- JavaScript
- JSON
- Unreal Engine Blueprint System
- Erstellen eines SSL Zertifikat
- Google Actions

---

## Probleme
### Frontend

Welche Probleme gab es während des Projekts bei dem Fronted?

<br />

- Bei der visuellen Ausgabe für eine FEN-Notation im Web auf korrekte Variabelnamen achten
- Teils schlechte Dokumentationen für das Arbeiten mit Blueprints
- Technologie zu neu (unausgereift, wenig Support / solutions, viel Aufwand den Fehler zu finden, stetige Änderungen, Inkonsistente / falsche docs)

---

class: center, middle
# Backend
## Logik & Datenbank

---

## Theoretisches Wissen
### Backend

Welche theoretischen Kenntnisse hast du im Backend gewonnen?

<br />

- Object-Document Mapping
- Dokumentenbasierte Datenbanken
- Vielgestaltigkeit der asynchronen Programmierung unter Node.js

---

## Technisches Wissen
### Backend

Welche technischen Kenntnisse hast du im Backend gewonnen?

<br />

- Javascript
- mongoose
- Promises, Callbacks für die asynchrone Programmierung unter Node.js / Javascript
- Integration von auf unterschiedlichen Programmiersprachen basierenden Modulen unter Node.js
- Jest Javascript Testing Framework für asynchrone Funktionen
- Anwendung von Travis CI

---

## Probleme
### Backend

Welche Probleme gab es während des Projekts bei dem Backend?

<br />

- der Workload war für die beteiligten Personen zu groß zur Umsetzung aller Anforderungen
- Komplexität von Travis CI im Zusammenspiel mit Node-Modulen, die in weitere Programmiersprachen entwickelt wurden -> kein TDD in gegebenem Zeitrahmen
- Komplexität von Travis CI im Zusammenspiel mit socket.io (Client/Server-Mock up) -> kein TDD in gegebenem Zeitrahmen
- Komplexität von Travis CI im Zusammenspiel mit Datenbankverbindungen (Client/Server-Mock up) -> kein TDD in gegebenem Zeitrahmen

---

class: center, middle
# CV/Bilderkennung

---

## Theoretisches Wissen
### CV/Bilderkennung

Welche theoretischen Kenntnisse hast du im Bereich CV gewonnen?

<br />

- Staunton-Figuren
- Lageerkennung (Rotationen, Translationen)
- Rotationsvektor
- Rodrigues-Formel
- Euler Winkel
- Matrizenoperationen

---

## Technisches Wissen
### CV/Bilderkennung

Welche technischen Kenntnisse hast du im Bereich CV gewonnen?

<br />

- Python (eigentliche Implementierung)
- C++ (Testprogramm zur Toolchain der Bildauswertung)
- Javascript (geringfügig wegen der Bildübergabe)
- Hintergründe Pose-Estimation und Template-Matching

---

## Probleme
### CV/Bilderkennung

Welche Probleme gab es während des Projekts bei der CV?

<br />

- teilweise verwirrende OpenCV-Dokumentation (insbesondere Flags)
- extreme Abhängigkeit von zeitaufwändigen Try+Error-Verfahren (Random-Fotos, Parametervielfalt)
- starke Verzögerungen wegen Hängenbleibens an Einzelproblemen, die für den Gesamtfortschritt unabdingbar zu lösen waren
- Einzelproblem: Verfeinerung der Rotationsmatrix, extremer Zeitverlust wegen Versuchs, die Kamera-Matrix anzupassen

---

## Probleme
### CV/Bilderkennung

<br /><br />

- Einzelproblem: Grenzfindung Schachbrett, wegen Suche nach Threshold-Parametern zur sicheren Musterbestimmung
- Einzelproblem: Figurenerkennung mit Template-Matching (für mich unlösbar, nicht nachvollziehbare Ergebnisse aus OpenCV)
- Workload wäre eigentlich zu bewältigen gewesen, Problem war Lösungsfindung zu Einzelfunktionen
- bis zuletzt ganze Funktion quasi nutzlos, obwohl Fortschritte gemacht wurden
- Template-Matching offenbar für die Aufgabenstellung ungeeignet, wegen Zeitmangel wurde keine andere Lösung mehr implementiert

---

class: center, middle
# Künstliche Intelligenz
## KI1 & KI2

---

## Theoretisches Wissen
### Künstliche Intelligenz

Welche theoretischen Kenntnisse hast du im Bereich KI gewonnen?

<br />

- MiniMax-Algorithmus
- Neuronale Netze
- Maschinelles lernen

---

## Technisches Wissen
### Künstliche Intelligenz

Welche technischen Kenntnisse hast du im Bereich KI gewonnen?

<br />

- Rust
- neon-bindings
- Python
- TensorFlow

---

## Probleme
### Künstliche Intelligenz

Welche Probleme gab es während des Projekts bei der KI?

<br />

- Schlecht dokumentierte Rust-Module
- Schlechte neon-bindings Dokumentation
- Gegen Ende des Spiels zu defensive Taktik von KI2
- Wenig fortgeschrittene Intelligenz von KI1
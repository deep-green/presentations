# Software-Projekt - Lessons Learned

## Allgemeines

### Mitwirkende

Name              | Zuständig für                      | Mitgeholfen an                           |
-----------------:|------------------------------------|:-----------------------------------------|
Alexander Scharow | Google Voice, Datenbank, Use Cases | Backend-Logik                            |
Patrick Reinke    | KI                                 | Zuggenerator, Backend, Server-Verwaltung |
Marti Stuwe       | KI                                 | KI Testclient, Zuggenerator              |
Phillip Penner    | KI                                 | KIvsKI                                   |
Luis Deutsch      | KI                                 | SocketIO, KIvsKI                         |
Tobias Koppmann   | Backend, Datenbank                 | Integration Client-Kommunikation         |
Hendrik Schröder  | Zuschauermodus Web				         | Weboberfläche Zuschauermodus             |
Nicola Kühnert    | Desktop Frontend, Unreal Engine    | -                                        |
Julien Garb       | Alexa                              | Alexa                                    |
Torsten Niemeier  | CV/Bilderkennung                   | nirgendwo                                |
_Yourname_        | _place_                            | _holder_                                 |

### Theoretisches Wissen
Welche theoretischen Kenntnisse hast du im Laufe des Projektes allgemein gewonnen?

```
- Schachregeln
- Schachnotationen
- ELO-Zahl als Bewertungswerkzeug
```

### Technisches Wissen
Welche technischen Kenntnisse hast du im Laufe des Projektes allgemein gewonnen?

```
- socket.io
- google Actions
```

### Probleme
Welche allgemeinen Probleme gab es während des Projekts (Teamarbeit, Projektleitung, etc.)?

```
- Andere darauf hinzuweisen besser zu kommunizieren, wenn die Kommunikation mir nicht gefällt
- Ressourcen besser einteilen
- Teile des Projekts priorisieren
- Teile des Projekts als erstes zu realisieren, weil andere darauf aufbauen
- Andere Teilnehmer früher mitteilen, wenn Probleme vorliegen
- Das Teambuilding benötigt Zeit -> die geringe gemeinsame Arbeitsdauer (1 Semester, Treffen in Abständen mehrerer Tage) reicht dafür kaum aus
- Umstrukturierungen erschweren das Verfolgen des Projektziels -> "aus dem Tritt geraten"

```

## Frontend (Unreal, Alexa, Google Actions & Web)

### Theoretisches Wissen
Welche theoretischen Kenntnisse hast du durch die Wahl des Themas gewonnen?

```
- JSON Objekte korrekt parsen
- FEN-Notation parsen und korrekt ausgeben
- Umgang und Programmierung von Alexa
- Umgang und Programmierung von Google Actions
```

### Technisches Wissen
Welche technischen Kenntnisse hast du durch die Wahl des Themas gewonnen?

```
- JavaScript
- JSON
- Unreal Engine Blueprint System
- Erstellen eines SSL Zertifikat
```

### Probleme
Welche Probleme gab es während des Projekts bei dem oben angegebenen Thema?

```
- Bei der visuellen Ausgabe für eine FEN-Notation im Web auf korrekte Variabelnamen achten
- Teils schlechte Dokumentationen für das Arbeiten mit Blueprints
```

## Backend (Logik & Datenbank)

### Theoretisches Wissen
Welche theoretischen Kenntnisse hast du im Laufe des Projektes gewonnen?

```
- Object-Document Mapping
- Dokumentenbasierte Datenbanken
- Vielgestaltigkeit der asynchronen Programmierung unter Node.js
```

### Technisches Wissen
Welche technischen Kenntnisse hast du im Laufe des Projektes gewonnen?

```
- Javascript
- mongoose
- Promises, Callbacks für die asynchrone Programmierung unter Node.js / Javascript
- Integration von auf unterschiedlichen Programmiersprachen basierenden Modulen unter Node.js
- Jest Javascript Testing Framework für asynchrone Funktionen
- Anwendung von Travis CI
```

### Probleme
Welche Probleme gab es während des Projekts bei dem oben angegebenen Thema?

```
- der Workload war für die beteiligten Personen zu groß zur Umsetzung aller Anforderungen
- Komplexität von Travis CI im Zusammenspiel mit Node-Modulen, die in weitere Programmiersprachen entwickelt wurden -> kein TDD in gegebenem Zeitrahmen
- Komplexität von Travis CI im Zusammenspiel mit socket.io (Client/Server-Mock up) -> kein TDD in gegebenem Zeitrahmen
- Komplexität von Travis CI im Zusammenspiel mit Datenbankverbindungen (Client/Server-Mock up) -> kein TDD in gegebenem Zeitrahmen
```

## Künstliche Intelligenz (KI1 & KI2)

### Theoretisches Wissen
Welche theoretischen Kenntnisse hast du im Laufe des Projektes gewonnen?

```
- MiniMax-Algorithmus
- Neuronale Netze
- Maschinelles lernen
```

### Technisches Wissen
Welche technischen Kenntnisse hast du im Laufe des Projektes gewonnen?

```
- Rust
- neon-bindings
- Python
- TensorFlow
```

### Probleme
Welche Probleme gab es während des Projekts bei dem oben angegebenen Thema?

```
- Schlecht dokumentierte Rust-Module
- Schlechte neon-bindings Dokumentation
```

## CV/Bilderkennung

### Theoretisches Wissen
Welche theoretischen Kenntnisse hast du im Laufe des Projektes gewonnen?

```
- FEN-Notation
- Staunton-Figuren
- Lageerkennung (Rotationen, Translationen)
- Rotationsvektor
- Rodrigues-Formel
- Euler Winkel
- Matrizenoperationen
```

### Technisches Wissen
Welche technischen Kenntnisse hast du im Laufe des Projektes gewonnen?

```
- Python (eigentliche Implementierung)
- C++ (Testprogramm zur Toolchain der Bildauswertung)
- Javascript (geringfügig wegen der Bildübergabe)
- Hintergründe Pose-Estimation und Template-Matching
```

### Probleme
Welche Probleme gab es während des Projekts bei dem oben angegebenen Thema?

```
- teilweise verwirrende OpenCV-Dokumentation (insbesondere Flags)
- extreme Abhängigkeit von zeitaufwändigen Try+Error-Verfahren (Random-Fotos, Parametervielfalt)
- starke Verzögerungen wegen Hängenbleibens an Einzelproblemen, die für den Gesamtfortschritt unabdingbar zu lösen waren
- Einzelproblem: Verfeinerung der Rotationsmatrix, extremer Zeitverlust wegen Versuchs, die Kamera-Matrix anzupassen
- Einzelproblem: Grenzfindung Schachbrett, wegen Suche nach Threshold-Parametern zur sicheren Musterbestimmung 
- Einzelproblem: Figurenerkennung mit Template-Matching (für mich unlösbar, nicht nachvollziehbare Ergebnisse aus OpenCV) 
- Workload wäre eigentlich zu bewältigen gewesen, Problem war Lösungsfindung zu Einzelfunktionen
- bis zuletzt ganze Funktion quasi nutzlos, obwohl Fortschritte gemacht wurden
- Template-Matching offenbar für die Aufgabenstellung ungeeignet, wegen Zeitmangel wurde keine andere Lösung mehr implementiert
```


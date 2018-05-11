name: templating
background-image: url(./img/game-of-chess.png)
class: center
count: false
---
class: center, middle
count: false
background-image: url(./img/game-of-chess.png)

# Schachsoftware
### Überblick - Standards - Möglichkeiten

---
template: templating
count: false

# Agenda

.left[
1. Einführung

2. Historie

3. Aufbau

4. Standards

5. Möglichkeiten in Deep Green
]
---
template: templating

# Einführung

.left[
- in fast allen Kulturen bekannt

- besitzt große Bedeutung

- sehr beliebtes Feld der Informatik

- vorhandene Standards

- sehr viele vorhandene Produkte
]

---
template: templating

# Historie

.left[
- Schachprogramme gibt es, seit es Rechenmaschinen gibt

- __Schachcomputer__
    - Torres' Turmendspielautomat (Leonardo Torres Quervedo, 1914)

    - ab 1950er zahllose Entwicklungen

    - Schachcomputer Belle (Ken Thompson, 1979)

- __Schachsoftware/-algorithmen__
    - Programm für Zuse Z1 (Konrad Zuse)
    
    - Alan Turing (Papiermaschine)

    - Teil der Spieltheorie (John von Neumann)

]

---
template: templating

# Aufbau

.left[
- unterteilt in Engine und Frontend

- __Frontend__
    -  muss Protokolle unterstützen

- __Engine__
    - Zuggenerator
        
    - Bewertungsfunktion

    - Bibliotheken und Datenbanken

    - Schachdatenbank (gespielte Partien)
]

---
template: templating

# Engine Architektur

.center[![Engine Architektur](./img/engine_architecture.jpg)]

---
template: templating

# Standards

.left[
- Protokolle
    - Chess Engine Communication Protocol (CECP)

    - Universal Chess Interface (UCI)

    - Beide Spezifikationen offen, werden von vielen Engines und GUIs unterstützt

- FEN - Forsyth-Edwards Notation
    - Eine Notation, die die gesamte Situation eines Bretts darstellen kann
    - erweiterte Varianten X-FEN und Shredder-FEN

- Elo Zahlen
    - Rating System
 
    - erfunden von Physiker und Statistiker Arpad Elo

    - Standard-System im Weltschachverband FIDE
]

---
template: templating

# Möglichkeiten

.left[

]


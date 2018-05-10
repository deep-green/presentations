# Die Schachsoftwar Deep Green

## Notizen zur Präsentation

## Einführung

- Schach ist eines der wenigen (bzw. einzige?) Spiel, dass im Großteil der Kulturen bekannt ist (westlich, Vorderasien -> Abwandlungen in Asien)

- Es besitzt eine große kulturelle und wissenschaftliche Bedeutung (Sport, Psychologie, Mathematik, Informatik)

- Wir haben uns ein in der Informatik sehr beliebtes Feld ausgesucht (unbeabsichtigt?)

- Resultat -> Es gibt sehr viele Standards für Schachsoftware

- Daraus ergeben sich Möglichkeiten für vermarktbare Produkte (besonders Frontend)

## 1. Kurze Historie der Schachsoftware

- Schachsoftware, bzw. Computerschach gibt es schon seit es Rechenmaschinen gibt

- 2 Entwicklungen eng verzahnt

### Schachcomputer

- Torres' Turmendspielautomat (1914)
- dann ab 1950er wieder Hochphase durch elektronische Rechner

### Schachsoftware

- bekannte Größen, die sich mit Schachcomputern bzw. -software befasst haben:
    * Konrad Zuse (lernte extra Schach)
    * Alan Turing (Papiermaschine)
    * John von Neumann (Teil der Spieltheorie)
    * Ken Thompson (erfand Schachcomputer "Belle")

- nahm interessante Auswüchse an (Cray X-MP [50 Mio\$] vs Belle[50k\$])

## 2. Klassischer Aufbau von Schachsoftware

- unterteilt in Engine und Frontend

- Frontend ist soweit einfach,
    -  muss Protokolle unterstützen

- Engine
    - Zuggenerator
        - interne Darstellung des Spielbretts
        - Erzeugung aller möglichen Züge anhand einer Situation
        - dabei auch Rochaden und En-Passant-Schläge 
    - Bewertungsfunktion (Bei uns KI)
        - bewertet die möglichen Züge
        - Mattstellungen oder heuristisch
    - Bibliotheken und Datenbanken
        - Eröffnungsbibliothek
        - Endspieldatenbank
    - Schachdatenbank (gespielte Partien)

## 3. Standards

- Protokolle
    * Chess Engine Communication Protocol (CECP)
    * Universal Chess Interface (UCI)
    * Beide Spezifikationen offen, werden von vielen Engines und GUIs unterstützt

- Elo Zahlen
    * Rating System, dass von dem Physike rund Statistiker Arpad Elo erfunden wurde
    * Standard-System im Weltschachverband FIDE
    * Beschreibt die Wahrscheinlichkeit eines Sieges anhand des aktuellen Punktestands
    * Punktegewinn anhand derr Wahrscheinlichkeit höher oder niedriger

## 4. Für das Projekt interessante Möglichkeiten der Umsetzung

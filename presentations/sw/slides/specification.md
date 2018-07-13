class: center, middle

# Software-Projekt

---

## Inhaltsverzeichnis

1. Softwarearchitekturdiagramm
2. Use-Cases
3. Protokoll
4. Frontend
5. Alexa
6. Google Actions
7. Backend
8. CV/Bilderkennung
9. Datenbank
10. Künstliche Intelligenz
11. Live Demo
12. Lessons Learned

---

class: center, middle
# Softwarearchitekturdiagramm

---

## Softwarearchitekturdiagramm

<img src="images/sw-dia.png" width="95%" />

---

class: center, middle
# Use-Cases

---

## Use-Cases
### Hauptmenü

<img src="images/usecase-hauptmenu.png" width="80%" />

---

## Use-Cases
### Im Spiel

<img src="images/usecase-ingame.png" width="75%" />

---

## Use-Cases
### Im Spiel mit Sprachsteuerung

<img src="images/usecase-ingame-voice.png" width="75%" />

---

class: center, middle
# Protokoll

---

## Protokoll
### Backend &#8667; Client &emsp; 1/4

#### Definition für reason

| Wert        | Bedeutung                              |
|:------------|:---------------------------------------|
|"won"        | Spiel wurde vom Empfänger gewonnen     |
|"lost"       | Spiel wurde vom Empfänger verloren     |
|"draw"       | Spiel endet unentschieden              |
|"con_lost"   | Verbindungsabbruch zum anderen Spieler |
|"player_end" | Verbindungsabbruch zum anderen Spieler |

#### invitation &emsp; _Zum Einladen eines gegnerischen Spielers_

```json
{
  "FEN": "rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1",
  "ID_enemy": "maxmustermann"
}
```

---

## Protokoll
### Backend &#8667; Client &emsp; 2/4

#### reject &emsp; _Zum Ablehnen eines Zuges oder eines Bildes_

```json
{
}
```

#### receive &emsp; _Zum Teilen und/oder Bestätigen eines Zuges und eines Bildes (color: false = white, true = black)_

```json
{
  "FEN": "rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1",
  "ID_game": 2,
  "color": false,
  "turns": [
    "e2e4",
    "c2c4"
  ]
}
```

---

## Protokoll
### Backend &#8667; Client &emsp; 3/4

#### end &emsp; _Zum Beenden eines Spiels; unabhängig vom Grund (Gewonnen, Verloren, Unentschieden oder Verbindungsabbruch)_

```json
{
  "reason": "connection lost",
  "ID_game": 2,
  "ID_player": "heinrichmustermann"
}
```

---

## Protokoll
### Backend &#8667; Client &emsp; 4/4

#### games &emsp; _Antwort auf 'getGames'; beinhaltet alle aktiven Spiele, die aktuelle FEN-Notation und die höchste ELO-Zahl der beiden Spieler_

```json
[
  {
    "ID_game": 1,
    "FEN": "rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1",
    "elo": 1267
  },
  {
    "ID_game": 2,
    "FEN": "rnbqkbnr/ppp1pppp/3p4/8/8/8/PPPPPPPP/RNBQKBNR b KQkq - 1 0",
    "elo": 1843
  }
]
```

---

## Protokoll
### Client &#8667; Backend &emsp; 1/6

#### makeMove &emsp; _Zum Tätigen eines Zuges_

```json
{
  "FEN": "rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1",
  "ID_game": 2,
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
```

#### rewind &emsp; _Zum Rückgängig machen eines Zuges; optional: Anzahl der Züge_

```json
{
  "ID_game": 2,
  "turnCount": 4,
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
```

---

## Protokoll
### Client &#8667; Backend &emsp; 2/6

#### accept &emsp; _Zum Annehmen eines Spiels_

```json
{
  "ID_game": 2,
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"  
}
```

#### reject &emsp; _Zum Ablehnen von Einladungen_

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
```

---

## Protokoll
### Client &#8667; Backend &emsp; 3/6

#### saveGame &emsp; _Zum Speichern von Spielen_

```json
{
  "ID_game": 2,
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"  
}
```

#### newGame &emsp; _Zum Starten eines neuen Spiels_

```json
{
  "ID_enemy": "maxmustermann",
  "color": false,
  "FEN": "rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
```

---

## Protokoll
### Client &#8667; Backend &emsp; 4/6

#### image &emsp; _Zum Hochladen einer Spielsituation per Bild_

```json
{
  "image": "data:image/jpeg;base64,/9j/4RiDRXhpZgAATU0AKgA...",
  "color": false,
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
```

#### saveTurn &emsp; _Zum Markieren eines Zuges_

```json
{
  "ID_game": 2,
  "turn": 4,
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"   
}
```

---

## Protokoll
### Client &#8667; Backend &emsp; 5/6

#### end &emsp; _Zum Beenden eines Spiels; unabhängig vom Grund (Gewonnen, Verloren, Unentschieden oder Verbindungsabbruch)_

```json
{
  "reason": "draw",
  "ID_game": 2,
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"  
}
```

#### getGames &emsp; _Fordert alle aktiven, betrachtbaren Spiele an_

```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
```

---

## Protokoll
### Client &#8667; Backend &emsp; 6/6

#### viewGame &emsp; _Abonniert das über ID_game vorgegebene Spiel_

```json
{
  "ID_game": 12,
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
}
```

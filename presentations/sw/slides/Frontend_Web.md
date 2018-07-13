class: center, middle
# Frontend
## Zuschausermodus Web

---

## Technologie
### Frontend - Zuschausermodus Web

__Programmiersprache(n):__
- JavaScript

__Bibliotheken:__
- socket.io

---

## Anforderungen Zuschauermodus
### Frontend - Zuschausermodus Web

- Spiel auswählen
- Automatische Aktualisierung des Zuges
- Historie des Spielverlaufs

---

## Anzeige der Figuren
### Frontend - Zuschausermodus Web

|weiß			|schwarz|
|--			|--|
|&#9817 Bauer		|&#9823 Bauer|
|&#9814 Turm		|&#9820 Turm|
|&#9816 Springer	|&#9822 Springer|
|&#9815 Läufer		|&#9821 Läufer|
|&#9813 Dame		|&#9819 Dame|
|&#9812 König		|&#9818 König|

---

## Darstellung
### Frontend - Zuschausermodus Web

- 8x8 Feld
- jedes Feld einzeln Ansprechbar
- FEN --> Positionierung

<img src="images/frontend/SchachbrettWEB.png" width="50%" />

---

## Code-Snippets
### Frontend - Zuschausermodus Web

```js
for (position = 0; position < fen.length; position++) {
            if (fen.charAt(position) == '/') {
                idZeile++;
                idSpalte = 0;
            }
            else if (fen.charAt(position) == 'p') {
                aktuell = '&#9823';
            }
            else if (fen.charAt(position) == 'r') {
                aktuell = '&#9820';
            }
            else if (fen.charAt(position) == 'n') {
                aktuell = '&#9822';
            }
            else if (fen.charAt(position) == 'b') {
                aktuell = '&#9821';
            }
            else if (fen.charAt(position) == 'q') {
                aktuell = '&#9819';
            }
            else if (fen.charAt(position) == 'k') {
                aktuell = '&#9818';
            }
           .
           .
```

---

## Code-Snippets
### Frontend - Zuschausermodus Web

```js
  if (idZeile == 1) {
           if (idSpalte == 1) {
               document.getElementById('c11').innerHTML = aktuell;
           }
           else if (idSpalte == 2) {
               document.getElementById('c12').innerHTML = aktuell;
           }
           else if (idSpalte == 3) {
               document.getElementById('c13').innerHTML = aktuell;
           }
           else if (idSpalte == 4) {
               document.getElementById('c14').innerHTML = aktuell;
           }
           else if (idSpalte == 5) {
               document.getElementById('c15').innerHTML = aktuell;
           }
           else if (idSpalte == 6) {
               document.getElementById('c16').innerHTML = aktuell;
           }
           .
           .
      }
}
```


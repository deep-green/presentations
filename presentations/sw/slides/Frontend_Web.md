class: center, middle
# Frontend - Zuschausermodus Web

### Technologien
- Webstorm
	- JavaScript
	- HTML
- SocketIO

---

# Anforderungen Zuschauermodus

- Spiel auswählen
- Automatische Aktualisierung des Zuges
- Historie des Spielverlaufs

---

# Anzeige der Figuren

weiß				schwarz
&#9817 Bauer		&#9823 Bauer
&#9814 Turm			&#9820 Turm
&#9816 Springer		&#9822 Springer
&#9815 Läufer		&#9821 Läufer
&#9813 Dame			&#9819 Dame
&#9812 König		&#9818 König

---

#Darstellung

- 8x8 Feld
- jedes Feld einzeln Ansprechbar
- FEN --> Positionierung

<img src="images/frontend/SchachbrettWEB.png" width="50%" />
---

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
           [...]
```
---
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
           else if (idSpalte == 7) {
                document.getElementById('c17').innerHTML = aktuell;
           }
           else if (idSpalte == 8) {
                document.getElementById('c18').innerHTML = aktuell;
           }
      }
            [...]
}
```


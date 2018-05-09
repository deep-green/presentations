class: center, middle
# MiniMax Algorithmus

---

# Was ist der Minimax-Algorithmus?

* Algorithmus zur Ermittlung der optimalen Spielstrategie
* Funktioniert nur bei endliche Zwei-Personen-Spiele mit perfekten Informationen
* Funktioniert bei Brettspielen wie z.B:
    * Schach
    * Go
    * Dame
    * Mühle
    * Vier gewinnt
    
---
    
# Wie funktioniert der Minimax-Algorithmus?
Theoretische Vorgehensweise des Algorithmus:
* Spielzüge in einem Suchbaum abbilden
* Jeden Spielzug bewerten 
    * Wenn Spieler A gewinnt mit __+1__ bewerten
    * Wenn Spieler B gewinnt mit __-1__ bewerten
    * Wenn es zu einem Unentschieden kommt mit __0__ bewerten
* Besten Spielzug mit Tiefensuche herausfinden
    * Bei einfachen Spielen bis zum Ende
    * Bei komplexeren Spielen bis zu einer vorgegebene Tiefe
    
---

# Beispiel
![Suchbaum](images/mm-suchbaum.png)    
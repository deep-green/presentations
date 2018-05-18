# Computer Vision - Maschinelles Sehen

## ... oder "Bildverstehen"


<p align="center">
  <img align="center" width="700" src="./images/bild1.jpg">
</p>


---

# Tasks

### - digitale Bilder 
 - erfassen
 - verarbeiten
 - analysieren
 - verstehen
### - Extrahieren
 - Daten
 - Informationen
 - Entscheidungen

---

## wissenschaftliche Disziplin:
Theorie hinter künstlichen Systemen, die Informationen aus Bilder extrahieren

## technologische Disziplin:
Theorien und Modelle -> Konstruktion maschinell sehender Systeme

## Werkzeuge:
- Mathematik (Geometrie, linearer Algebra, Statistik, Optimierung und Funktionalanalysis)

---

## Anwendungsgebiete:
- Industrie (Automatisierung, Qualitätskontrolle, Robotik)
- Verkehrstechnik (Radarfalle (Kennzeichen), autonomes Fahren)
- Sicherheitstechnik (Zutrittskontrolle, Erkennung von Gefahrensituationen)
- Social Media (anstössige Bilder)

### industrielle Umgebung vs. natürliche Umgebung

---

# akt. Forschungs- und Anwendungsprojekte 

## größtenteils: 
- Objekte erkennen, beschreiben, vermessen, klassifizieren

## kleiner Bereich:
- Bilder tatsächlich verstehen bzw. interpretieren

---

# Bildverarbeitung - Image-Processing
# Bilderkennung - Image-Analysis

<img align="center" width="600" height="410" src="./images/titelbild.jpg">

---

## Bildverarbeitung
- Verarbeitung von Signalen = Bildern
- meist zweidimensional
- Ergebnis entweder Bild
- oder Merkmale eines Bildes (Bilderkennung)

## Bilderkennung (image analysis)
- Teilgebiet der Bildverarbeitung
- Teilgebiet der Mustererkennung
- Versuch, Objekte zu segmentieren
- Segmente -> symbolische Beschreibung
- keine Suche nach Zusammenhängen

---

# unsere Aufgabenstellung

1. Spieler macht mit Kamera ein Bild seines Schachbretts
2. Spieler sendet das Bild per HTTP-POST
3. Per Bilderkennung wird die Spielsituation erkannt
4. Die erkannte Spielsituation wird als JSON oder ähnlich zurückgeschickt
5. Dem Spieler wird die erkannte Situation angezeigt
6. Der Spieler kann Korrekturen vornehmen

<p align="center">
  <img align="center" width="250" height="250" src="./images/schachnotation.png">
</p>


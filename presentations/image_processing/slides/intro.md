class: center, middle


# Maschinelles Sehen - Computer Vision

... oder Bildverstehen beschreibt im Allgemeinen die computergestützte Lösung von Aufgabenstellungen, die sich an den Fähigkeiten des menschlichen visuellen Systems orientieren. 
[Wikipedia]

## Anwendungsgebiete:
- Industrie (Automatisierung, Qualitätskontrolle, Robotik)
- Verkehrstechnik (Radarfalle (Kennzeichen), autonomes Fahren)
- Sicherheitstechnik (Zutrittskontrolle, Erkennung von Gefahrensituationen)

---

# Bildverarbeitung - Image-Processing
# Bilderkennung - Image-Analysis

<img align="center" width="600" height="410" src="./images/titelbild.jpg">

---

# Definitionen

## Bildverarbeitung
Unter Bildverarbeitung versteht man in der Informatik und der Elektrotechnik die Verarbeitung von Signalen, die Bilder repräsentieren, beispielsweise Fotografien oder Einzelbilder aus Videos. Das Ergebnis einer Bildverarbeitung kann wiederum ein Bild sein oder auch eine Menge von Merkmalen des Eingabebildes (siehe Bilderkennung). In den meisten Fällen werden Bilder als zweidimensionales Signal betrachtet, so dass übliche Methoden aus der Signalverarbeitung angewandt werden können.
[Wikipedia]

---

# Definitionen

## Bilderkennung
Bilderkennung (englisch image analysis) ist ein Teilgebiet der Mustererkennung und der Bildverarbeitung. In der Bilderkennung versucht man, Objekte in einem Bild zu segmentieren. Diesen wird eine symbolische Beschreibung zugewiesen, aber es wird nicht nach Zusammenhängen zwischen den Objekten gesucht, wie es in der Musteranalyse üblich ist. 
[Wikipedia]

---

# Aufgabenstellung

1. Spieler macht mit Kamera ein Bild seines Schachbretts
2. Spieler sendet das Bild per HTTP-POST
3. Per Bilderkennung wird die Spielsituation erkannt
4. Die erkannte Spielsituation wird als JSON oder ähnlich zurückgeschickt
5. Dem Spieler wird die erkannte Situation angezeigt
6. Der Spieler kann Korrekturen vornehmen

<p align="center">
  <img align="center" width="250" height="250" src="./images/schachnotation.png">
</p>


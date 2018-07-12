class: center, middle

# Tensorflow
<img src="images/tf.png" width="100%">

---

## Was ist TensorFlow?

- TensorFlow wurde von Google veröffentlicht
- Framework für Maschinelles Lernen
- Open-Source
- Tensorflow wird genutzt von Firmen wie :  SAP, Nvidia, AMD, intel, Twitter und Coca Cola
- TensorFlow nutzt dabei die Rechenleistung von CPU und GPU
- TensorFlow wird in Python benutzt
- TensorFlow ist in C++ geschrieben

---

## Wie funktioniert TensorFlow?

- Berechnungen werden über Datenflussgraphen ausgeführt
- In diesen Graphen representieren die Knoten mathematische Funktionen
- Die Kanten repräsentieren die Daten, welche für gewöhnlich multidimensionale Arrays sind oder Tensoren


---

## Wie verwende ich TensorFlow?

- Zuerst installieren: **pip3 install --upgrade tensorflow**
	- Für GPU Version: **pip3 install --upgrade tensorflow-gpu**
- Im Skript importieren: **import tensorflow as tf**
- Anschließend hat man Zugriff auf alle Operationen und Methoden von TensorFlow
- Beispiel:
<img src="images/bspskript.PNG" width="75%">

---

## Wie kann ich mir nun meinen Graphen angucken?

- Es ist möglich über die Kommandozeile eine Darstellung auf den localhost zu streamen
	- Beispiel:  **tensorboard --logdir="C:\Users\Luis Deutsch\Desktop\output" --host=127.0.0.1**

<img src="images/graphex.PNG" width="90%">
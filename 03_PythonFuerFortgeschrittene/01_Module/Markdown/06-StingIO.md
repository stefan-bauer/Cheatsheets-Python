# StringIO

Quelle: Datamics

Das StingIO Modul implementiert ein im Speicher hinterlegtes Objekt, das einer Datei ähnelt. Dieses Objekt kann dann als Input oder Output für die meisten Funktionen verwendet werden, die eine Datei erwarten würden.

Der beste Weg das zu erklären ist ein Beispiel:


```python
from io import StringIO
import io
```


```python
# Willkürlicher String
nachricht = "Das ist nur ein normaler String."
```


```python
# Wir können jetzt die StringIO Methode nutzen, um ein Dateien Objekt zu erstellen
f = io.StringIO(nachricht)
```

Jetzt haben wir ein Objekt f das wir wie eine Datei behandeln können. Zum Beispiel:


```python
f.read()
```




    'Das ist nur ein normaler String.'



Wir können auch hinein schreiben:


```python
f.write(" Zweite Zeile für unser dateiähnliches Objekt.")
```




    45




```python
# Den Cursor wie bei einer Datei an den Start setzen
f.seek(0)
```




    0




```python
# Auslesen
f.read()
```




    'Das ist nur ein normaler String.Zweite Zeile für unser dateiähnliches Objekt.'



Toll! Wir haben gesehen, wie wir StringIO nutzen können, um normale String in im Speicher hinterlege dateiähnliche Objekte umwandeln zu können. Diese Art der Verwendung hat verschiedene Anwendungsgebiete.

# Dateien

Quelle: Datamics

Python nutzt Datei Objekte, um mit externen Dateien auf Computern zu interagieren. Diese Datei Objekte können jegliche Art von Datei sein, die du auf deinem Computer hast: von Audio-, über Text- und E-Mail-Daten bis hin zu Excel Dokumenten usw. Dabei gilt es zu beachten, dass wahrscheinlich einige Libraries oder Module installiert werden müssen, um mit den verschiedenen Dateitypen zu interagieren. Diese sind simpel zu erhalten (wir werden den Download von Modulen später behandeln). 

## Hintergrund zu Dateien

Was Dateien auszeichnet ist, dass sie auch unabhängig von der Programmausführung bestehen können. Anders als es bspw. unsere Variablen im Code tun. Dateien werden deshalb als nicht flüchtig bzw. als persistent bezeichnet.

*Randnotiz: Das Wort "Datei" ist eine Schöpfung aus den beiden deutschen Wörtern "Daten" und "Kartei".*

Die Daten (also Nullen und Einsen), die in einer Datei gespeichert sind, erhalten im Endeffekt immer erst durch ein Programm oder das Betriebssystem eine Bedeutung. 

## Dateien in Python

Python bietet eine vorinstallierte *Öffnen* Funktion, die es uns erlaubt, mit grundlegenden Datei Typen zu arbeiten. Als erstes brauchen wir jedoch eine Datei. Wir werden iPython "Magie" nutzen, um eine Text Datei zu erstellen.

## iPython Datei Erstellung


```python
%%writefile test.txt
Hallo, das ist eine kurze Testdatei
```

    Writing test.txt


## Python öffnet eine Datei

Wir können eine Datei mit der open() Funktion öffnen. Die open Funktion hat Parameter als Input. Lasst uns anschauen, wie es funktioniert:


```python
# Die text.txt Datei öffnen, die wir gerade erstellt haben
my_file = open('test.txt')
```


```python
# Jetzt können wir den Inhalt der Datei lesen
my_file.read()
```




    'Hallo, das ist eine kurze Testdatei'




```python
# Was passiert aber, wenn wir erneut lesen wollen?
my_file.read()
```




    ''



Das passiert, weil man sich Python beim Lesen als Cursor vorstellen kann, der bis zum Ende der Datei geht. Dort bleibt er stehen und befindet sich dort nach dem ersten read Befehl. Es gibt also nichts mehr zu lesen. Wir können den Cursor folgendermaßen zurücksetzen:


```python
# Den Anfang der Datein (Index 0) suchen
my_file.seek(0)
```




    0




```python
my_file.read()
```




    'Hallo, das ist eine kurze Testdatei'



Um nicht immer wieder zum Anfang zu müssen können wir auch die `readlines` Funktion nutzen. Bei großen Dateien sollte man allerdings Vorsicht walten lassen, da alles im Speicher gehalten wird. Wie man mit großen Dateien umgehen kann schauen wir uns später im Kurs an.


```python
# readlines() gibt eine Liste aller Zeilen in der Datei zurück
my_file.readlines()
```




    []



## In eine Datei schreiben

Per Standard erlaubt uns die `open` Funktion nur, Dateien zu lesen. Wir müssen den Parameter 'w' übergeben, um Inhalte überschreiben zu können. Zum Beispiel:


```python
# Wir fügen einen zweiten Parameter 'w' hinzu, der für Schreiben (write) steht
my_file = open('test.txt','w')
```


```python
# In die Datei schreiben
my_file.write('Das ist eine neue Zeile')
```




    23




```python
# Die Datei lesen
my_file = open('test.txt', 'r')
my_file.read()
```




    'Das ist eine neue Zeile'



## Iterationen in einer Datei

Es folgte eine kurze Vorschau einer for Schleife, mit der wir Iterationen in einer Datei ausführen. Zunächst erstellen wir mit iPython eine neue Datei:


```python
%%writefile neu.txt
Erste Zeile
Zweite Zeile
```

    Writing neu.txt


Jetzt können wir unserem Programm sagen, durch jede Zeile der Datei zu gehen und etwas zu tun:


```python
for zeile in open('neu.txt'):
    print(zeile)
```

    Erste Zeile
    
    Zweite Zeile


Macht euch keine Sorgen darüber, bereits alles hiervon komplett zu verstehen. For Schleifen werden bald behandelt. Aber wir können schon einmal beleuchten, was wir oben gemacht haben. Wir haben programmiert für jede Zeile der Datei die Zeile auszugeben. Wichtige Punkte hierbei sind:

1. Wir hätten 'zeile' jegliche Bezeichnungen geben können (siehe nächstes Beispiel).
2. Da wir nicht .read() ausgeführt haben, wurde die Datei nicht in den Speicher geladen.
3. Achtet auf die Einrückung der zweiten Zeile Code. Das ist in Python notwendig.

Wir werden später mehr darüber lernen. Als nächstes kommen: Sets und Booleans!


```python
for esz7 in open('neu.txt'):
        print(esz7)
```

    Erste Zeile
    
    Zweite Zeile


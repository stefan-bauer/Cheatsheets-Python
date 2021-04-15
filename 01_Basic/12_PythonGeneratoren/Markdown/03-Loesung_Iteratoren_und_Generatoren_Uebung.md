# Iteratoren und Generatoren Übung - Lösung

Quelle: Datamics

## Aufgabe 1

Erstelle einen Generator, der die Quadratzahlen von Zahlen bis zu einer Zahl N erstellt.


```python
def genquadrate(N):
    for i in range(N):
        yield i ** 2
```


```python
for x in genquadrate(10):
    print(x)
```

    0
    1
    4
    9
    16
    25
    36
    49
    64
    81


## Aufgabe 2

Erstelle einen Generator der N zufällige Nummer zwischen einer unteren und oberen Grenze (das sind die Inputs) ausgibt. Nutzt beispielsweise die random Bibliothek. Zum Beispiel:


```python
import random

random.randint(1,10)
```




    10




```python
def zuf_zahl(unten,oben,N):
    for i in range(N):
        yield random.randint(unten, oben)
```


```python
for num in zuf_zahl(1,10,12):
    print(num)
```

    5
    4
    5
    9
    1
    5
    9
    7
    4
    2
    2
    10


## Aufgabe 3

Verwende die iter() Funktion, um den String zu konvertieren.


```python
s = "Hallo"

# Code hier
s = iter(s)
print(next(s))
```

    H


## Aufgabe 4

Erklärt einen Anwendungsfall für einen Generator durch die Verwendung der yield Anweisung wo du nicht eine normale Funktion mit einer return Anweisung verwenden willst.

<b>Antwort: Wenn der Output potentiell eine große Menge an Speicher benötigt und man nur beabsichtigt zu iterieren, dann würde man einen Generator verwenden.</b>

## Extra Punkte!

Kannst du erklären, was <i>gencomp</i> im Code unten ist? (Hinweis: wir haben das nie in unseren Lektionen gelernt. Ihr könnt Google/Stack Overflow verwenden!)


```python
meine_liste = [1,2,3,4,5]

gencomp = (item for item in meine_liste if item > 3)

for item in gencomp:
    print(item)
```

    4
    5


Hinweis: "generator comprehension" suchen...

# Gut gemacht!

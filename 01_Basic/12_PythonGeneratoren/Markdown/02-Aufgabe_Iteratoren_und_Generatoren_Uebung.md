# Iteratoren und Generatoren Übung - Aufgabe

Quelle: Datamics

## Aufgabe 1

Erstelle einen Generator, der die Quadratzahlen von Zahlen bis zu einer Zahl N erstellt.


```python
def genquadrate(N):
    pass
```


```python
for x in genquadrate(10):
    print(x)
```

## Aufgabe 2

Erstelle einen Generator der N zufällige Nummern zwischen einer unteren und oberen Grenze (das sind die Inputs des Nutzers) ausgibt. Nutzt beispielsweise die random Bibliothek. Zum Beispiel:


```python
import random

random.randint(1,10)
```




    1




```python
def zuf_zahl(unten,oben,N):
    pass
```


```python
for num in zuf_zahl(1,10,12):
    print(num)
```

## Aufgabe 3

Verwende die iter() Funktion, um den String zu konvertieren.


```python
s = "Hallo"

# Code hier

```

## Aufgabe 4

Erklärt einen Anwendungsfall für einen Generator durch die Verwendung der `yield` Anweisung, wo du nicht eine normale Funktion mit einer return Anweisung verwenden willst.

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

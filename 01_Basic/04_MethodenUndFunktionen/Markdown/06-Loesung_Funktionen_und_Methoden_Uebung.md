# Funktionen und Methoden Übung - Lösung

Quelle: Datamics

Vervollständigt die folgenden Fragen:

Schreibe eine Funktion, die das Volumen einer Kugel berechnet, wenn der Radius gegeben ist.


```python
def vol(rad):
    return (4/3)*(3.14)*(rad**3)
```

Schreibe eine Funktion, die überprüft, ob sich eine Zahl in einem bestimmten Bereich (range) befindet.


```python
def  bereich_check(zahl,unten,oben):
    # Überprüfen, ob eine Zahl zwischen unten und oben liegt.
    if zahl in range (unten,oben+1):
        print('%s ist im Bereich',zahl)
```

Und jetzt das gleiche, wenn du nur einen Boolean Wert erhalten wollen würdest.


```python
def bereich_boolean(zahl,unten,oben):
    return zahl in range(unten,oben+1)
```

Schreibe eine Python Funktion, die die groß- und kleingeschriebene Buchstaben in einem String zählt und ausgibt.


```python
def gross_klein(s):
    d={'gross':0,'klein':0}
    for c in s:
        if c.isupper():
            d['gross']+=1
        elif c.islower():
            d['klein']+=1
        else:
            pass
    print('Original String: ',s)
    print('Anzahl großer Buchstaben: ',d['gross'])
    print('Anzahl kleiner Buchstaben: ',d['klein'])
```

Schreibe eine Python Funktion, die eine Liste als Input nimmt und eine weitere Liste ausgibt, die nur noch einzigartige Werte enthält.


```python
def einzig_liste(l):
    x=[]
    for a in l:
        if a not in x:
            x.append(a)
    return x
```

Schreibe eine Funktion, die alle Werte innerhalb einer Liste multipliziert.


```python
def multi(zahlen):
    total = 1
    for x in zahlen:
        total *= x
    return total
```

Schreibe eine Python Funktion, die überprüft, ob ein eingegebener String ein Palindrom ist, oder nicht.

Hinweis: Ein Palindrom ist ein Wort, das vorwärts und rückwärts gleich gelesen wird. Zum Beispiel: Otto.


```python
def palindrom(s):
    s = s.replace(' ','') # Alle Leerzeichen ersetzen
    return s == s[-1]
```

#### Schwer:

Schreibe eine Funktion, die überprüft, ob ein Satz ein Pangramm ist.

Hinweis: Ein Pangramm ist ein Satz, der jeden Buchstaben des Alphabets enthält.

Hinweis: Schaut euch das String Modul an


```python
import string

def pangramm(s, alphabet=string.ascii_lowercase):
    alphaset = set(alphabet)
    return len(alphaset) <= len(set(s.lower()))
```

## Gute Arbeit!

# Durchzählen

Quelle: Datamics

In dieser Lektion werden wir mehr über die extrem nützliche vorinstallierte Funktion enumerate() (dt.: durchzählen) lernen. Enumerate erlaubt es uns durchzuzählen, während wir durch ein Objekt iterieren. Dies tut sie, indem ein Tupel in der Form (Zähler, Element) zurückgegeben wird. Die Funktion selbst ist äquivalent zu:
    
    def enumerate(sequenz, start=0):
        n = start
        for elem in sequenz:
            yield n, elem
            n += 1
            
## Beispiel


```python
lst = ['a','b','c']

for nummer, item in enumerate(lst):
    print(nummer)
    print(item)
```

    0
    a
    1
    b
    2
    c


enumerate() wird besonders wichtig, wenn wir eine Art Limit bzw. einen Auslöser haben. Zum Beispiel:


```python
for zähler, item in enumerate(lst):
    if zähler >=2:
        break
    else:
        print(item)
```

    a
    b


Toll! Ihr solltet jetzt verstehen, was enumerate() macht und wie wir es sinnvoll verwenden können.

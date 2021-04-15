# Collections Module

Quelle: Datamics

Das Collections (dt.: Sammlungen) Modul ist ein vorinstalliertes (built-in) Modul, das spezielle Behälter Daten typen implementiert, die eine Alternative zu Python's vorinstallierten Behältern bieten. Die Grundlagen kennen wir bereits: Dict, Liste, Set und Tupel.

Jetzt lernen wir mehr über die Alternativen, die das Collections Modul bietet.

## Counter

*Counter* ist eine Unterklasse des Dictionary, die dabei hilft, zerlegbare Objekte zu zählen. Innerhalb davon sind die Elemente als Dictionary Key gespeichert und ihre Anzahl als Wert.

Hier sehen wir, wie Counter benutzt werden kann:


```python
from collections import Counter
import collections
```

### Counter mit Listen


```python
l = [1,2,2,2,2,3,3,3,1,2,1,12,3,2,32,1,21,1,223,1]

Counter(l)
```




    Counter({1: 6, 2: 6, 3: 4, 12: 1, 21: 1, 32: 1, 223: 1})



### Counter mit Strings


```python
Counter('aabsbsbsbhshhbbsbs')
```




    Counter({'a': 2, 'b': 7, 'h': 3, 's': 6})



### Counter mit Wörtern in einem Satz


```python
s = 'Wie oft taucht jedes einzelne Wort in diesem Satz aus vielen Worten auf?'

words = s.split()

Counter(words)
```




    Counter({'Satz': 1,
             'Wie': 1,
             'Wort': 1,
             'Worten': 1,
             'auf?': 1,
             'aus': 1,
             'diesem': 1,
             'einzelne': 1,
             'in': 1,
             'jedes': 1,
             'oft': 1,
             'taucht': 1,
             'vielen': 1})




```python
# Methoden mit Counter()
c = Counter(words)

c.most_common(2)
```




    [('Wie', 1), ('oft', 1)]



### Übliche Muster mit dem Counter() Objekt


```python
sum(c.values())                 # Summe aller Anzahlen
c.clear()                       # Alle Anzahlen zurücksetzen
list(c)                         # Einzigartige Elemente anzeigen
set(c)                          # In ein Set konvertieren
dict(c)                         # In ein reguläres Dictionary konvertieren
c.items()                       # In eine Liste aus (Element, Anzahl) Paaren konvertieren
Counter(dict(liste_aus_paaren)) # Aus einer Liste aus (Element, Anzahl) Paaren konvertieren
c.most_common()[:-n-1:-1]       # n wenigst häufige Elemente
c += Counter()                  # 0 und negative Anzahlen entfernen
```

## DefaultDict

`defaultdict` ist ein Dictionary ähnliches Objekt, welches alle Methoden bietet, die auf Dictionaries anwendbar sind. Es nimmt allerdings den ersten Parameter (default_factory) als Datentyp für das Dictionary. `defaultdict` zu benutzen ist schneller, als das selbe mit dict.set_default zu lösen.

**Ein defaultdict wird nie den Key Error anzeigen. Jeder Key, der nicht existiert, bekommt den Wert des default_factory zugewiesen.**


```python
from collections import defaultdict
```


```python
d = {}
```


```python
d["eins"]
```




    <object at 0x10e680b30>




```python
d = defaultdict(object)
```


```python
d["eins"]
```




    <object at 0x10e680b40>




```python
for item in d:
    print(item)
```

    eins


Kann auch mit Standardwerten initialisiert werden:


```python
d = defaultdict(lambda: 0)
```


```python
d["eins"]
```




    0



## OrderedDict

Ein `OrderedDict` ist eine Dictionary Unterklasse, die sich merkt, in welcher Reihenfolge sein Inhalt hinzugefügt wurde.

Zum Beispiel ein normales Dictionary:


```python
print("Normales Dictionary:")

d = {}

d['a'] = 'A'
d['b'] = 'B'
d['c'] = 'C'
d['d'] = 'D'
d['e'] = 'E'


for k, v in d.items():
    print(k, v)
```

    Normales Dictionary:
    a A
    b B
    c C
    d D
    e E


Und im Vergleich ein OrderedDict:


```python
print("Geordnetes Dictionary:")

d = collections.OrderedDict()

d['a'] = 'A'
d['b'] = 'B'
d['c'] = 'C'
d['d'] = 'D'
d['e'] = 'E'


for k, v in d.items():
    print(k, v)
```

    Geordnetes Dictionary:
    a A
    b B
    c C
    d D
    e E


### Gleichheit mit OrderedDict

Ein gewöhnliches Dictionary schaut sich seinen Inhalt an, wenn es auf Gleichheit überprüft wird. Ein OrderedDict berücksichtigt neben dem Inhalt auch die Reihenfolge der Items.


```python
print("Normales Dictionary:")
print("Sind sie gleich?")

d1 = {}
d1['a'] = 'A'
d1['b'] = 'B'

d2 = {}
d2['b'] = 'B'
d2['a'] = 'A'

print(d1 == d2)
```

    Normales Dictionary:
    Sind sie gleich?
    True



```python
print("Geordnetes Dictionary:")
print("Sind sie gleich?")

d1 = collections.OrderedDict()
d1['a'] = 'A'
d1['b'] = 'B'

^
d2 = collections.OrderedDict()

d2['b'] = 'B'
d2['a'] = 'A'

print(d1 == d2)
```

    Geordnetes Dictionary:
    Sind sie gleich?
    False


## namedtuple

Das normale Tupel verwendet numerische Indizes, um auf seinen Inhalt zuzugreifen. Zum Beispiel:


```python
t = (12,13,14)
```


```python
t[0]
```




    12



Für einfache Anwendungen ist das für gewöhnlich ausreichend. Andererseits kann es zu Errors führen, wenn wir versuchen den Index für jedes Element zu speichern. Insbesondere wenn das Tupel an einer anderen Stelle im Code erstellt wird und/oder viele Elemente beinhaltet. Ein `namedtuple` weist Namen sowie numerische Indizes zu jedem Mitglied zu.

Jede Art von `namedtuple` wird durch seine eigene Klasse repräsentiert, die man durch die namedtupel() Funktion erstellt. Die Parameter sind erstens der Name und zweitens ein String, der die Namen der Elemente beinhaltet.

Wir können uns namedtuples als schnelle Variante zur Erstellung von Objekten/Klassen merken. Zum Beispiel:


```python
from collections import namedtuple
```


```python
Hund = namedtuple("Hund", "Alter Rasse Name")

Sam = Hund(Alter=2,Rasse="Schäferhund",Name="Sam")

Frank = Hund(Alter=3,Rasse="Mops",Name="Frank")
```

Wir erstellen ein `namedtuple` also so, dass wir zuerst den Objektnamen (Hund) festlegen und dann die Vielzahl an Feldern als einen String mit Leerzeichen zwischen den Namen. Wir können anschließend verschiedene Attribute aufrufen:


```python
Sam
```




    Hund(Alter=2, Rasse='Schäferhund', Name='Sam')




```python
Sam.Alter
```




    2




```python
Sam.Rasse
```




    'Schäferhund'




```python
Sam[2]
```




    'Sam'



## Abschluss

Hoffentlich könnt ihr am Ende dieser Lektion nachvollziehen wie nützlich das Collections Modul ist.

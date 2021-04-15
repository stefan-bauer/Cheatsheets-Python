# Ausgabe Formatierung
Quelle: Datamics
In dieser Lektion werden wir kurz behandeln, auf welche verschiedene Arten wir unsere print Anweisungen formatieren können. Da wir mehr und mehr programmieren wird es nützlich sein, print Anweisungen zu haben, in denen eine Variable eingesetzt wird.

Das einfachste Beispiel für eine print Anweisung ist folgendes:


```python
print("Das ist ein String")
```

    Das ist ein String


## Strings

Wir können %s nutzen, um Strings in unser print Statement einzufügen.


```python
s = 'STRING'
print('Setze einen String mit einem mod und s ein: %s' %(s))
```

    Setze einen String mit einem mod und s ein: STRING


## Kommazahlen

Kommazahlen nutzen das Format %n1.n2f, wobei das n1 für die Mindestanzahl an Stellen bestimmt, die der String beinhalten soll. Diese werden durch Leerzeichen ersetzt, sollte die Zahl nicht so viele Stellen haben. Der n2 Platzhalter steht dafür, wie viele Zahlen nach dem Dezimalpunkt angezeigt werden sollen. Schauen wir uns einige Beispiele an:


```python
print('Kommazahlen: %1.2f' %(13.144))
```

    Kommazahlen: 13.14



```python
print('Kommazahlen: %1.0f' %(13.144))
```

    Kommazahlen: 13



```python
print('Kommazahlen: %1.5f' %(13.144))
```

    Kommazahlen: 13.14400



```python
print('Kommazahlen: %10.2f' %(13.144))
```

    Kommazahlen:      13.14



```python
print('Kommazahlen: %25.2f' %(13.144))
```

    Kommazahlen:                     13.14


## Umwandlungsformat Methoden

Es sollte an dieser Stelle angemerkt werden, dass die zwei Methoden %s und &r jedes Python Objekt in einen String umwandeln. Dabei werden zwei unterschiedliche Methoden verwendet: str() und repr(). Wir werden später noch mehr über diese Methoden lernen, aber wir können uns bereits merken, dass nahezu jedes Python Objekt durch diese Methoden übergeben werden kann.


```python
print('Hier ist eine Nummer: %s. Hier ist ein String: %s' %(123.1,'Hi'))
```

    Hier ist eine Nummer: 123.1. Hier ist ein String: Hi



```python
print('Hier ist eine Nummer: %r. Hier ist ein String: %r' %(123.1,'Hi'))
```

    Hier ist eine Nummer: 123.1. Hier ist ein String: 'Hi'


## Multiples Formatieren

Wir können ein Tupel an das mod Symbol übergeben um multiple Formate in unserem print Statement auszugeben:


```python
print('Erstens: %s, Zweitens: %1.2f, Drittens: %r' %('Hi!',3.14,22))
```

    Erstens: Hi!, Zweitens: 3.14, Drittens: 22


## Nutzen der string .format() Methode

Der beste Weg um Objekte in unsere Strings zu formatieren ist es, die `format` Methode zu nutzen. Die Syntax lautet:

    'String hier {var1} und {var2}' .format(var1='Etwas1',var2='Etwas2')
    
Hier sind einige Beispiele:


```python
print('Das ist ein String mit einer {p}' .format(p='Einfügung'))
```

    Das ist ein String mit einer Einfügung



```python
# Mehrere male:
print('Eins: {p}, Zwei: {p}, Drei: {p}' .format(p='Hi!'))
```

    Eins: Hi!, Zwei: Hi!, Drei: Hi!



```python
# Mehrere Objekte:
print('Objekt 1: {a}, Objekt 2: {b}, Objekt 3: {c}' .format(a=1,b='zwei',c=12.3))
```

    Objekt 1: 1, Objekt 2: zwei, Objekt 3: 12.3


Das sind die Grundlagen der String Formatierung. Denkt daran, dass Python 2 die print "..." Anweisung nutzt, nicht die print Funktion!

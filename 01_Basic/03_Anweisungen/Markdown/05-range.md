# range()

Quelle: Datamics

In dieser kurzen Lektion werden wir die `range` Funktion diskutieren. Wir haben bisher noch kein tiefgreifendes Verständnis für Funktionen, aber wir können die Grundlagen dieser einfachen (aber extrem nützlichen!) Funktion verstehen. 

range() erlaubt es uns, eine Liste von Nummern anzulegen, die von einem Startpunkt zu einem Endpunkt reichen. Wir können dabei außerdem die Schrittgröße festlegen. Die Syntax von `range` sieht folgendermaßen aus:

    range(start,ende,schrittgröße)

Worauf wir in Python 3 achten müssen ist, dass `range` uns nicht gleich eine Liste ausgibt. Um das zu erreichen können wir die `list` Funktion verwenden, welche syntaktisch wie folgt aussieht:

    list(object)

Wir können jetzt ein paar Beispiele durchgehen:


```python
list(range(0,10))
```




    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]




```python
x = list(range(0,10))
type(x)
```




    list




```python
start = 0 # Standard
stop = 20
x = list(range(start,stop))
```


```python
x
```




    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]



Großartig! Achtete darauf, wie es bis zur 20 hochging, diese aber nicht beinhaltet. Genau wie beim Indexieren. Wie können wir nun die Schrittgröße eingeben? Wir können einen dritten Parameter übergeben:


```python
x = list(range(start,stop,2))
# Check
x
```




    [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]



Toll! Das war's...oder doch nicht?

### Warunung: Speicher!

Ihr könntet euch fragen, was passiert, wenn wir eine riesige Bandbreite von zahlen erstellen wollen? Wie kann mein Computer das alles im Speicher behalten?

Gut mitgedacht! Das ist ein Dilemma, das durch die Verwendung eines Generators umgangen werden kann. Eine vereinfachte Erklärung: Ein Generator erlaubt die Generierung von generierten Objekten die im dieser Instanz bereitgestellt werden, aber nicht wirklich im Speicher abgelegt werden.

Das bedeutet, dass der Generator keine Liste erstellt, wie es range() tut. Stattdessen werden die Zahlen in der Bandbreite einmalig erzeugt. Python 2 hat einen vorinstallierten range Generator names xrange(). Es ist empfehlenswert xrange() für for Loops in Python 2 zu nutzen.

Die gute Nachricht ist, dass sich range() in Python 3 wie ein Generator verhält und ihr euch keine weiteren Sorgen machen müsst. Jetzt noch schnell ein Beispiel für xrange().


```python
for num in range(10):
    print(num)
```

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9



```python
# In Python 2 bietet sich xrange() an
# Der Code funktioniert so nicht in Python 3
for num in xrange(10):
    print(num)
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-13-4bc70a6aca1c> in <module>()
          1 # In Python 2 bietet sich xrange() an
          2 # Der Code funktioniert so nicht in Python 3
    ----> 3 for num in xrange(10):
          4     print(num)


    NameError: name 'xrange' is not defined


Wir werden Errors in einer späteren Lektion genauer untersuchen. Es sei aber bereits darauf verwiesen, dass uns dieser Error anzeigt, dass `xrange` nicht definiert ist. Das liegt daran, dass wir Python 3 verwenden.

Der wichtige Takeaway hier ist, dass wenn ihr range() verwenden möchtet, das Ergebnis aber nicht in einer Liste speichern müsst, ihr in Python 2 besser xrange() verwendet. In Python 3 könnt ihr in jedem Fall range() verwenden.

Ihr solltet nun verstanden haben, wie man range() in den beiden Python Versionen anwendet.

# Iteratoren und Generatoren

Quelle: Datamics

In diesem Abschnitt des Kurses werden wir mehr über die Unterschiede von Iteration und Generation in Python lernen. Und darüber hinaus, wie wir durch die `yield` Anweisung unsere eigenen Generatoren erstellen können. Generatoren erlauben es uns, zu generieren während wir fortschreiten, anstatt alles im Speicher zu halten.

Wir haben das bereits thematisiert, als wir uns die range() Funktion in Python 2 und die entsprechende xrange() Funktion angeschaut haben, von denen letztere ein Generator ist.

Wir können das ein wenig vertiefen. Wir wissen bereits, wie wir mit <b>def</b> und <b>return</b> Funktionen erstellen können. Generator Funktionen erlauben es uns, eine Funktion zu schreiben, die einen Wert ausgibt und später dort weitermacht, wo sie aufgehört hat. Diese Art von Funktion ist in Python ein Generator, der es uns erlaubt über Zeit hinweg eine Sequenz von Werten zu generieren. Der Hauptunterschied im Sinne der Syntax wird die <b>yield</b> Anweisung sein.

In den meisten Aspekten wirken Generatoren wie normale Funktionen. Sie unterscheiden sich hauptsächlich darin, dass eine Generator Funktion, sobald sie kompiliert wird, zu einem Objekt wird, das Iteration unterstützt. Das bedeutet, dass sie beim Ausführen nicht nur einen Wert zurückgeben und dann aussteigen wird. Die Generator Funktion wird automatisch aussetzen, aber an dieser Stelle bleiben. Der größte Vorteil davon liegt darin, dass nicht immer alle Werte von Anfang an berechnet werden müssen, sondern die Generator Funktion nach vorherigen Berechnungen pausiert wird. Dieses Feature nennt man <i>state suspension</i>. 

Um ein besseres Verständnis für Generatoren zu erhalten, lasst uns einige erstellen:


```python
# Generator Funktion für den Raum einer Nummer (hoch 3)
def genraum(n):
    for num in range(n):
        yield num**3
```


```python
for x in genraum(10):
    print(x)
```

    0
    1
    8
    27
    64
    125
    216
    343
    512
    729


Wunderbar! Jetzt wo wir eine Generator Funktion erstellt haben, müssen wir nicht auf jeden einzelnen Raum achten, den wir erstellt haben. 

Generatoren sind am besten dafür geeignet, große Sets von Ergebnissen zu berechnen. Und das in Fällen, in denen wir keinen Speicher für alle Ergebnisse auf einmal aufbringen wollen.

Wie wir bereits in vorherigen Lektionen angemerkt haben geben viele Standard Funktionen, die in Python 2 noch Listen erzeugt haben, jetzt in Python 3 Generatoren aus.

Lasst uns als weiteres Beispiel Fibonacci Reihen wählen:


```python
def genfibon(n):
    '''
    Eine Fibonacci Reihe bis zur Zahl n erstellen
    '''
    a = 1
    b = 1
    for i in range(n):
        yield a
        a,b = b,a+b
```


```python
for num in genfibon(10):
    print(num)
```

    1
    1
    2
    3
    5
    8
    13
    21
    34
    55


Was wäre, wenn das eine normale Funktion wäre? Wie würde sie aussehen?


```python
def fibon(n):
    a = 1
    b = 1
    output = []
    
    for i in range(n):
        output.append(a)
        a,b = b,a+b
        
    return output
```


```python
fibon(10)
```




    [1, 1, 2, 3, 5, 8, 13, 21, 34, 55]



Achtet darauf, dass wenn wir einen großen Wert für n (z.B. 100000) eingeben würden, die zweite Funktion alle einzelnen Ergebnisse speichern müsste. Dabei brauchen wir eigentlich immer nur das vorherige Ergebnis, um das nächste zu berechnen!

## next() und iter()

Die beiden vorinstallierten (build-in) Funktionen next() und iter() sind ein wichtiger Schlüssel zum vollen Verständnis von Generatoren.

Die `next` Funktion erlaubt es uns, das nächste (next) Element einer Sequenz zu wählen. Seht her:


```python
def simple_gen():
    for x in range(3):
        yield x
```


```python
# simple_gen zuweisen
g = simple_gen()
```


```python
print(next(g))
```

    0



```python
print(next(g))
```

    1



```python
print(next(g))
```

    2



```python
print(next(g))
```


    ---------------------------------------------------------------------------

    StopIteration                             Traceback (most recent call last)

    <ipython-input-13-bc24f410ad62> in <module>()
    ----> 1 print(next(g))
    

    StopIteration: 


Nachdem wir alle Werte erzeugt haben, führte next() zu einem <i>Stopiteration</i> Error. Worüber uns dieser Error informiert, ist die Tatsache, dass alle Werte erzeugt wurden.

Ihr könntet euch wundern, warum wir diesen Error nicht bei Schleifen erhalten? Die for Schleife achtet selbst auf diesen Error und stoppt dann die Durchführung. 

Lasst uns fortschreiten und sehen, wie wir iter() verwenden. Ihr wisst sicherlich noch, dass Strings iterierbar sind:


```python
s = "hallo"

# Über String iterieren
for buchst in s:
    print(buchst)
```

    h
    a
    l
    l
    o


Das bedeutet allerdings nicht, dass Strings selbst ein Iterator sind. Wir können das mit der next() Funktion überprüfen:


```python
next(s)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-15-bc0566bea448> in <module>()
    ----> 1 next(s)
    

    TypeError: 'str' object is not an iterator


Interessant! Das bedeutet, dass String Objekte Iteration unterstützen, wir aber nicht direkt darüber iterieren können, wie es eine Generator Funktion könnte. Die iter() Funktion erlaubt uns genau das!


```python
s_iter = iter(s)
```


```python
next(s_iter)
```




    'h'




```python
next(s_iter)
```




    'a'



Großartig! Jetzt wisst ihr, wie man Objekte die iterierbar sind in Iteratoren selbst umwandelt!

Der größte Takeaway von dieser Lektion ist es, das `yield` Kennwort zu benutzen, um aus einer Funktion einen Generator zu machen. Diese Änderung kann euch eine Menge Speicherkapazität in Anwendungsfällen sparen.

# Fortgeschrittene Listen

Quelle: Datamics

In diesem Abschnitt unseres Kurses werden wir uns etwas genauer mit den Methoden auseinandersetzen, die uns für Listen zur Verfügung stehen. Das sind offiziell keine "fortgeschrittenen" Methoden, nur Methoden, die uns typischer Weise nicht begegnen würden, sofern wir nicht genauer hinschauen. Andererseits könntet ihr manche davon bereits entdeckt haben.

Lasst uns beginnen!


```python
l = [1,2,3]
```

# Anfügen

Eine Methode die ihr sicherlich bereits genutzt habt ist append(), um Elemente an das Ende einer Liste anzufügen. 


```python
l.append(4)
# Check
l
```




    [1, 2, 3, 4]



## Zählen

Wir haben count() bereits in der Methoden Lektion diskutiert, aber hier kommt es noch einmal kurz. count() nimmt ein Element als Parameter und gibt aus, wie häufig es in der Liste erscheint.


```python
l.count(10)
```




    0




```python
l.count(2)
```




    1



## Erweitern

Oft ist es anfangs etwas schwer den Unterschied zwischen anfügen und erweitern zu differenzieren. Also merkt euch:

<b>append: Element an das Ende anfügen</b>


```python
x = [1,2,3]
x.append([4,5])
print(x)
```

    [1, 2, 3, [4, 5]]


<b>extend: Hängt nacheinander Elemente einzeln ans Ende an</b>


```python
x = [1,2,3]
x.extend([4,5])
print(x)
```

    [1, 2, 3, 4, 5]


Achtet darauf, wie extend jedes einzelne Element (nacheinander) anhängt und append das ganze Element. Das ist der Hauptunterschied.

## Index

index() gibt den Index des Elements zurück, das man als Parameter eingibt. Hier wird ein Error erzeugt, sofern das Element gar nicht enthalten ist.


```python
l.index(2)
```




    1




```python
l.index(12)
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-9-3f090052d656> in <module>()
    ----> 1 l.index(12)
    

    ValueError: 12 is not in list


## Einfügen

Die Methode insert(index, objekt) hat zwei Parameter. Index zeigt die Stelle an, an der das Objekt eingefügt werden soll. Zum Beispiel:


```python
l
```




    [1, 2, 3, 4]




```python
# Einen String am Index 2 einfügen
l.insert(2,'String')
```


```python
# Check
l
```




    [1, 2, 'String', 3, 4]



## Fallen lassen

Ihr habt bestimmt schon die pop() Methode gesehen, die das letzte Element der Liste entfernt.


```python
ele = l.pop()
```


```python
l
```




    [1, 2, 'String', 3]




```python
ele
```




    4



## Entfernen

Die remove() Methode entfernt die erste Erscheinung eines Wertes. Seht hier:


```python
l
```




    [1, 2, 'String', 3]




```python
l.remove('String')
```


```python
l
```




    [1, 2, 3]




```python
l = [1,2,3,4,3]
```


```python
l.remove(3)
```


```python
l
```




    [1, 2, 4, 3]



## Umkehren

Um die Elemente einer Liste in umgekehrter Reihenfolge aufzulisten, verwenden wir die reverse() Methode. Das beeinflusst die Liste permanent.


```python
l.reverse()
```


```python
l
```




    [3, 4, 2, 1]



## Sortieren

sort() ordnet die Liste nachhaltig:


```python
l
```




    [3, 4, 2, 1]




```python
l.sort()
```


```python
l
```




    [1, 2, 3, 4]



Toll! Ihr solltet jetzt ein Verständnis von all den Methoden haben, die es in Python für Listen gibt!

# Zip

Quelle: Datamics

zip() erstellt einen Iterator, der Elemente aus allen iterierbaren Objekten zusammenfasst.

Sie gibt einen Iterator aus Tupeln zurück, in dem das i-te Tupel die i-ten Elemente der (per Parameter) eingegebenen Sequenzen enthält. Dieser Iterator hält an, sobald das letzte Element des kürzesten Input erreicht ist. 

zip() ist gleich zu folgender Funktion:

    def zip(*iterables):
        # zip('ABCD', 'xy') --> Ax By
        sentinel = object()
        iterators = [iter(it) for it in iterables]
        while iterators:
            result = []
            for it in iterators:
                elem = next(it, sentinel)
                if elem is sentinel:
                    return
                result.append(elem)
            yield tuple(result)
            
zip() sollte nur mit Inputs ungleicher Länge ausgeführt werden, wenn das Abschneiden des überstehenden Endes egal ist.

Lasst uns ein bisschen Action sehen:


```python
x = [1,2,3]
y = [4,5,6]

# Zip auf die Listen anwenden
list(zip(x,y))
```




    [(1, 4), (2, 5), (3, 6)]



Gemerkt, wie wir Tupel als Ergebnis erhalten haben? Was passiert, wenn ein Input länger ist als der andere?


```python
x = [1,2,3]
y = [4,5,6,7,8]

# Zip auf die Listen anwenden
list(zip(x,y))
```




    [(1, 4), (2, 5), (3, 6)]



Achtet darauf, wie das Ergebnis von zip() durch das kürzeste Input Element bestimmt wird. Insgesamt ist es nicht empfohlen Inputs ungleicher Länge zu verwenden. Außer ihr seid wirklich sicher, dass ihr nur einen Teil des Inputs braucht.

Was passiert, wenn wir Dictionaries per zip() zusammenführen wollen?


```python
d1 = {'a':1,'b':2}
d2 = {'c':4,'d':5}

list(zip(d1,d2))
```




    [('a', 'c'), ('b', 'd')]



Das ergibt deshalb Sinn, weil wir nur die Keys erhalten, wenn wir durch ein Dictionary iterieren. Wir müssen Methoden aufrufen, falls wir Keys und Werte haben wollen:


```python
list(zip(d2,d1.values()))
```




    [('c', 1), ('d', 2)]



Großartig! Lasst uns zum Schluss zip() benutzen, um Keys und Werte der zwei Dictionaries zu tauschen.


```python
def switcharoo(d1,d2):
    dout = {}
    
    for d1key,d2val in zip(d1,d2.values()):
        dout[d1key] = d2val
    
    return dout
```


```python
switcharoo(d1,d2)
```




    {'a': 4, 'b': 5}



Toll! Ihr könnt zip() einsetzen, um eine Menge tippen zu sparen! Und das in vielen Situationen!

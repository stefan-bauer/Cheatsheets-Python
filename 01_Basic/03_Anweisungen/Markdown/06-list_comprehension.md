# Listen Abstraktion 

Quelle: Datamics

In Ergänzung zu Sequenz Anwendungen und Listen Methoden enthält Python eine etwas fortgeschrittenere Operation namens `list comprehension` (dt.: Listen Abstraktion).

*Randnotiz: List Comprehension hätte fast die Funktionen map, reduce und filter ersetzt, mit denen wir uns später noch detailliert befassen werden.*

`list comprehension` erlaubt es uns, Listen durch eine andere Notation zu erstellen. Wir können uns es im Grunde als einzeilige `for` Schleife innerhalb von Klammern vorstellen.

Jeden, der mit der Mathematik vertraut ist, dürfte Listen Abstraktion an die mathematische Notation von Mengen erinnern.

Ein einfaches Beispiel für Listen Abstraktion:


```python
# Jeden Buchstaben eines Strings erfassen
lst = [x for x in 'Wort']
```


```python
# Check
lst
```




    ['W', 'o', 'r', 't']



Das ist das Grundkonzept von list comprehension. Wenn ihr euch etwas mit mathematischer Notation auskennt, sollte euch dieses Format bekannt vorkommen. Zum Beispiel: x^2, x ∈ {0,1,2,...,10}

Lasst uns noch ein paar weitere Beispiel betrachten:


```python
# Quadratzahlen eines range() in eine Liste schreiben
lst = [x**2 for x in range(1,11)]
```


```python
# Check
lst
```




    [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]




```python
# Check for even numbers in a range
lst = [x for x in range(11) if x % 2 == 0]
```


```python
# Check
lst
```




    [0, 2, 4, 6, 8, 10]




```python
# Convert Celsius to Fahrenheit
celsius = [0,10,20.1,34.5]

fahrenheit = [ ((float(9)/5)*temp + 32) for temp in celsius ]

# Check
fahrenheit
```




    [32.0, 50.0, 68.18, 94.1]




```python
lst = [ x**2 for x in [x**2 for x in range(11)]]
# Check
lst
```




    [0, 1, 16, 81, 256, 625, 1296, 2401, 4096, 6561, 10000]



Später im Kurs werden wir noch zu Generator Abstraktion kommen. Nach dieser Lektion solltet ihr euch im Umgang mit dem Lesen und Schreiben von list comprehension wohl fühlen.

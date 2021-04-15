# Lambda Ausdrücke

Quelle: Datamics

Eines der nützlichsten (und für Anfänger verwirrendsten) Tools von Python ist der Lambda Ausdruck. Lambda Ausdrücke erlauben es uns "anonyme" Funktionen zu erstellen. Das bedeutet, dass wir schnell ad-hoc Funktionen erstellen können, ohne eine Funktion ordnungsgemäß mit def definieren zu müssen.

Anonyme Funktionen sind insbesondere bei der Verwendung von `map`, `reduce` und `filter` von Vorteil. Wir werden auf diese drei Funktionen in gesonderten Kapiteln später im Kurs eingehen.

Funktions-Objekte, die von Lambda Ausdrücken zurückgegeben werden, funktionieren genau gleich wie solche, die durch `def` erstellt wurden. Der besondere Unterschied, der Lambda in manchen Fällen so nützlich macht, ist folgender:

**Lambda's Aufbau besteht aus einem einzigen Ausdruck.**

Der Aufbau von Lambda ist gleich dem, den wir nach `def` schreiben würden. Wir schreiben das Ergebnis nur als Ausdruck, im Gegensatz dazu, es explizit zurückzugeben. Weil es auf einen Ausdruck limitiert ist, ist ein Lambda weniger allgemein als ein def. Wir können somit nur das Design verschmälern, um Verschachtelung zu limitieren. Lambda ist dafür gedacht, einfache Funktionen zu coden, wohingegen def größere Aufgaben erledigt.

Dabei kann Lambda eine beliebige Anzahl von Parametern aufnehmen, in seinem Ausdruck verarbeiten und schließlich immer ein einziges Ergebnis zurückgeben.

Lasst uns uns einem Lambda Ausdruck langsam nähern, indem wir eine Funktion nach und nach zusammenfassen.


```python
def square(num):
    result = num**2
    return result
```


```python
square(2)
```




    4




```python
# Zusammenfassen
def square(num):
    return num**2
```


```python
square(3)
```




    9




```python
# Alles in eienr Zeile geschrieben, obwohl es sonst schlechter Style ist
def square(num): return num**2
```


```python
square(4)
```




    16



Diese Form versucht ein Lambda zu ersetzen. Sie kann dann folgendermaßen geschrieben werden:


```python
lambda num: num**2
```




    <function __main__.<lambda>>




```python
# Diese Funktion einem Namen zuweisen:
square = lambda num: num**2
```


```python
square(5)
```




    25



Und hier haben wir es! Die Zusammenfassung einer Funktion zu einem Lambda Audruck. Schauen wir uns einige weitere Beispiele an:

### Beispiel 1: Überprüfen ob eine Zahl gerade ist


```python
even = lambda x: x%2==0
```


```python
even(3)
```




    False




```python
even(4)
```




    True



### Beispiel 2: Erstes Zeichen eines Strings ausgeben


```python
erstes = lambda s: s[0]
```


```python
erstes('Hallo')
```




    'H'



### Beispiel 3: Einen String umkehren


```python
umk = lambda s: s[::-1]
```


```python
umk('Hallo')
```




    'ollaH'



### Beispiel 4: Genau wie bei normalen Funktionen können wir mehr als einen Parameter aufnehmen


```python
add = lambda x,y: x+y
```


```python
add(3,4)
```




    7



Lambda Ausdrücke können in Verbindung mit map(), filter() und reduce() wirklich glänzen. Jede dieser Funktionen hat eine eigene Lektion. Wenn ihr wirklich an Lambda interessiert seid, dann könnt ihr euch diese anschauen.

# Eingebaute Funktionen Test

Quelle: Datamics

Für diesen Test solltet ihr die eingebauten Funktionen genutzt haben, um die benötigten Funktionen in einer Zeile Code zu schreiben.

## Aufgabe 1

Nutzt map(), um eine Funktion zu schreiben, die die Länge jedes einzelnen Wortes in einem String (durch Leerzeichen getrennt) herausfindet und die Werte in einer Liste zurückgibt.

Diese Funktion wird als Input eine Phrase haben und eine Liste von Zahlen ausgeben.


```python
def wort_laenge(phrase):
    
    return list(map(len, phrase.split()))
```


```python
wort_laenge("Wie lange sind die Wörter dieser Phrase")
```




    [3, 5, 4, 3, 6, 6, 6]



## Aufgabe 2

Nutzt reduce(), um eine Liste von Stellen einzulesen und die entsprechende Zahl ausgibt. 

Wandelt die Zahlen des Inputs nicht in einen String um! 


```python
from functools import reduce

def stellen_zu_zahlen(stellen):
    
    return reduce(lambda x,y: x*10 + y,stellen)
```


```python
stellen_zu_zahlen([3,4,3,2,1])
```




    34321



## Aufgabe 3

Nutzt filter(), um alle Wörter aus einer Liste auszugeben, die mit einem bestimmten Buchstaben beginnen.


```python
def filter_woerter(wort_liste, buchstabe):
    
    return list(filter(lambda wort: wort[0]==buchstabe,wort_liste))
```


```python
l = ["Hallo","sind","Katze","Hund","Schinken","Hi","gehen","zu","Herz"]
filter_woerter(l,"H")
```




    ['Hallo', 'Hund', 'Hi', 'Herz']



## Aufgabe 4

Nutze zip() und Listen Verständnis, um eine Liste auszugeben, deren Werte zwei Strings aus Liste1 und Liste2, die mit einem Konnektor verbunden wurden.


```python
def verbinden(L1, L2, konnektor):
    
    return [wort1+konnektor+wort2 for (wort1,wort2) in zip(L1,L2)]
```


```python
verbinden(['A','B'],['a','b'],'-')
```




    ['A-a', 'B-b']



## Aufgabe 5

Benutze enumerate() und andere Skills, um ein Dictionary zu erstellen, dass die Werte einer Liste als Key hat und deren Index als Wert. Ihr könnt davon ausgehen, dass ein Wert nur einmal in der Liste vorkommt. 


```python
def dict_liste(L):
    
    return {key:value for value,key in enumerate(L)}
```


```python
dict_liste(["a","b","c"])
```




    {'a': 0, 'b': 1, 'c': 2}



## Aufgabe 6

Nutze enumerate() und andere Skills von oben, um den count der Anzahl von Items in einer Liste auszugeben, deren Wert ihrem Index entspricht.


```python
def count_treffer_index(L):
    
    return len([num for count, num in enumerate(L) if num == count])
```


```python
count_treffer_index([0,2,2,1,5,5,6,10])
```




    4



# Gute Arbeit!

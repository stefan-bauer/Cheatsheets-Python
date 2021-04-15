# Sets und Booleans

Quelle: Datamics

Es gibt zwei weitere Objekt Arten in Python, die wir uns anschauen sollten: Sets und Booleans.

## Sets

Sets sind ungeordnete Sammlungen von einzigartigen Elementen. Wir können sie erstellen, indem wir die `set()` Funktion nutzen. Lasst uns fortfahren und ein Set erstellen, um zu verstehen, wie es funktioniert:


```python
x = set()
```


```python
# Wir fügen Elemente zu Sets durch die add() Funktion hinzu
x.add(1)
```


```python
# Check
x
```




    {1}



Die geschweiften Klammern bemerkt? Das bedeutet allerdings nicht, dass wir hier ein Dictionary haben! Nichtsdestotrotz lassen sich Parallelen ziehen und ein Set kann als Dictionary verstanden werden, das nur Keys beinhaltet.

Wir wissen bereits, dass Sets einzigartige Elemente beinhalten. Was passiert dann, wenn wir etwas hinzufügen wollen, das bereits beinhaltet ist?


```python
# Ein neues Element hinzufügen
x.add(2)
```


```python
# Check
x
```




    {1, 2}




```python
# Ein bereits enthaltenes Element hinzufügen
x.add(1)
```


```python
# Check
x
```




    {1, 2}



Wir sehen: es wurde keine weitere 1 eingefügt. Das liegt genau daran, dass Sets nur einzigartige Elemente beinhalten. Wir können eine Liste mit verschiedenen sich wiederholenden Elementen an ein Set übergeben und erhalten die einzigartigen Elemente. Zum Beispiel:


```python
# Liste sich wiederholender Elemente erstellen
l = [1,2,1,1,3,5,3,4,6,2]
```


```python
# Die liste an ein Set übergeben
set(l)
```




    {1, 2, 3, 4, 5, 6}



## Booleans

Python verfügt über Booleans. Das sind Wahrheitswerte, die entweder Wahr (`True`) oder Falsch (`False`) annehmen können. Es verfügt außerdem über eine Platzhalter Objekt names `None`. Lasst uns einige kurze Beispiele betrachten (bevor wir in das Thema in einer späteren Lektion vertiefen):


```python
# Ein Objekt zu einem Boolean machen
a = True
```


```python
# Check
a
```




    True



Wir können None als Platzhalter benutzen, wenn wir einem Objekt noch keinen speziellen Wahrheitswert zuordnen wollen:


```python
# None Platzhalter
b = None
```

Das ist es! Du solltest jetzt ein grundsätzliches Verständnis für Objekte und Datenstrukturen in Python haben. Als nächstes kannst du dir die Assessment Aufgabe anschauen!

# Fortgeschrittene Sets

Quelle: Datamics

In dieser Lektion werden wir uns mit verschiedenen Methoden für Sets auseinandersetzen, die ihr bis jetzt noch nicht gesehen haben könntet. Wir wiederholen die bekannten und tauchen dann ein wenig tiefer ein. Los geht's!


```python
s = set()
```

## Hinzufügen

Um Elemente zum Set hinzuzufügen nutzen wir add(). Denkt daran, dass ein Set keine duplizierten Elemente aufnimmt und sie nur einmal darstellt. Deshalb ist es ein Set!


```python
s.add(1)
```


```python
s.add(2)
```


```python
s
```




    {1, 2}



## Zurücksetzen

Clear() entfernt alle Elemente aus dem Set.


```python
s.clear()
```


```python
s
```




    set()



## Kopieren

Die Methode copy() kopiert ein Set. Bedenkt, dass es wirkliche eine Kopie ist, d.h. Veränderungen an einem der Sets lassen das andere unberührt.


```python
s = {1,2,3}
sc = s.copy()
```


```python
sc
```




    {1, 2, 3}




```python
s.add(4)
```


```python
s
```




    {1, 2, 3, 4}




```python
sc
```




    {1, 2, 3}



## Unterschied

Um herauszufinden, was zwei Sets unterscheidet können wir difference() verwenden. Die Schreibweise lautet:

    set1.difference(set2)
    
Zum Beispiel:


```python
s.difference(sc)
```




    {4}



## Unterschied + Update

Die difference_update Schreibweise lautet:

    set1.difference_update(set2)
    
Diese Methode gibt set1 zurück, nachdem die Elemente entfernt wurden, die in Set 2 enthalten sind.


```python
s1 = {1,2,3}
```


```python
s2 = {1,4,5}
```


```python
s1.difference_update(s2)
```


```python
s1
```




    {2, 3}



## Element entfernen

Sofern ein Element Bestandteil eines Sets ist, kann es mit discard() entfernt werden. Andernfalls passiert nichts.


```python
s
```




    {1, 2, 3, 4}




```python
s.discard(4)
```


```python
s
```




    {1, 2, 3}



## Überschneidung

intersection() und intersection_update() geben die Überschneidung von zwei oder mehr Sets als neues Set zurück.


```python
s1 = {1,2,3}
```


```python
s2 = {1,2,4}
```


```python
s1.intersection(s2)
```




    {1, 2}




```python
s1
```




    {1, 2, 3}



intersection_update() wird ein Set mit der Schnittmenge von sich selbst und einem weiteren Set überschreiben.


```python
s1.intersection_update(s2)
```


```python
s1
```




    {1, 2}



## Keine Überschneidung

Um zu überprüfen, ob zwei Sets keine Schnittmenge haben, verwenden wir isdisjoint(). Diese Methode gibt True (wahr) aus, falls keine Schnittmenge vorliegt.


```python
s1 = {1,2}
s2 = {1,2,4}
s3 = {5}
```


```python
s1.isdisjoint(s2)
```




    False




```python
s1.isdisjoint(s3)
```




    True



## Teilmenge / Subset / Superset

Die Methode issubset() ermittelt, ob ein anderes Set ein bestimmtes Set beinhaltet.


```python
s1
```




    {1, 2}




```python
s2
```




    {1, 2, 4}




```python
s1.issubset(s2)
```




    True



Die Methode issuperset() ermittelt, ob ein bestimmtes Set ein anderes Set beinhaltet.


```python
s2.issuperset(s1)
```




    True



 ## Symmetrie
 
 symmetric_difference() und symmetric_update() geben den symmetrischen Unterschied als ein neues Set zurück, d.h. all die Elemente, die (nur) in genau einem der Sets beinhaltet sind.


```python
s1
```




    {1, 2}




```python
s2
```




    {1, 2, 4}




```python
s1.symmetric_difference(s2)
```




    {4}



## Zusammenführung

Die Methode union() falls zwei Sets zusammen, d.h. alle Werte, die in mindestens einem der beiden Sets auftauchen.


```python
s1.union(s2)
```




    {1, 2, 4}



## Update

Um ein Set mit der Zusammenführung aus sich selbst und einem anderen Set zu überschreiben verwenden wir update().


```python
s1.update(s2)
```


```python
s1
```




    {1, 2, 4}



Großartig! Jetzt sollten euch alle Methoden, die euch für Sets zur Verfügung stehen, geläufig sein. Diese Daten Struktur ist extrem nützlich und wird häufig von Anfängern unterschätzt. Behaltet es euch im Kopf!

Gute Arbeit!

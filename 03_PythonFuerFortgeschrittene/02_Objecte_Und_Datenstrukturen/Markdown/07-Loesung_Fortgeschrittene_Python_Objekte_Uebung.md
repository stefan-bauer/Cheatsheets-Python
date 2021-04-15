# Fortgeschrittene Python Objekte Aufgabe

Quelle: Datamics

## Fortgeschrittene Zahlen
<b>Problem 1:</b> Wandle 1024 in binär und hexadezimal Format um.


```python
print(bin(1024))
print(hex(1024))
```

    0b10000000000
    0x400


<b>Problem 2:</b> Rundet 5.23222 auf zwei Dezimalstellen.


```python
round(5.23222,2)
```




    5.23



## Fortgeschrittene Strings
<b>Problem 3:</b> Überprüft, ob jedes Zeichen in diesem String klein geschrieben ist.


```python
s = 'Hallo wie geht es dir Marie, fühlst du dich okay?'

s.islower()
```




    False



<b>Problem 4:</b> Wie häufig taucht der Buchstabe 'w' in folgendem String auf?


```python
s = 'txyxyxytxytxytwhwjwjwjwbwbwgssj'

s.count('w')
```




    7



## Fortgeschrittene Sets
<b>Problem 5:</b> Finde die Elemente in Set 1, die nicht in Set 2 sind.


```python
Set1 = {2,3,1,5,6,8}
Set2 = {3,1,7,5,6,8}

Set1.difference(Set2)
```




    {2}



<b>Problem 6:</b> Finde alle Elemente, die in beiden Sets sind.


```python
Set1.union(Set2)
```




    {1, 2, 3, 5, 6, 7, 8}



## Fortgeschrittene Dictionaries
<b>Problem 7:</b> Erstelle mit Dictionary Verständnis dieses Dictionary: {0:0,1:1,2:8,3:27,4:64}.


```python
{x:x**3 for x in range(5)}
```




    {0: 0, 1: 1, 2: 8, 3: 27, 4: 64}



## Fortgeschrittene Listen
<b>Problem 8:</b> Kehre die Liste um.


```python
l = [1,2,3,4]

l.reverse()

l
```




    [4, 3, 2, 1]



<b>Problem 9:</b> Sortiere die Liste.


```python
l = [3,4,2,5,1]

l.sort()

l
```




    [1, 2, 3, 4, 5]



## Gute Arbeit!

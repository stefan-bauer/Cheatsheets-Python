# NumPy Indexing und Selection

Quelle: Datamics

In dieser Lektion werden wir diskutieren, wie man Elemente oder Gruppen von Elementen aus einem Array auswählt.


```python
import numpy as np
```


```python
# Ein Beispielarray erstellen
arr = np.arange(0,11)
```


```python
# Anzeigen
arr
```




    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10])



## Indexing und Selection mit Klammern

Der einfachste Weg um ein oder mehrere Element(e) aus einem Array auszuwählen sieht dem bei einer Liste sehr ähnlich:


```python
# Wert mit seinem Index erhalten
arr[8]
```




    8




```python
# Erhalte die Werte in einem Bereich
arr[1:5]
```




    array([1, 2, 3, 4])




```python
# Erhalte die Werte in einem Bereich
arr[0:5]
```




    array([0, 1, 2, 3, 4])



## Broadcasting

NumPy Arrays unterscheiden sich von normalen Python Listen durch ihre Fähigkeit des [Broadcasting](https://docs.scipy.org/doc/numpy/user/basics.broadcasting.html).


```python
# Einen Wert durch einen Index-Bereich festlegen (Broadcasting)
arr[0:5]=100

# Anzeigen
arr
```




    array([100, 100, 100, 100, 100,   5,   6,   7,   8,   9,  10])




```python
# Das Array zurücksetzen. Warum das nötig ist sehen wir gleich
arr = np.arange(0,11)

# Anzeigen
arr
```




    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10])




```python
# Ein Stück des Arrays wählen
stueck_des_arr = arr[0:6]

# Anzeigen
stueck_des_arr
```




    array([0, 1, 2, 3, 4, 5])




```python
# Das Stück bearbeiten
stueck_des_arr[:]=99

# Das Stück erneut anzeigen
stueck_des_arr
```




    array([99, 99, 99, 99, 99, 99])



Achtet darauf, wie diese Änderung auch im originalen Array auftaucht!


```python
arr
```




    array([99, 99, 99, 99, 99, 99,  6,  7,  8,  9, 10])



Die Daten wurden hier nicht kopiert. Das erzeugte Teilstück ist eine Betrachtung des originalen Arrays. Das vermeidet Speicherprobleme.


```python
# Um eine Kopie zu erzeugen, müssen wir das explizit anweisen
arr_kopie = arr.copy()

arr_kopie
```




    array([99, 99, 99, 99, 99, 99,  6,  7,  8,  9, 10])



## Indexing in 2D Arrays (Matrizen)

Das allgemeine Format ist arr_2d[row][col] oder arr_2d[row,col]. Ich empfehle normalerweise die Komma-Notation für mehr Klarheit.


```python
arr_2d = np.array(([5,10,15],[20,25,30],[35,40,45]))

# Anzeigen
arr_2d
```




    array([[ 5, 10, 15],
           [20, 25, 30],
           [35, 40, 45]])




```python
# Die Reihe indexieren
arr_2d[1]
```




    array([20, 25, 30])




```python
# Das Format ist arr_2d[row][col] oder arr_2d[row,col]

# Einzelne Elemente auswählen
arr_2d[1][0]
```




    20




```python
# Einzelne Elemente auswählen
arr_2d[1,0]
```




    20




```python
# 2D Array Stücke auswählen

# Form (2,2) von oben rechts
arr_2d[:2,1:]
```




    array([[10, 15],
           [25, 30]])




```python
# Form untere Reihe
arr_2d[2]
```




    array([35, 40, 45])




```python
# Form untere Reihe
arr_2d[2,:]
```




    array([35, 40, 45])



### Raffiniertes Indexing

Raffiniertes Indexing erlaubt es uns ganze Reihen oder Spalten entgegen ihrer Reihenfolge zu wählen. Um das zu verdeutlichen erstellen wir zunächst ein NumPy Array:


```python
# Eine Matrix erstellen
arr2d = np.zeros((10,10))
```


```python
# Länge des Array
arr_laenge = arr2d.shape[1]
```


```python
# Das Array erstellen

for i in range(arr_laenge):
    arr2d[i] = i
    
arr2d
```




    array([[ 0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.],
           [ 1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.],
           [ 2.,  2.,  2.,  2.,  2.,  2.,  2.,  2.,  2.,  2.],
           [ 3.,  3.,  3.,  3.,  3.,  3.,  3.,  3.,  3.,  3.],
           [ 4.,  4.,  4.,  4.,  4.,  4.,  4.,  4.,  4.,  4.],
           [ 5.,  5.,  5.,  5.,  5.,  5.,  5.,  5.,  5.,  5.],
           [ 6.,  6.,  6.,  6.,  6.,  6.,  6.,  6.,  6.,  6.],
           [ 7.,  7.,  7.,  7.,  7.,  7.,  7.,  7.,  7.,  7.],
           [ 8.,  8.,  8.,  8.,  8.,  8.,  8.,  8.,  8.,  8.],
           [ 9.,  9.,  9.,  9.,  9.,  9.,  9.,  9.,  9.,  9.]])



Raffiniertes Indexing erlaubt uns nun folgendes:


```python
arr2d[[2,4,6,8]]
```




    array([[ 2.,  2.,  2.,  2.,  2.,  2.,  2.,  2.,  2.,  2.],
           [ 4.,  4.,  4.,  4.,  4.,  4.,  4.,  4.,  4.,  4.],
           [ 6.,  6.,  6.,  6.,  6.,  6.,  6.,  6.,  6.,  6.],
           [ 8.,  8.,  8.,  8.,  8.,  8.,  8.,  8.,  8.,  8.]])




```python
# Und das in jeder Reihenfolge
arr2d[[6,4,8,2]]
```




    array([[ 6.,  6.,  6.,  6.,  6.,  6.,  6.,  6.,  6.,  6.],
           [ 4.,  4.,  4.,  4.,  4.,  4.,  4.,  4.,  4.,  4.],
           [ 8.,  8.,  8.,  8.,  8.,  8.,  8.,  8.,  8.,  8.],
           [ 2.,  2.,  2.,  2.,  2.,  2.,  2.,  2.,  2.,  2.]])



### Mehr Hilfe beim Indexing

Indexing in einer 2D Matrix kann anfangs etwas verwirrend sein. Bei Google Bilder findet man nützliche Bilder, die einem dabei helfen. Bspw. das folgende:

![title](numpy_indexing.png)

## Selection

Lass uns jetzt noch kurz anschauen, wie wir Klammern nutzen können, um eine Selection basieren auf Vergleichsoperatoren durchzuführen.


```python
arr = np.arange(1,11)
arr
```




    array([ 1,  2,  3,  4,  5,  6,  7,  8,  9, 10])




```python
arr > 4
```




    array([False, False, False, False,  True,  True,  True,  True,  True,  True], dtype=bool)




```python
bool_arr = arr>4
bool_arr
```




    array([False, False, False, False,  True,  True,  True,  True,  True,  True], dtype=bool)




```python
arr[bool_arr]
```




    array([ 5,  6,  7,  8,  9, 10])




```python
arr[arr>2]
```




    array([ 3,  4,  5,  6,  7,  8,  9, 10])




```python
x=2
arr[arr>x]
```




    array([ 3,  4,  5,  6,  7,  8,  9, 10])



# Gut gemacht!

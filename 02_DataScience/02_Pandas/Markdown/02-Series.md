# Series

Quelle: Datamics

Der erste Hauptdatentyp den wir uns für Pandas anschauen ist der der *Series*. Lass uns Pandas importieren und einige Series Objekte untersuchen.

Eine Series (dt. Serie) ist sehr ähnlich zu einem NumPy Array. Tatsächlich ist es auf dem NumPy Array Objekt aufgebaut. Was das NumPy Array letztlich von einer Series unterscheidet ist, dass Series Achsenbeschriftungen haben kann. Das bedeutet wir können nicht nur über numerische Indizes, sondern auch über das Label indexieren. Außerdem muss eine Series nicht unbedingt numerische Werte beinhalten.

Schauen wir uns das Konzept an einigen Beispielen an:


```python
import numpy as np
import pandas as pd
```

## Eine Series erstellen

Wir können Listen, NumPy Arrays oder Dictionaries in eine Series konvertieren:


```python
labels = ["a","b","c"]
meine_liste = [10,20,30]
arr = np.array([10,20,30])
d = {"a":10,"b":20,"c":30}
```

### Listen nutzen


```python
pd.Series(data=meine_liste)
```




    0    10
    1    20
    2    30
    dtype: int64




```python
pd.Series(data=meine_liste,index=labels)
```




    a    10
    b    20
    c    30
    dtype: int64




```python
pd.Series(meine_liste,labels)
```




    a    10
    b    20
    c    30
    dtype: int64



### NumPy Arrays


```python
pd.Series(arr)
```




    0    10
    1    20
    2    30
    dtype: int64




```python
pd.Series(arr,labels)
```




    a    10
    b    20
    c    30
    dtype: int64



### Dictionaries


```python
pd.Series(d)
```




    a    10
    b    20
    c    30
    dtype: int64



## Daten in einer Series

Eine Pandas Series kann eine Vielzahl an Objekttypen beinhalten:


```python
pd.Series(data=labels)
```




    0    a
    1    b
    2    c
    dtype: object




```python
# Sogar Funktionen (auch wenn dieser Anwendungsfall unwahrscheinlich ist)
pd.Series([sum,print,len])
```




    0      <built-in function sum>
    1    <built-in function print>
    2      <built-in function len>
    dtype: object



## Einen Index nutzen

Der Schlüssel zur Nutzung von Series ist das Verständnis für deren Index. Pandas nutzt diese Indexnamen oder -nummern, um schnelle Suchen durchzuführen. Dies funktioniert ähnlich einer Hash-Tabelle oder einem Dictionary.

Schauen wir uns einige Beispiele an, wie man Informationen aus einer Series zieht. Dazu erstellen wir zwei Series ser1 und ser2:


```python
ser1 = pd.Series([1,2,3,4],index=["USA","Deutschland","Russland","Japan"])
```


```python
ser1
```




    USA            1
    Deutschland    2
    Russland       3
    Japan          4
    dtype: int64




```python
ser2 = pd.Series([1,2,5,4],index=["USA","Deutschland","Italien","Japan"])
```


```python
ser2
```




    USA            1
    Deutschland    2
    Italien        5
    Japan          4
    dtype: int64




```python
ser1["USA"]
```




    1



Operationen werden basierend auf dem Index durchgeführt:


```python
ser1 + ser2
```




    Deutschland    4.0
    Italien        NaN
    Japan          8.0
    Russland       NaN
    USA            2.0
    dtype: float64



Soweit so gut. Lasst uns als nächstes mit den Data Frames fortfahren. Diese erweitern das Konzept der Series.

# Gut gemacht!

# Fortgeschrittene Dictionaries

Quelle: Datamics

Anders als manche der anderen Daten Strukturen mit denen wir gearbeitet haben, haben wir für Dictionaries die meisten der wirklich nützlichen Methoden während unseres Kurses bereits kennengelernt. Für die Vollständigkeit hier noch einige weitere:


```python
d = {'k1':1,'k2':2}
```

## Dictionary Abstraktion

Genau wie beim Listen Abstraktion haben auch Dictionaries ihre eigene Version von Abstraktion (comprehension), um sie schnell erstellen zu können. Es wird nicht so häufig verwendet, dennoch wollen wir ein Beispiel betrachten:


```python
{x:x**2 for x in range(10)}
```




    {0: 0, 1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64, 9: 81}



Einer der Gründe dafür, dass es nicht so häufig verwendet wird ist, dass es schwer ist, Key Namen zu strukturieren, sofern sie nicht auf den Werten basieren.

## Iteration

Wir können über Dictionaries iterieren, indem wir die iter() Methode verwenden. Iterationen sind über Keys, Values und Items möglich. Zum Beispiel:


```python
for k in iter(d.keys()):
    print(k)
```

    k1
    k2



```python
for v in iter(d.values()):
    print(v)
```

    1
    2



```python
for item in iter(d.items()):
    print(item)
```

    ('k1', 1)
    ('k2', 2)


## Anzeigen

Wir können durch items(), keys() und values() anzeigen lassen, was sich im Dictionary befindet.


```python
d.items()
```




    dict_items([('k1', 1), ('k2', 2)])




```python
d.keys()
```




    dict_keys(['k1', 'k2'])




```python
d.values()
```




    dict_values([1, 2])



Toll! Jetzt solltet ihr selbstbewusst im Umgang mit der Vielzahl an Methoden sein, die euch für Dicitonaries zur Verfügung stehen.

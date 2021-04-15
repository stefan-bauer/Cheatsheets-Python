# Dictionaries
Quelle:Datamics

Wir haben bereits über Sequenzen in Python gesprochen. Jetzt werden wir einen Gang hochschalten und mehr über *Mappings* in Python lernen. Sofern ihr andere Sprachen kennt, könnt ihr dies ungefähr mit *Hash* Tabellen oder einer *Map* vergleichen.

Diese Lektion über Dictionaries beinhaltet:

1. Erstellen eines Dictionary
2. Zugriff auf Objekte eines Dictionary
3. Veschachtelte Dictonaries
4. Grundlegende Dictionary Methoden

Was sind also diese <i>Mappings</i>? 

Mappings sind eine Sammlung von Objekten die über einen <i>Key</i> (dt.: Schlüssel) gespeichert werden. Das ist anders als bei Sequenzen, in denen Objekte über ihre relative Position gespeichert werden. Das ist eine wichtige Unterscheidung, da Mappings die Reihenfolge nicht berücksichtigen, da Objekte über einen Key definiert sind.

Ein Python Dictonary besteht aus einem Key und einem zugehörigen Wert. Sie beinhalten also Key-Value (dt.: Schlüssel-Wert) Paare. Deren Werte können nahezu jedes Python Objekt sein.

Dicitonaries gehören zu den wichtigsten Datentypen in Python; kaum ein Programm kommt ohne sie aus. Sie teilen folgende Eigenschaften mit Listen:
* Dictionaries können leicht verändert werden
* Dictionaries können beliebig wachsen und schrumpfen

## Erstellen eines Dictionary

Lasst uns betrachten, wie wir Dictionaries erstellen, um ein besseres Verständnis für sie zu erhalten!


```python
# Erstellen eines Dictionary mit {} and : um Key und Wert zu trennen
mein_dict = {'Key1':'Wert1','Key2':'Wert2'}
```


```python
# Werte über ihren Key aufrufen
mein_dict['Key2']
```




    'Wert2'



Es ist wichtig festzuhalten, dass Dictionaries sehr flexibel sind in Hinsicht auf die Daten Arten, die sie beinhalten könne. Zum Beispiel:


```python
mein_dict = {'Key1':123,'Key2':[12,23,34],'Key3':['Item1','Item2','Item3']}
```


```python
# Jetzt können wir Items aus dem Dictionary aufrufen
mein_dict['Key3']
```




    ['Item1', 'Item2', 'Item3']




```python
# Wir können auch einen Index dieses Wertes aufrufen
mein_dict['Key3'][0]
```




    'Item1'




```python
# Und dann können wir noch Methoden auf den Index anwenden
mein_dict['Key3'][0].upper()
```




    'ITEM1'



Wir können die Werte beeinflussen. Wie hier:


```python
mein_dict['Key1']
```




    123




```python
# Wir ziehen 123 vom Wert ab
mein_dict['Key1'] = mein_dict['Key1'] - 123
```


```python
# Check
mein_dict['Key1']
```




    0



Ein kleiner Hinweis: Python hat eine eingebaute Methode um Selbstaddition (oder -subtraktion, -multiplikation, -division) durchzuführen. Wir hätten für das obenstehende Statement auch += oder -= verwenden können.


```python
# Das Objekt sich selbst minus 123 gleichsetzen
mein_dict['Key1'] -= 123
mein_dict['Key1']
```




    -123



Wir können Keys auch per Zuweisung erstellen. Wenn wir beispielsweise mit einem leeren Dictionary beginnen, können wir dieses kontinuierlich erweitern.


```python
# Ein neues Dictionary erstellen
d = {}
```


```python
# Eine neuen Key durch Zuweisung erstellen
d['Tier'] = 'Hund'
```


```python
# Das geht übrigens mit allen Objekten
d['Antwort'] = 42
```


```python
# Check
d
```




    {'Tier': 'Hund', 'Antwort': 42}



## Verschachteln von Dictionaries

Hoffentlich erkennt ihr, wie mächtig Python durch seine flexiblen Verwendungsmöglichkeiten von Verschachtelungen bzw. Einbettungen und Methoden ist. Hier folgt ein Dictionary innerhalb eines Dictionary:


```python
# Dictionary innerhalb eines Dictionary innerhalb eines Dictionary
d = {'Key':{'SubKey':{'SubSubKey':'Wert'}}}
```

Wow! Das ist wie bei Inception. Lasst uns überprüfen, wie wir auf diese Werte zugreifen können.


```python
# Die Keys nacheinander aufrufen
d['Key']['SubKey']['SubSubKey']
```




    'Wert'



## Einige Dictionary Methoden

Es gibt einige Methoden, die wir auf das Dictionary anwenden können. Lasst uns eine schnelle Einführung durchgehen:


```python
# Ein typisches Dictionary erstellen
d = {'Key1':1,'Key2':2,'Key3':3}
```


```python
# Methode, die alle Keys eines Dictionary ausgibt
d.keys()
```




    dict_keys(['Key1', 'Key2', 'Key3'])




```python
# Methode, die alle Werte ausgibt
d.values()
```




    dict_values([1, 2, 3])




```python
# Methode, die Tupel aller Items wiedergibt
d.items()
```




    dict_items([('Key1', 1), ('Key2', 2), ('Key3', 3)])



Hoffentlich habt ihr jetzt ein gutes Grundverständnis darüber, wie Dictionaries erstellt werden. Es gibt darüber noch viel mehr zu lernen, worauf wir zu einem späteren Zeitpunkt zurückkommen werden. Was nach dieser Lektion wichtig zu wissen ist, ist wie Dictionaries erstellt werden und wie auf ihre Werte zugegriffen werden kann.

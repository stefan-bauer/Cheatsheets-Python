# Tupel
Quelle: Datamics
In Python sind Tupel sehr ähnlich zu Listen. Im Gegensatz zu Listen sind sie aber nicht änderbar. Das bedeutet, dass weder Werte hinzugefügt, noch gelöscht werden können. Deshalb verwendet man Tupel immer dann, wenn etwas nicht geändert werden soll. Beispiele sind Wochentage oder das Datum eines Kalenders.

Die Vorteile von Tupeln gegenüber Listen zusammengefasst:
*  Tupel sind performanter als Listen.
* Wenn bekannt ist, dass Daten nicht geändert werden müssen, sollten Tupel verwendet werden, um ungewollte Änderungen zu vermeiden.
* Tupel können als Schlüssel in Dictionaries verwendet werden können, da Schlüssel nur Objekte von unveränderlichen Datentypen sein können. Listen können also nicht verwendet werden. 

In dieser Lektion werden wir einen Überblick über folgendes erhalten:

1. Tupel erstellen
2. Grundlegende Tupel Methoden
3. Unveränderlichkeit
4. Wann man Tupel verwendet

Für die Verwendung von Tupeln haben wir schon ein Gefühl, da wir Listen kennen. Sie werden sehr ähnlich behandelt abgesehen von ihrer Unveränderlichkeit.

## Tupel erstellen

Zur Erstellung von Tupeln werden () verwendet und Elemente durch Komma getrennt. Wie zum Beispiel hier:


```python
# Ein Tupel erstellen
t = (1,2,3)
```


```python
# Die Länge wird wie bei Listen gemessen
len(t)
```




    3




```python
# Außerdem können die Arten von Objekten gemixt werden
t = ('Eins',2)

# Check
t
```




    ('Eins', 2)




```python
# Auch Indexierung funktioniert wie bei Listen
t[0]
```




    'Eins'




```python
# Und auch die Teilung funktioniert gleich
t[-1]
```




    2



## Grundlegende Tupel Methoden

Tupel haben vordefinierte Methoden, allerdings weniger als Listen. Hier sind zwei davon:


```python
# Nutzt .index(), um einen Wert einzugeben und dessen Index zu erhalten
t.index('Eins')
```




    0




```python
# Nutzt .count(), um die Anzahl des Vorkommens eines Wertes zu ermitteln
t.count(2)
```




    1



## Unveränderlichkeit

Es kann nicht oft genug betont werden, das Tupel unveränderlich sind. Um das ein für alle mal klar zu stellen:


```python
t[0] = 'Neuer Wert'
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-8-037f89273267> in <module>()
    ----> 1 t[0] = 'Neuer Wert'
    

    TypeError: 'tuple' object does not support item assignment



```python
t.append('Anhang')
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    <ipython-input-9-72af8ab9d520> in <module>()
    ----> 1 t.append('Anhang')
    

    AttributeError: 'tuple' object has no attribute 'append'


## Wann werden Tupel verwendet?

Falls ihr euch fragt: "Warum überhaupt mit Tupeln auseinandersetzen, wenn sie weniger Methoden zur Verfügung stellen?" Und um ehrlich zu sein: Tupel werden weniger häufig verwendet als Listen. Aber immer dann, wenn Unveränderlichkeit notwendig ist, können sie punkten. Wenn in einem eurer Programme ein Objekt verarbeitet werden soll, dass nicht geändert werden darf, dann sind Tupel die richtige Lösung. Es bietet eine gute Quelle für Datenintegrität.

Ihr solltet nun also in der Lage sein Tupel zu erstellen und zu nutzen, sowie das Konzept der Unveränderlichkeit verstanden haben.

Als nächstes: Dateien!

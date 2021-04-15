# Objektorientierte Programmierung Übung - Aufgabe

Quelle:Datamics

## Aufgabe 1

Fülle die `Linien` Klasse Methoden aus, um Koordinaten als Paar von Tupeln zu akzeptieren und Steigung sowie Distanz zu berechnen.


```python
class Linie(object):
    
    def __init__(self,koor1,koor2):
        pass
    
    def distanz(self):
        pass
    
    def steigung(self):
        pass
```


```python
# Beispielhaftes Ergebnis

koordinate1 = (3,2)
koordinate2 = (8,10)

li = Linie(koordinate1,koordinate2)
```


```python
li.distanz()
```


```python
li.steigung()
```

## Aufgabe 2

Fülle die Klasse aus.


```python
class Zylinder(object):
    def __init__(self,hoehe=1,radius=1):
        pass
    
    def volumen(self):
        pass
    
    def oberflaeche(self):
        pass
```


```python
# Beispielhaftes Ergebnis
c = Zylinder(2,3)
```


```python
c.volumen()
```


```python
c.oberflaeche()
```

# Objektorientierte Programmierung Übung - Lösung

Quelle:Datamics

## Aufgabe 1

Fülle die `Linien` Klasse Methoden aus, um Koordinaten als Paar von Tupeln zu akzeptieren und Steigung sowie Distanz zu berechnen.


```python
class Linie(object):
    
    def __init__(self,koor1,koor2):
        self.koor1 = koor1
        self.koor2 = koor2
    
    def distanz(self):
        x1,y1 = self.koor1
        x2,y2 = self.koor2
        return ( (x2-x1)**2 + (y2-y1)**2)**0.5
    
    def steigung(self):
        x1,y1 = self.koor1
        x2,y2 = self.koor2
        return (y2-y1)/(x2-x1)
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




    9.433981132056603




```python
li.steigung()
```




    1.6



## Aufgabe 2

Fülle die Klasse aus.


```python
class Zylinder(object):
    def __init__(self,hoehe=1,radius=1):
        self.hoehe = hoehe
        self.radius = radius
    
    def volumen(self):
        return self.hoehe * (3.14) * (self.radius)**2
    
    def oberflaeche(self):
        top = (3.14)*(self.radius)**2
        return 2*top + 2*3.14*self.radius*self.hoehe
```


```python
# Beispielhaftes Ergebnis
c = Zylinder(2,3)
```


```python
c.volumen()
```




    56.52




```python
c.oberflaeche()
```




    94.2



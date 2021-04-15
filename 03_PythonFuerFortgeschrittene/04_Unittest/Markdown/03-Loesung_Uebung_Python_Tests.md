# Übungsaufgabe für Python Tests - Lösung

Quelle: Datamics

In dieser Übung werden wir uns das für Vorstellungsgesprächen bekannte Uhr-Winkel Problemstellung anschauen um Tests in Python zu erstellen. Zum Bespiel kann bei Unternehmen wie Google die folgende Frage gestellt werden: "Was ist der Winkel zwischen dem Stundenzeiger und dem Minutenzeiger um 2:20 Uhr?". Wir werden diese Fragestellung jetzt mit einer Pythonfunktion beantworten.

Das folgende Bild veranschaulicht die Winkel auf einer Analogen Uhr um 2:20 Uhr:

![Uhr](ClockAngles.jpg) 

*Hinweis:*

Der Stundenzeiger bewegt sich in 12 Stunden um 360 Grad. Das beudet 0,5 Grad in einer Minute. Der Minutenzeiger bewegt sich in 60 Minuten um 360 Grad. Das bedeutet 6 Grad in einer Minute. Nach H Stunden und M minuten ergeben sich die folgenden Formeln:

Winkel des Stundenzeiger = 0,5 x (60 x H + M)

und 

Winkel des Minutenzeigers = 6 x M







Vervollständige die *uhrwinkel(stunde, minute)* Funktion:


```python
def uhrwinkel(stunde, minute):
    winkel = abs((stunde * 30 + minute * 0.5) - (minute * 6))
    return min(360-winkel, winkel)
```


```python
uhrwinkel(2, 20)
```




    50.0




```python
uhrwinkel(9, 10)
```




    145.0




```python
uhrwinkel(12, 0)
```




    0.0



# Docmodul Test

Erstellen einen Docmodul für die *uhrwinkel(stunde, minute)* Funktion mit den gezeigten Tests:


```python
def uhrwinkel(stunde, minute):
    # erstelle die Winkelberechnug und die passenden Tests mit dem docstring
    """ 
    Testet ob eine Zahl eine Primzahl ist. 
    
    >>> uhrwinkel(2,20)
    50.0
    >>> uhrwinkel(9,10)
    145.0
    >>> uhrwinkel(12,0) 
    0.0
    >>> 
    
    """
    winkel = abs((stunde * 30 + minute * 0.5) - (minute * 6))
    return min(360-winkel, winkel)

def _test():
    # importiere doctest und rufe die Funktion testmod() auf
    import doctest
    doctest.testmod()

if __name__ == "__main__":
    _test()
```

# unittest

Erstelle als nächstes einen unittest für die *uhrwinkel(stunde, minute)* Funktion mit den gezeigten Tests:

Hinweis: Das Modul "unittest" kann auch ohne den import einer Pythondatei uhrwinkel.py die zuvor erstelle uhrwinkel Funktion aufrufen.

Importiere zunächst das Benötigte Modul:


```python
import unittest
```


```python
# leite die Klasse UhrwinkelTest von der Klasse unittest.TestCase ab
class UhrwinkelTest(unittest.TestCase):
    # erstelle eine test Methode mit einem assert
    
    def testUhrwinkel(self):
        self.assertEqual(uhrwinkel(2,20), 50.0)
        self.assertEqual(uhrwinkel(9,10), 145.0)
        self.assertEqual(uhrwinkel(12,0), 0.0)
    
if __name__ == "__main__": 
    unittest.main(argv=['first-arg-is-ignored'], exit=False)
    # unittest.main()  Methode für Unit-Testing mit dem Terminal, nicht IPython notebooks
```

    .
    ----------------------------------------------------------------------
    Ran 1 test in 0.002s
    
    OK


Erweitere als nächstes den Test mit einer *setUp()* Funktion, die die Testparamter in Form von Tupeln lädt und danach mit der assertEqual() Methode diese Werte iterativ testet.



```python
class UhrwinkelTest(unittest.TestCase):
    def setUp(self):
        self.elements = ( ((2, 20), 50.0 ), ((9, 10), 145.0 ), ((12, 0), 0.0 ))
        print ("setUp aufgerufen!")
        
    def testUhrwinkel(self):
        for ((h,m), ergebnis) in self.elements:
            self.assertEqual(uhrwinkel(h, m), ergebnis)
        print ("test aufgerufen!")
    
if __name__ == "__main__": 
    unittest.main(argv=['first-arg-is-ignored'], exit=False)
    # unittest.main()  Methode für unit testing mit dem Terminal, nicht IPython notebooks
```

    .

    setUp aufgerufen!
    test aufgerufen!


    
    ----------------------------------------------------------------------
    Ran 1 test in 0.002s
    
    OK


# Gut gemacht!

Glückwunsch zur Erstellung deiner ersten Python Tests!

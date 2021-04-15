# Übungsaufgaben für Python Tests

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
    pass
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
    pass

def _test():
    # importiere doctest und rufe die Funktion testmod() auf
    pass

if __name__ == "__main__":
    _test()
```

# unittest

Erstelle als nächstes einen unittest für die *uhrwinkel(stunde, minute)* Funktion mit den gezeigten Tests:

Hinweis: Das Modul "unittest" kann auch ohne den import einer Pythondatei uhrwinkel.py die zuvor erstelle uhrwinkel Funktion aufrufen.

Importiere zunächst das Benötigte Modul:


```python

```


```python
# leite die Klasse UhrwinkelTest von der Klasse unittest.TestCase ab
class UhrwinkelTest(              ):
    # erstelle eine test Methode mit einem assert


    
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
class UhrwinkelTest(              ):
    def setUp(self):

        
    def testUhrwinkel(self):

    
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

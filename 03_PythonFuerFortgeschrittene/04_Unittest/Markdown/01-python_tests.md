# Python Tests

Quelle: Datamics

In der Programmierung gibt es unterschiedliche Fehlerarten wie Syntaxfehler, Ausnahmen und semantische Fehler. Diese schauen wir uns zunächst an bevor wir mit dem schreiben von Tests beginnen.

### Syntaxfehler (engl.: syntax errors)

Während der Programmentwicklung gibt es immer wieder "kleine Fehler", häufig sind es Tippfehler. Irgendwo fehlt immer mal ein Doppelpunkt, so zum Beispiel hinter einem "if", oder man hat vielleicht "true" statt "True" geschrieben. Dabei handelt es sich um die Verletzung von Schreibweisen von einzelnen Wörtern, also zum Beispiel Schlüsselwörtern oder von Strukturregeln. Diese Fehler sind relativ leicht zu finden da sie schon bei dem Kompilieren angezeigt werden.


```python
if true
    print ("Dies ist ein Syntaxfehler!")
```


      File "<ipython-input-2-ffc1392b3d49>", line 1
        if true
               ^
    SyntaxError: invalid syntax



### Ausnahmen (engl: exceptions)

Selbst wenn eine Anweisung oder ein Ausdruck syntaktisch korrekt ist, kann es bei der Ausführung zu Fehlern kommen. Fehler, die bei der Ausführung auftreten, werden Ausnahmen (engl: exceptions) genannt und sind nicht notwendigerweise schwerwiegend. Wir haben diese schon in dem Kapitel Fehlerbehandlung mit try catch behandelt.


```python
4 + spam*3
```


    

    NameErrorTraceback (most recent call last)

    <ipython-input-1-6b1dfe582d2e> in <module>()
    ----> 1 4 + spam*3
    

    NameError: name 'spam' is not defined


### Semantische Fehler

Neben den syntaktischen Fehlern und Ausnahmen, die sich häufig relativ leicht finden und beheben lassen, gibt es auch die semantischen Fehler. Diese sind relativ schwer zu finden da sie erst später im Ergebniss des Programmcodes auftreten oder auch nur selten wenn bestimmte Situationen eintreten. Ein Beispiel ist dass man bei der Berechnung von Prozent vergisst mit 100 zu multiplizieren.


```python
def prozent(wert, total):
    return wert / total  # anstatt "wert * 100 / total"
```

# Unit Tests

Die Semantischen Fehler kann mit Unit tests abfangen. Dies ist vorallem Sinnvoll wenn mehrere Personen am gleichen Code arbeiten. Für Unit tests definieren wir uns zunächst eine Funktion die überprüft ob eine Zahl eine Primzahl ist.


```python
def ist_primzahl(n):
    """ 
    Testet ob eine Zahl eine Primzahl ist. 
    """
    for i in range(3, n):
        if n % i == 0:
            return False
    return True
```

Danach testen wir die Primzahl-Funktion mit Zahlen und überprüfen das Ergebnis:


```python
ist_primzahl(6)
```




    False




```python
ist_primzahl(2)
```




    True




```python
ist_primzahl(-6)
```




    True




```python
ist_primzahl(0.5)
```


    

    TypeErrorTraceback (most recent call last)

    <ipython-input-65-8ec51201ad10> in <module>()
    ----> 1 ist_primzahl(0.5)
    

    <ipython-input-62-344910f772fd> in ist_primzahl(n)
          3     Testet ob eine Zahl eine Primzahl ist.
          4     """
    ----> 5     for i in range(3, n):
          6         if n % i == 0:
          7             return False


    TypeError: range() integer end argument expected, got float.


Wir sehen, dass die Funktionen auf Integer-Zahlen definiert sind. Für negative ganze Zahlen liefert die Funktion immer True zurück. Ruft man die Funktionen mit Float-Zahlen auf, gibt es einen TypeError, weil range nicht für Float-Werte definiert ist.
Wir können nun unser Modul testen, ob die Aufrufe der Methode ist_primzahl für bestimmte Werte auch die vordefinierten Ergebniswerte zurückliefern.
Man könnte also unser Modul direkt um eine oder mehrere if-Anweisungen erweitern: 


```python
if ist_primzahl(3) == True and ist_primzahl(6) == False and ist_primzahl(10) == False:
    print("Test für Primzahl-Funktion erfolgreich")
else:
    print("Primzahl-Funktion liefert fehlerhafte Werte")
```

    Test für Primzahl-Funktion erfolgreich


Nun wollen wir bewusst einen Fehler in unsere Primzahl-Funktion einbauen. Dazu ändern wir die range von 10 bis n: 


```python
def ist_primzahl(n):
    """ 
    Testet ob eine Zahl eine Primzahl ist. 
    """
    for i in range(10, n):
        if n % i == 0:
            return False
    return True

```

Danach testen wir nochmal unsere Primzahl-Funktion: 


```python
if ist_primzahl(2) == True and ist_primzahl(6) == False and ist_primzahl(1) == True:
    print("Test für Primzahl-Funktion erfolgreich")
else:
    print("Primzahl-Funktion liefert fehlerhafte Werte")
```

    Primzahl-Funktion liefert fehlerhafte Werte


# Modul Test

Jedes Python-Modul hat einen definierten Namen im built-in-Attribut __name__. Nehmen wir an, wir haben ein Modul mit dem Namen "primzahl" unter "primzahl.py" gespeichert. Wird dieses Modul mit "import primzahl" importiert, dann hat das built-in-Attribut __name__ den Wert "primzahl". Wird die Datei primzahl.py als eigenständiges Programm aufgerufen, also mittels 'python primzahl.py' dann hat diese Variable den Wert '__main__'. 

Wird unser Modul direkt gestartet, also nicht importiert, hat __name__ den Wert "__main__".
Wir können unser Modul nun so umschreiben, dass die Tests nur gestartet werden, wenn das Modul direkt gestartet wird: 


```python
# Modul primzahl.py 

def ist_primzahl(n):
    """ 
    Testet ob eine Zahl eine Primzahl ist. 
    """
    for i in range(3, n):
        if n % i == 0:
            return False
    return True

if __name__ == "__main__":
    if ist_primzahl(2) == True and ist_primzahl(6) == False and ist_primzahl(1) == True:
        print("Test für Primzahl-Funktion erfolgreich")
    else:
        print("Primzahl-Funktion liefert fehlerhafte Werte")
```

    Test für Primzahl-Funktion erfolgreich


# doctest-Modul

Das doctest-Modul stellt eine weitere einfache Methode dar um Modultests durchzuführen. Wie auch der Name schon vermuten lässt, befindet sich der eigentliche Test bei dieser Methode im Docstring.

*Vorgehensweise:*

Zuerst muss man das Modul "doctest" importieren. Dann kopiert man einen Auszug aus einer interaktiven Sitzung in den Docstring einer Funktion.

Diese Aufrufe mit den Ergebnissen kopieren wir aus der interaktiven Shell in den Docstring unserer Funktion. Damit das Modul doctest aktiv wird, müssen wir die Methode testmod() starten, falls das Modul direkt aufgerufen wird. Diesen Aufruf können wir wie üblich mit einem Test des Attributs __name__ auf den Wert "__main__" machen. Das vollständige Modul sieht nun wie folgt aus:
    


```python

def ist_primzahl(n):
    """ 
    Testet ob eine Zahl eine Primzahl ist. 
    
    >>> ist_primzahl(0)
    True
    >>> ist_primzahl(1)
    True
    >>> ist_primzahl(10) 
    False
    >>> ist_primzahl(15)
    False
    >>> 
    
    """
    for i in range(3, n):
        if n % i == 1:
            return False
    return True

def _test():
    import doctest
    doctest.testmod()

if __name__ == "__main__":
    _test()
```

Nun wollen wir wieder bewusst einen Fehler in unsere Primzahl-Funktion einbauen. Dazu ändern wir wieder die range von 10 bis n: 


```python
def ist_primzahl(n):
    """ 
    Testet ob eine Zahl eine Primzahl ist. 
    
    >>> ist_primzahl(0)
    True
    >>> ist_primzahl(1)
    True
    >>> ist_primzahl(10) 
    False
    >>> ist_primzahl(15)
    False
    >>> 
    
    """
    for i in range(10, n):
        if n % i == 1:
            return False
    return True

def _test():
    import doctest
    doctest.testmod()

if __name__ == "__main__":
    _test()
```

    **********************************************************************
    File "__main__", line 9, in __main__.ist_primzahl
    Failed example:
        ist_primzahl(10) 
    Expected:
        False
    Got:
        True
    **********************************************************************
    1 items had failures:
       1 of   4 in __main__.ist_primzahl
    ***Test Failed*** 1 failures.


# unittest


Im Vergleich zum Modul "doctest" werden bei dem Modul "unittest"die Testfälle außerhalb des eigentlichen Programmcodes definiert. Zum Beispiel könnne die Tests in einer eigenen Datei definiert werden und so die Programmdokumentation und die Testbeschreibung voneinander trennen. Das beudeutet allerdings auch einen größeren Aufwand für die Erstellung der Tests. Das Modul "unittest" ist dabei von JUnit (Testen von Java-Programmen) von Erich Gamma und SUnit (Smalltalk-Testframework) von Kent Beck abgeleitet.



Wir werden nun für unser Modul primzahl.py einen Test mit unittest erstellen. In einer Datei primzahl_unittest.py müssen wir das Modul unittest und das zu testende Modul ("primzahl") importieren.

Außerdem müssen wir eine Klasse "PrimzahlTest" (oder ein anderer belibiger Name) erstellen, die von unittest.TestCase erbt. In dieser Klasse werden die nötigen Testfälle in Methoden definiert. Der Name dieser Methoden ist beliebig, er muss jedoch mit test beginnen. In unserer Methode "testCalculation" benutzen wir die Methode assertEqual der Klasse TestCase. 

 - **assertEqual(first, second, msg = None)** prüft, ob der Ausdruck "first" gleich dem Ausdruck "second" ist. Falls die beiden Ausdrücke ungleich sind, wird msg ausgegeben. 
 - **assertTrue(first, msg = None)** prüft, ob der Ausdruck "first" gleich dem Ausdruck "True" ist. Falls first nicht True ist, wird msg ausgegeben. 
 
Für das testen in Jupyter Notebook müssen wir die unittest.main erweitern da diese standardmässig nach dem Argument sys.argv sucht. Da dieses allerdings von IPthon gestartet wurde, muss man dieses Argument explizit weiterreichen um einen Fehler im Jupyter Notebook zu vermeiden. Außerdem müssen wir im Notebook noch den Parameter 'exit=False' mitübergeben um zu verhindern dass sich der Kernel beendet.


```python
import unittest
from primzahl import ist_primzahl

class PrimzahlTest(unittest.TestCase):
    
    def testPrimzahl(self):
        self.assertEqual(ist_primzahl(0), True)
        self.assertEqual(ist_primzahl(1), True)
        self.assertEqual(ist_primzahl(10), False)
        self.assertEqual(ist_primzahl(15), False)
    
    # Alternativer Test mit assertTrue
    def testAssertTrue(self):
        self.assertTrue(ist_primzahl(1))

if __name__ == "__main__": 
    unittest.main(argv=['first-arg-is-ignored'], exit=False)
    # unittest.main()  Methode für unit testing mit dem Terminal, nicht IPython notebooks
```

    ..
    ----------------------------------------------------------------------
    Ran 2 tests in 0.004s
    
    OK


Hier ist eine Liste mit weiteren häufigen assert Methoden:

|Method | Checks that |
|------|------| 
 | assertEqual(a, b) | a == b |   
 | assertNotEqual(a, b) | a != b |   
 | assertTrue(x) | bool(x) is True |   
 | assertFalse(x) | bool(x) is False |   
 | assertIs(a, b) | a is b |  
 | assertIsNot(a, b) | a is not b |  
 | assertIsNone(x) | x is None |  
 | assertIsNotNone(x) | x is not None |  
 | assertIn(a, b) | a in b |  
 | assertNotIn(a, b) | a not in b |  
 | assertIsInstance(a, b) | isinstance(a, b) |  
 | assertNotIsInstance(a, b) | not isinstance(a, b) | 

Als nächstes erweitern wir unsere Test mit der setUp und der tearDown Methode


```python
import unittest
from primzahl import ist_primzahl

class PrimzahlTest(unittest.TestCase):
    
    def setUp(self):
        self.elements = ( (0, True), (1, True), (10, False), (15, False) )
        print ("setUp aufgerufen!")
        
    def testPrimzahl(self):
        for (i, ergebnis) in self.elements:
            self.assertEqual(ist_primzahl(i), ergebnis)
        print ("test aufgerufen!")
        
    def tearDown(self):
        # Objekte können gelöscht oder geändert werden
        # in diesem Fall macht es jedoch wenig Sinn:
        self.elements = None
        print ("tearDown aufgerufen!")

if __name__ == "__main__": 
    unittest.main(argv=['first-arg-is-ignored'], exit=False)
    # unittest.main()  Methode für unit testing mit dem Terminal, nicht IPython notebooks
```

    .

    setUp aufgerufen!
    test aufgerufen!
    tearDown aufgerufen!


    
    ----------------------------------------------------------------------
    Ran 1 test in 0.002s
    
    OK


# Gut gemacht!

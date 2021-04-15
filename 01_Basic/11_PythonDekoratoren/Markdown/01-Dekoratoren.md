# Dekoratoren

Quelle: Datamics

Dekoratoren (en.: Decorators) gehören zu den leistungsstärksten Design-Möglichkeiten für Python-Programme und Skripts. 

Dabei unterscheidet man in Python zwei Arten von Dekoratoren:
1. Funktions-Dekoratoren
2. Klassen-Dekoratoren

Dekoratoren können als Python Objekte verstanden werden, die die Funktionalität anderer Funktionen verändern. Es wird dabei eine Funktion oder Klasse an den Dekorator übergeben, welcher eine Modifizierte Version davon zurückspielt. So helfen sie dabei, den Code zu verkürzen. 

Es ist an dieser Stelle angebracht eine kleine Unterscheidung vorzunehmen: Die Verwendung von Dekoratoren ist sehr einfach. Ihre Erstellung hingegen kann zunächst kompliziert erscheinen.

Es kommt beim ersten Kontakt mit Dekoratoren in Python häufiger zu Problemen, weshalb wir uns für eine kleine Wiederholung entschieden haben. Um Dekoratoren ausreichend zu erklären, werden wir langsam auf Funktionen aufbauen.

*Versichert euch dabei, Python und die Notebooks neu zu starten, damit sie genau so aussehen.*

Hier unsere ersten Schritte:

## Funktionen Wiederholung


```python
def funk():
    return 1
```


```python
funk()
```




    1



## Geltungsbereich Wiederholung

Erinnert euch an die Lektion zu verschachtelte Anweisungen und daran, dass Python den Geltungsbereich nutzt, um zu wissen, worauf sich ein Name bezieht. Zum Beispiel:


```python
s = "Globale Variable"

def funk():
    print(locals())
```

Beachtet, dass Python Funktionen einen neuen Geltungsbereich schaffen. D.h. die Funktionen haben ihren eigenen Namensbereich, den sie auf Namen überprüfen, wenn diese innerhalb der Funktion genannt werden. Wir können überprüfen, welche lokalen und globalen Variablen aktuell definiert sind, indem wir locals() und globals() verwenden. Zum Beispiel:


```python
print(globals())
```

    {'__name__': '__main__', '__doc__': 'Automatically created module for IPython interactive environment', '__package__': None, '__loader__': None, '__spec__': None, '__builtin__': <module 'builtins' (built-in)>, '__builtins__': <module 'builtins' (built-in)>, '_ih': ['', 'def funk():\n    return 1', 'func()', 'funk()', 's = "Globale Variable"\n\ndef funk():', 's = "Globale Variable"\n\ndef funk():\n    print locals()', 's = "Globale Variable"\n\ndef funk():\n    print(locals())', 'print(globals())'], '_oh': {3: 1}, '_dh': ['/Users/davidmika/Github/komplettes-python-bootcamp'], '_sh': <module 'IPython.core.shadowns' from '/Users/davidmika/anaconda/envs/python3/lib/python3.6/site-packages/IPython/core/shadowns.py'>, 'In': ['', 'def funk():\n    return 1', 'func()', 'funk()', 's = "Globale Variable"\n\ndef funk():', 's = "Globale Variable"\n\ndef funk():\n    print locals()', 's = "Globale Variable"\n\ndef funk():\n    print(locals())', 'print(globals())'], 'Out': {3: 1}, 'get_ipython': <bound method InteractiveShell.get_ipython of <ipykernel.zmqshell.ZMQInteractiveShell object at 0x108bd1320>>, 'exit': <IPython.core.autocall.ZMQExitAutocall object at 0x108c1df60>, 'quit': <IPython.core.autocall.ZMQExitAutocall object at 0x108c1df60>, '_': 1, '__': '', '___': '', '_i': 's = "Globale Variable"\n\ndef funk():\n    print(locals())', '_ii': 's = "Globale Variable"\n\ndef funk():\n    print locals()', '_iii': 's = "Globale Variable"\n\ndef funk():', '_i1': 'def funk():\n    return 1', 'funk': <function funk at 0x10865f730>, '_i2': 'func()', '_i3': 'funk()', '_3': 1, '_i4': 's = "Globale Variable"\n\ndef funk():', '_i5': 's = "Globale Variable"\n\ndef funk():\n    print locals()', '_i6': 's = "Globale Variable"\n\ndef funk():\n    print(locals())', 's': 'Globale Variable', '_i7': 'print(globals())'}


Wir erhalten hier ein Dictionary zurück, dass alle globalen Variablen beinhaltet. Viele davon sind in Python vordefiniert. Lasst uns fortfahren und deren Keys überprüfen:


```python
print(globals().keys())
```

    dict_keys(['__name__', '__doc__', '__package__', '__loader__', '__spec__', '__builtin__', '__builtins__', '_ih', '_oh', '_dh', '_sh', 'In', 'Out', 'get_ipython', 'exit', 'quit', '_', '__', '___', '_i', '_ii', '_iii', '_i1', 'funk', '_i2', '_i3', '_3', '_i4', '_i5', '_i6', 's', '_i7', '_i8'])


Ist euch aufgefallen, dass <b>s</b> darunter ist?


```python
globals()["s"]
```




    'Globale Variable'



Jetzt können wir unsere Funktion funk() benutzen, um zu überprüfen, ob es lokale Variablen gibt. Es sollte keine geben...


```python
funk()
```

    {}


Großartig! Jetzt können wir damit beginnen, die Logik eines Dekorators zu verstehen. Hier spielt es wieder eine Rolle, <b>dass in Python alles ein Objekt ist</b>. Das bedeutet, dass Funktionen Objekte sind, die benannt und in andere Funktionen übergeben werden können. Lasst uns mit einem einfachen Beispiel beginnen:


```python
def hallo(name='David'):
    return("Hallo "+name)
```


```python
hallo()
```




    'Hallo David'



Jetzt können wir der Funktion einen Namen geben. Wichtig ist, dass wir an dieser Stelle keine Klammern verwenden. Wir wollen die Funktion nicht ausführen! Stattdessen platzieren wir sie nur in der gruss Variable.


```python
gruss = hallo
```


```python
gruss
```




    <function __main__.hallo>




```python
gruss()
```




    'Hallo David'



Diese Zuordnung ist nicht abhängig von der Originalfunktion!


```python
del hallo
```


```python
hallo()
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-1-df04e3305513> in <module>()
    ----> 1 hallo()
    

    NameError: name 'hallo' is not defined



```python
gruss()
```




    'Hallo David'



## Funktionen innerhalb von Funktionen

Toll! Wir haben gesehen, wie wir Funktionen als Objekte behandeln können. Jetzt können wir uns anschauen, wie man Funktionen innerhalb von anderen Funktionen definieren kann:


```python
def hallo(name="David"):
    print("Die hallo() Funktion wurde ausgeführt")
    
    def gruss():
        return '\t Das ist innerhalb der gruss() Funktion'
    
    def willkommen():
        return '\t Das ist innerhalb der willkommen() Funktion'
    
    print(gruss())
    print(willkommen())
    print("Jetzt sind wir wieder innerhalb der hallo() Funktion")
```


```python
hallo()
```

    Die hallo() Funktion wurde ausgeführt
    	 Das ist innerhalb der gruss() Funktion
    	 Das ist innerhalb der willkommen() Funktion
    Jetzt sind wir wieder innerhalb der hallo() Funktion



```python
willkommen()
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-3-f471134968ef> in <module>()
    ----> 1 willkommen()
    

    NameError: name 'willkommen' is not defined


Durch den Geltungsbereich der Funktionen ist willkommen() außerhalb von hallo() nicht erreichbar. Jetzt können wir lernen, wie wir auf Funktionen innerhalb von Funktionen zugreifen können.

## Zugriff auf Funktionen


```python
def hallo(name="David"):
    
    def gruss():
        return '\t Das ist innerhalb der gruss() Funktion'
    
    def willkommen():
        return '\t Tas ist innerhalb der willkommen() Funktion'
    
    if name == "David":
        return(gruss)
    else:
        return(wilkommen)
```


```python
x = hallo()
```

Lasst uns schauen, welche Funktion wir erhalten, wenn wir x = hallo() setzen. Die geschlossenen Klammern bedeuten, dass der Name als David definiert wurde.


```python
x
```




    <function __main__.hallo.<locals>.gruss>



Gut! Jetzt können wir uns anschauen, wie x zur gruss Funktion innerhalb der hallo Funktion leitet.


```python
print(x())
```

    	 Das ist innerhalb der gruss() Funktion


An dieser Stelle können wir uns noch einmal den Code anschauen.

In der if/else Abfrage geben wir gruss und wilkommen zurück, nicht gruss() und willkommen(). 

Das liegt daran, dass die Klammern hinter dem Namen dafür sorgen, dass die Funktion ausgeführt wird. Wohingegen, wenn wir die Klammern weglassen, wir den Namen übergeben und ihn anderen Variablen zuordnen können, ohne den Code auszuführen.

Wenn wir x = hallo() schreiben, wird hallo() ausgeführt und weil der Name per Definition "David" ist, wird die Funktion gruss() zurückgegeben. Wenn wir die Anweisung x=hallo(name = "Sam") eingeben, erhalten wir die willkommen Funktion zurück.

## Funktionen als Parameter

Lasst uns jetzt betrachten, wie wir Funktionen als Parameter übergeben:


```python
def hallo():
    return "Hallo David!"

def andere(func):
    print("Anderer Code würde hier stehen")
    print(func())
```


```python
andere(hallo)
```

    Anderer Code würde hier stehen
    Hallo David!


Gut! Achtet darauf wie wir die Funktion als Objekt übergeben können und es dann innerhalb einer anderen Funktion nutzen können. Jetzt können wir damit beginnen unseren ersten Dekorator zu schreiben:

## Einen Dekorator erstellen

In dem vorherigen Beispiel haben wir tatsächlich schon manuell einen Dekorator erstellt. Hier werden wir ihn modifizieren, um die Anwendung klarer herauszustellen:


```python
def neu_dekorator(funk):
    
    def huellen_funktion():
        print("Code würde hier stehen, der vor der funk ausgeführt wird.")
        
        funk()
        
        print("Hier steht, was nach der funk ausgeführt wird.")
        
    return huellen_funktion

def funk_braucht_dek():
    print("Diese Funktion braucht einen Dekorator")
```


```python
funk_braucht_dek()
```

    Diese Funktion braucht einen Dekorator



```python
# Neuzuordnung funk_braucht_dekorator
funk_braucht_dek = neu_dekorator(funk_braucht_dek)
```


```python
funk_braucht_dek()
```

    Code würde hier stehen, der vor der funk ausgeführt wird.
    Diese Funktion braucht einen Dekorator
    Hier steht, was nach der funk ausgeführt wird.


Was ist hier passiert? Der Dekorator hat die Funktion umschlossen und ihr Verhalten geändert. Jetzt können wir noch nachvollziehen, wie wir diesen Code schreiben können indem wir das @ Symbol verwenden. Dieses wird in Python für Dekoratoren verwendet:


```python
@neu_dekorator
def funk_braucht_dek():
    print("Diese Funktion braucht einen Dekorator.")
```


```python
funk_braucht_dek()
```

    Code würde hier stehen, der vor der funk ausgeführt wird.
    Diese Funktion braucht einen Dekorator.
    Hier steht, was nach der funk ausgeführt wird.


Toll! Jetzt haben wir manuell einen Dekorator erstellt und gesehen, wie wir das @ Symbol in Python verwenden können, um dies zu automatisieren und den Code aufzuräumen.

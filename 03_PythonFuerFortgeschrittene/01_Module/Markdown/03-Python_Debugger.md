# Python Debugger

Quelle: Datamics

Ihr habt wahrscheinlich eine Menge von print Anweisungen verwendet, um zu versuchen, die Errors in eurem Code zu finden. Ein besserer Weg dies zu tun, ist die Verwendung des vorinstallierten (built-in) Debugger Moduls `pdb`. Das pdb Modul implementiert eine interaktive Debugging Umgebung für Python Programme. Es beinhaltet Features, um euer Programm zu pausieren, die Werte von Variablen anzuschauen und die Programmausführung Schritt für Schritt durchzuführen. So könnt ihr verstehen, was euer Programm wirklich macht und Fehler in der Logik finden.

Das zu zeigen ist ein wenig schwierig, da wir absichtlich einen Error erzeugen müssen. Hoffentlich verdeutlicht dieses einfache Beispiel den großen Nutzen des pdb Moduls.

*Beachtet: Die Nutzung in einem iPython Notebook Setting ist nicht der normale Anwendungsfall.*


```python
x = [1,3,4]
y = 2
z = 3

ergebnis = y + z
print(ergebnis)
ergebnis2 = y+x
print(ergebnis2)
```

    5



    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-1-250126f2ab66> in <module>()
          5 ergebnis = y + z
          6 print(ergebnis)
    ----> 7 ergebnis2 = y+x
          8 print(ergebnis2)


    TypeError: unsupported operand type(s) for +: 'int' and 'list'


Hmmm, wo kommt bloß dieser Error her? Lasst uns ein set_trace() (dt. Spur setzen) implementieren, indem wir das pdb Modul benutzen. Das erlaubt uns den Code an der Stelle der Spur zu pausieren.


```python
import pdb

x = [1,3,4]
y = 2
z = 3

ergebnis = y + z
print(ergebnis)

# Eine Spur mit dem pdb setzen
pdb.set_trace()

ergebnis2 = y+x
print(ergebnis2)
```

    5
    --Return--
    > <ipython-input-2-1825a3fa6c09>(11)<module>()->None
    -> pdb.set_trace()
    (Pdb) x
    [1, 3, 4]
    (Pdb) y
    2
    (Pdb) z
    3
    (Pdb) x+y
    *** TypeError: can only concatenate list (not "int") to list
    (Pdb) q



    ---------------------------------------------------------------------------

    BdbQuit                                   Traceback (most recent call last)

    <ipython-input-2-1825a3fa6c09> in <module>()
          9 
         10 # Eine Spur mit dem pdb setzen
    ---> 11 pdb.set_trace()
         12 
         13 ergebnis2 = y+x


    /Users/davidmika/anaconda/envs/python3/lib/python3.6/bdb.py in trace_dispatch(self, frame, event, arg)
         50             return self.dispatch_call(frame, arg)
         51         if event == 'return':
    ---> 52             return self.dispatch_return(frame, arg)
         53         if event == 'exception':
         54             return self.dispatch_exception(frame, arg)


    /Users/davidmika/anaconda/envs/python3/lib/python3.6/bdb.py in dispatch_return(self, frame, arg)
         94             finally:
         95                 self.frame_returning = None
    ---> 96             if self.quitting: raise BdbQuit
         97             # The user issued a 'next' or 'until' command.
         98             if self.stopframe is frame and self.stoplineno != -1:


    BdbQuit: 


Toll! So konnten wir die verschiedenen Variablen im Code überprüfen und auf Fehler kontrollieren. Ihr könnt 'q' (wie quit; dt.: beenden) benutzen, um den Debugger zu beenden. Für weitere Informationen könnt ihr euch die [Dokumentation](https://docs.python.org/3.2/library/pdb.html) anschauen.

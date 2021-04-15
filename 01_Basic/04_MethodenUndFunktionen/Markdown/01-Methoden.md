# Methoden

Quelle:Datamics

Wir haben schon ein paar Beispiele für Methoden gesehen, als wir uns mit Objekten und Daten Strukturen in Python befasst haben. Methoden sind eigentlich Funktionen, die in Objekte eingebaut sind. Später im Kurs werden wir noch lernen, wie wir unsere eigenen Objekte und Methoden erstellen, indem wir Objektorientierte Programmierung (OOP) und Klassen nutzen.

Methoden führen spezifische Aktionen mit dem Objekt durch und können Parameter aufnehmen, so wie es Funktionen tun. Diese Lektion soll als kurze Einführung zu Methoden dienen und euch zum Denken über das Design von Methoden anregen. Darauf kommen wir zurück, wenn wir die OOP erreichen.

Methoden sind in folgender Form gestaltet:

    object.method(arg1,arg2,arg3,...)
    
Ihr werdet später sehen, dass wir uns Methoden so vorstellen können, dass sie einen "selbst" (en.: self) Parameter haben, der sich aufs Objekt bezieht. Wir können diesen Parameter jetzt nicht sehen, werden in aber später im Kurs nutzen, wenn wir uns mit OOP beschäftigen.

Lasst uns schnell die Methoden zu einer Liste anschauen:


```python
# Liste erstellen
l = [1,2,3,4,5,]
```

Glücklicherweise können wir mit iPython und dem Jupyter Notebook schnell sehen, welche möglichen Methoden ein Objekt hat, indem wir die Tab Taste benutzen. Die Methoden für Listen sind:

* append
* count
* extend
* insert
* pop
* remove
* reverse
* sort

Lasst uns einige ausprobieren:


```python
# append lässt uns Elemente ans Ende der Liste anhängen
l.append(6)
# Check
l
```




    [1, 2, 3, 4, 5, 6]




```python
# Count wertet die Anzahl an Erscheinungen eines Wertes aus
l.count(2)
```




    1



Ihr könnt an jeder Stelle Shift + Tab benutzen, um im Jupyter Notebook mehr Hilfe zu den Methoden zu erhalten. Im Allgemeinen kann man in Python die help() Funktion benutzen:


```python
help(l.count)
```

    Help on built-in function count:
    
    count(...)
        L.count(value) -> integer -- return number of occurrences of value
    


Traut euch ruhig, mit den restlichen Methoden für Listen etwas herumzuspielen. Später in dieser Sektion wird das Quiz die Nutzung von help() und Google Suche nach einigen Methoden beinhalten.

Toll! Durch diese Lektion solltet ihr wie selbstverständlich Methoden zu Objekten aufrufen können.

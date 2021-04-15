# Filter

Quelle: Datamics

Die Funktion filter(funktion, liste) bietet die Möglichkeit, alle Werte aus einer Liste zu filtern, für die die Funktion True ergibt.

Die Funktion filter(funktion, liste) braucht eine Funktion als ihren ersten Parameter. Diese Funktion muss einen Boolean Wert, also True or False, zurückgeben. Die Funktion wird dann auf jedes iterierbares Element der Liste angewendet. Nur wenn die Funktion True ergibt, wird das Element in das Ergebnis aufgenommen.

Schauen wir uns einige Beispiele an:


```python
# Zuerst erstellen wir eine Funktion
def gerade_check(num):
    if num % 2 == 0:
        return True
```

Jetzt können wir eine Liste von Zahlen filtern. Beachtet: evtl. fühlt es sich komisch an, die Funktion ohne Anführungszeichen in den Filter einzugeben. Bedenkt aber, dass auch Funktionen Objekte in Python sind.


```python
lst = range(20)

list(filter(gerade_check,lst))
```




    [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]



filter() wird meistens mit lambda Funktionen genutzt, weil wir Filter meistens für schnelle Aufgaben benutzen, wenn wir keine gesamte Funktion schreiben wollen. Lasst uns das obige Beispiel mit einer lambda Funktion wiederholen:


```python
list(filter(lambda x: x%2==0,lst))
```




    [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]



Toll! Ihr solltet jetzt ein gutes Verständnis davon haben, wie Filter in eurem Code eingesetzt werden können.

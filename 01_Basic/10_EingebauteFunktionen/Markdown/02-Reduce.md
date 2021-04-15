# reduce()

Quelle: Datamics

Häufig haben Anfänger ein Problem damit, reduce() gleich zu verstehen, deshalb: passt jetzt gut auf! Die Funktion

    reduce(funktion,sequenz)
 
wendet eine Funktion fortlaufend auf eine Sequenz an. Sie gibt dann einen einzigen Wert zurück.

Wenn die Sequenz folgendermaßen aussieht seq[s1,s2,s3,...,sn], wird durch das Aufrufen von reduce(funktion,sequenz) folgendes gemacht:
* Zuerst wird die Funktion die ersten beiden Elemente der Sequenz verarbeiten, d.h. funk(s1,s2).
* Die Liste auf die reduce() angewendet wird sieht nun folgendermaßen aus: [funk(s1,s2),s3,...,sn]
* Im nächsten Schritt wird die Funktion auf das erste Ergebnis und das dritte Element der Sequenz angewendet, d.h. funk((funk(s1,s2),s3).
* Die Liste sieht jetzt so aus: [funk(funk(s1,s2),s3),s4,...,sn].
* So geht es immer weiter, bis kein Element mehr außer dem Ergebnis der Funktion in der Liste enthalten ist.


#### Achtung: In Python 3 müssen wir reduce erst importieren

Sehen wir uns ein Beispiel an:


```python
from functools import reduce

lst =[47,11,42,13]
reduce(lambda x,y: x+y,lst)
```




    113



Schauen wir uns ein Diagramm an, um besser zu verstehen, was passiert:
![title](reduce.png)

Beachtet, wie wir die Sequenz immer weiter reduzieren bis ein einzelner Wert erreicht wird. Lasst uns ein weiteres Beispiel betrachten:


```python
# Das Maximum einer Liste finden
max_find = lambda a,b: a if (a > b) else b
```


```python
# Anwendung
reduce(max_find,lst)
```




    47



Hoffentlich versteht ihr, wie nützlich reduce in verschiedenen Situationen sein kann. Behaltet es im Kopf, wenn ihr an euren Projekten arbeitet.

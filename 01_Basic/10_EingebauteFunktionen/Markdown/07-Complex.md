# complex()

Quelle: Datamics

complex() gibt eine komplexe Zahl mit dem Wert reelle Zahl + imag*1j zurück oder wandelt eine Zahl bzw. einen String in eine komplexe Zahl um.

Wenn der erste Parameter ein String ist, wird er als komplexe Nummer interpretiert und die Funktion muss ohne zweiten Parameter aufgerufen werden. Der zweite Parameter kann nie ein String sein. Jedes Argument kann numerischer Art sein. Wenn imag ausgelassen wird, wird es per Standard zu 0 und der Konstruktor dient als eine numerische Konversion wie int und float. Wenn beide Argumente ausgelassen werden erhalten wir 0j.

Wenn sie Mathematik oder Ingenieurswesen betreiben, die komplexe Zahlen benötigen ist es ein nützliches Tool in Python.

Hier einige Beispiele:


```python
# Erstellen der Zahl 2+3j
complex(2,3)
```




    (2+3j)




```python
complex(10,1)
```




    (10+1j)




```python
complex('12.2j')
```




    12.2j



Das ist auch schon alles, was wir über diese nützliche Funktion wissen müssen. Behaltet sie im Kopf, falls ihr je mit komplexen Zahlen arbeiten müsst.

# map()

Quelle: Datamics

map() ist eine Funktion, die zwei Parameter aufnimmt: eine Funktion und eine iterierbare Sequenz. In folgender Form:

    map(funktion,sequenz)

Das erste Argument ist der Name einer Funktion und das zweite der einer Sequenz (z.B. eine Liste). map() wendet die Funktion auf alle Elemente der Sequenz an. Es gibt eine neue Liste mit den Elementen, die durch die Funktion geändert wurden, zurück.

Als wir uns Listen Abstraktion angeschaut haben, haben wir einen kleinen Ausdruck geschrieben, um Fahrenheit in Celsius umzurechnen. Lasst uns das gleiche machen, aber dieses Mal map() benutzen.

Wir starten mit zwei Funktionen:


```python
def fahrenheit(T):
    return ((float(9)/5)*T + 32)
def celsius(T):
    return (float(5)/9)*(T-32)
    
temp = [0, 22.5, 40,100]
```

Lasst uns jetzt map() in Aktion sehen:


```python
F_temps = list(map(fahrenheit, temp))

# Check
F_temps
```




    [32.0, 72.5, 104.0, 212.0]




```python
list(map(celsius, F_temps))
```




    [0.0, 22.5, 40.0, 100.0]



Im obigen Beispiel haben wir keinen lambda Ausdruck verwendet. Durch das Verwenden von lambda hätten wir nicht die Namen für die Funktion fahrenheit() und celsius() definieren müssen.


```python
list(map(lambda x: (5.0/9)*(x - 32), F_temps))
```




    [0.0, 22.5, 40.0, 100.0]



Großartig! Wir haben dasselbe Ergebnis erhalten. map() mit lambda Ausdrücken zu verwenden ist viel stärker verbreitet, da es eben genau der Sinn von map() ist, das manuelle erstellen von for Schleifen zu erübrigen.

map() kann außerdem auf mehr als nur ein iterierbares Objekt angewendet werden. Allerdings müssen die iterierbaren Objekte die selbe Länge haben. 

Zum Beispiel wenn wir mit zwei Listen arbeiten. map() wird die lambda Funktion auf die Elemente der Parameterliste anwenden. D.h. zuerst auf alle Elemente mit Index 0, dann auf alle Elemente mit Index 1 usw. So lange, bis der n-te Index erreicht ist.

Zum Beispiel wenn wir map() auf zwei Listen anwenden:


```python
a = [1,2,3,4]
b = [5,6,7,8]
c = [9,10,11,12]

list(map(lambda x,y:x+y, a,b))
```




    [6, 8, 10, 12]




```python
# Now all three lists
list(map(lambda x,y,z:x+y+z, a,b,c))
```




    [15, 18, 21, 24]



Wir können im obigen Beispiel sehen, dass der Parameter x seinen Wert aus der Liste a erhält, während y seinen Wert aus b erhält und z aus Liste c. Ihr könnt gerne mit euren eigenen Beispielen Versuche unternehmen. So könnt ihr auch überprüfen, ob ihr das Prinzip von map() verstanden habt.

Gute Arbeit! Ihr solltet jetzt ein Grundverständnis der map() Funktion haben.

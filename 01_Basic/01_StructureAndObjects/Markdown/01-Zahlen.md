# Zahlen und mehr in Python!
Quelle: Datamics
In dieser Lektion werden wir mehr über Zahlen in Python lernen und darüber, wie man sie anwendet.
Wir werden folgende Themen behandeln:
1. Arten von Zahlen
2. Grundlegende Arithmetik
3. Unterschied zwischen Python 2 und 3 bei Division
4. Objektzuweisung in Python

## Arten von Zahlen
Python beinhaltet verschiedene "Arten" (en.: types) von Zahlen. Wir werden uns hauptsächlich mit Ganzzahlen (en.: integers) und Kommazahlen (en.: floats) beschäftigen. Später unternehmen wir einen kurzen Abstecher zu den komplexen Zahlen (en.: complex numbers).
Integers sind einfach ganze Zahlen, positiv und negativ. Zum Beispiel: 2 und -2 sind Integers.
Floats sind Kommazahlen und in Python besonders, da sie einen Dezimalpunkt oder einen Exponenten (e) beinhalten, um die Zahl zu definieren. Zum Beispiel sind 2.0 und -2.1 Zahlen mit Dezimalpunkt. 4E2 (4 mal 10 hoch 2) ist ebenso ein Beispiel für eine Float-Zahl in Python.

Im Laufe dieses Kurses werden wir insbesondere mit Integern und Floats arbeiten.
Nun lasst uns mit einfacher Mathematik beginnen.
## Grundlegende Arithmetik


```python
# Addition
2+1
```




    3




```python
# Subtraktion
2-1
```




    1




```python
# Multiplikation
2*2
```




    4




```python
# Division
3/2
```




    1.5



### Python 2 Unterschied!

Würden wir in Python 2 die Division 3/2 durchführen, erhielten wir als Ergebnis 1. Der Grund warum wir dieses Ergebnis erhalten würden ist, dass Python 2 Division anders berechnet als Python 3. In Python 2 erzeugt das / Symbol eine Division im "klassischen" Sinne. Das heißt, dass die Dezimalpunkte abgeschnitten werden. In Python 3 hingegen erzeugt das / Symbol eine "wahre" Division. Das Ergebnis ist also 1.5.

Wie können wir dies in Python 2 umgehen?
Dazu gibt es 2 Lösungen:

a) Eine der Zahlen als Float definieren


```python
# Eine der Zahlen als Float spezifizieren
3.0/2
```




    1.5




```python
# Was für beide Zahlen funktioniert
3/2.0
```




    1.5



b) Wir könnten auch eine der Zahlen mit Hilfe einer Funktion von einem Integer in eine Float umwandelt. Diese Funktion heißt, wenig überraschend, "float()".


```python
# Wir können die float() Funktion nutzen, um Integers umzuwandeln
float(3)/2
```




    1.5



Wir werden später im Kurs noch viel detaillierter auf Funktionen eingehen, also keine Sorgen, falls diese Syntax zunächst ungewohnt scheint. Ihr könnt das als kleine Vorschau betrachten.

Eine weitere "Vorschau" die wir nutzen können um mit klassischer Division in Python 2 zu arbeiten ist es, das sogenannten <b>future</b> Modul zu importieren.

Das ist ein Modul in Python 2, das Python 3 Funktionen beinhaltet. Somit erlaubt es uns Python 3 Funktionen in Python 2 zu nutzen. Wir werden später im Kurs auch auf Imports und Module noch genauer eingehen, also keine Sorge, falls Sie das import Statement noch nicht ganz nachvollziehen können.


```python
from __future__ import division
3/2
```




    1.5



Wenn wir `division` aus dem <b>future</b> Modul importieren, dann wird die klassische Division niergendwo mehr im Python 2 Code in Problem darstellen.

## Weitere Arithmethik


```python
# Potenzen
2**3
```




    8




```python
# So wird auch die Wurzel gezogen
2**0.5
```




    1.4142135623730951



Python folgt gängigen Regeln der Mathematik. Dazu gehören die Operatorrangfolge (Punkt-vor-Strick-Rechnung), sowie Assoziativ- und Kommutativgesetzt. Das ist wichtig für das Rechnen komplizierterer Ausdrücke bspw. unter Verwendung von Klammern.


```python
# Die Reihenfolge der Operationen wird in Python eingehalten
2 + 10 * 10 + 3
```




    105




```python
# Klammern können genutzt werden um die Reihenfolge zu spezifizieren
(2+10)*(10+3)
```




    156



## Variablen Zuweisung

Jetzt wo wir gesehen haben wie in Python grundsätzlich mit Zahlen gerechnet wird, können wir uns anschauen, wie wir Namen zuweisen und Variablen erstellen können.

Anders als in den meisten anderen Programmiersprachen müssen wir Python nicht erst sagen, welchem Datentyp eine Variable angehört. Python erkennt das an der Schreibweise, die wir bei der Definition verwenden. Wir werden immer mehr darüber lernen, je mehr Datentypen wir kennenlernen.

### Andere Sprachen

Um beispielsweise in C eine Variable mit Zahlenwert zu definieren müssen wir erst angeben, welchen Datentyp unsere Variable haben soll.

    int x;

Somit weiß die Programmiersprache (in diesem Fall C), dass wir für die Variable den Datentyp Integer (dt.: Ganzzahl) verwenden möchten. Das "Problem" daran ist, dass sie nun auch wirklich nur noch Zahlen als Wert tragen kann. Anschließend können wir in einem zweiten Schritt den tatsächlichen Wert definieren.

    x = 42;

### Python

In Python nutzen wir ein einzelnes = Zeichen, um Variablen ihrem Namen zuzuweisen. Lasst uns ein paar Beispiele betrachten. Python erkennt dabei den Datentyp automatisch.


```python
# Wir erstellen ein Objekt names "a" and weisen ihm die Zahl 5 zu
a = 5
```

Wenn ich nun in meinem Python-Skript a aufrufe, wird es Python als 5 behandeln.


```python
# Die Objekte addieren
a+a
```




    10



Was geschieht bei Neuzuweisung? Wird Python uns die Variable überschreiben lassen?


```python
# Neuzuweisung
a = 10
```


```python
a
```




    10



Ja! Python lässt uns bereits vergebene Variablennamen überschreiben. Wir können außerdem die Variablen selbst benutzen, um eine Neuzuweisung durchzuführen. Hier ist ein Beispiel dafür, was ich meine:


```python
# Check
a
```




    10




```python
# Wir benutzen a um a neu zuzuweisen
a = a + a
```


```python
# Check
a
```




    20



In Python müssen die Namen, die wir nutzen um diese Labels zu erstellen, einigen Regeln folgen:

1. Namen dürfen nicht mit einer Zahl beginnen
2. Es darf keine Leerzeichen im Namen geben, nutzt stattdessen _
3. Folgende Zeichen dürfen nicht beinhaltet sein: '",<>/?|\()!@#$%^&*~-+
4. Es wird üblicherweise so gehandhabt Namen klein zu schreiben

Die Verwendung von Variablennamen kann ein nützliches Hilfsmittel sein, um den Überblick über verschiedene Variablen in Python zu behalten. Zum Beispiel:


```python
# Hier werden die Namen benutzt, um den Überblick zu behalten!
einkommen = 100

steuersatz = 0.1

steuern = einkommen * stauersatz
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-20-ea8ee669c3c4> in <module>
          4 steuersatz = 0.1
          5 
    ----> 6 steuern = einkommen * stauersatz
    

    NameError: name 'stauersatz' is not defined



```python
# Meine Steuern zeigen
steuern
```




    10.0



Was haben wir also gelernt? Wir haben Grundlegendes über Zahlen in Python gelernt. Zusätzlich haben wir gelernt, wie man Arithmethik in Python anwendet und einfache Berechnungen durchführt. Diese Lektion wurde dadurch abgeschlossen, die Zuweisung von Variablen kennenzulernen.

Im nächsten Kapitel beschäftigen wir uns mit: Strings.

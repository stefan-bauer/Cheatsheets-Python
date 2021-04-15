# Verschachtelte Anweisungen und Geltungsbereich

Quelle: Datamics

Jetzt, da wir unsere eigenen Funktionen zu schreiben gelernt haben, ist es wichtig zu verstehen, wie Python mit Variablen Namen umgeht. Wenn wir einen Variable Namen erstellen wird dieser im sogenannten Namensraum (en.: name space) gespeichert. Variablen Namen haben außerdem einen Geltungsbereich, welcher bestimmt, welche anderen Teile des Codes diesen Namen kennen. 

Lasst und mit einem kurzen Gedankenexperiment beginnen:


```python
x = 25

x = 25

def drucker():
    x = 50
    return x

print(x)
print(drucker())
```

Was denkt ihr, wird die Ausgabe für unseren drucker() sein wird? Und was wird print(x) ausgeben? 25 oder 50?


```python
print(x)
```

    25



```python
print(drucker())
```

    50


Interessant! Aber woher weiß Python, welches x wir mit unserem Code meinen? Hier kommt das Konzept des Geltungsbereichs ins Spiel. Python befolgt einige Regeln, um zu entscheiden, welche Variable (so wie x) gemeint ist. Lasst uns diese Regeln betrachten:

Dir Idee des Geltungsbereichs ist sehr wichtig zu verstehen, um Variablennamen richtig zu vergeben und aufzurufen.

Einfach ausgedrückt kann diese Idee bei 3 grundsätzlichen Regeln beschrieben werden:

1. Namenszuweisungen werden lokale Namen per Standard erstellen oder ändern
2. Namensreferenzen durchlaufen 4 Bereiche, die da heißen:
    * lokal
    * einschließende Funktionen
    * global
    * bereits eingebaut
3. Namen die in globalen und nichtlokalen Anweisungen definiert werden ordnen Namen dem Geltungsbereich einschließender Funktionen zu.

#### LEGB Regel

L: Lokal - Namen die in irgendeiner Form innerhalb einer Funktion (def oder lambda) zugewiesen werden und nicht global in dieser Funktion definiert sind.

E: Einschließende Funktionen - Namen im lokalen Geltungsbereich aller einschließenden Funktionen (def oder lambda) von innen nach außen.

G: Globale (Module) - Namen die auf der höchsten Ebene einer Datei zugewiesen werden oder innerhalb einer Funktion als global ausgewiesen werden.

B: Bereits (in Python) eingebaute - Namen die bereits in die vorinstallierten Module wie range, open, usw. eingebaut sind.

## Kurzes Beispiel für LEGB

### Lokal


```python
# x ist hier Lokal
f = lambda x:x**2
```

### Einschließende Funktionen

Das passiert, wenn wir eine Funktion in einer Funktion haben.


```python
name = 'Das ist ein globaler Name'

def gruss():
    # Einschließende Funktion
    name = 'David'
    
    def hallo():
        print('Hallo '+name)
    
    hallo()

gruss()
```

    Hallo David


Achtet darauf, wie David verwendet wurde, weil die hallo() Funktion in der gruss() Funktion eingeschlossen ist!

### Global

In Jupyter können wir schnell überprüfen, ob eine Variable global ist, indem wir schauen, ob eine andere Zelle auf sie zugreifen kann.


```python
print(name)
```

    Das ist ein globaler Name


### Bereits eingebaute

Das sind die vorinstallierten Funktionsnamen in Python. Überschreibt diese besser nicht!


```python
len
```




    <function len>



## Lokale Variablen

Wenn ihr Variablen innerhalb einer Funktionsdefinition deklariert, dann sind sie in keiner Weise mit anderen Variablen außerhalb der Funktion verknüpft, die denselben Namen haben. D.h. die Namen  von Variablen sind lokal in Bezug auf Funktionen. Das ist somit der Geltungsbereich der Variablen. Alle Variablen haben den Geltungsbereich des Blocks in dem sie deklariert werden ausgehend von dem Punkt, an dem sie definiert werden.

Ein Beispiel:


```python
x = 50

def funk(x):
    print('x ist',x)
    x = 2
    print('Lokales x ist jetzt',x)

funk(x)
print('x ist noch',x)
```

    x ist 50
    Lokales x ist jetzt 2
    x ist noch 50


Das erste Mal, wenn wir den Wert des Namens x ausgeben, also mit der ersten Zeile innerhalb der funk(x) Funktion, nutzt Python die Definition im Hauptblock, also über der Funktion.

Danach ordnen wir x den Wert 2 zu. Der Name x ist lokal für unsere Funktion. Wenn wir also den Wert von x in der Funktion ändern, dann bleibt das x des Hauptblocks unberührt.

Mit der letzten print() Anweisung geben wir den Wert des x des Hauptblocks aus. Dadurch können wir bestätigen, dass es wirklich unberührt von der lokalen Definition innerhalb der Funktion geblieben ist.

## Die global Anweisung

Wenn man einen Wert einem Namen des Hauptblocks eines Programms zuordnen möchte, dann muss man Python sagen, dass die Zuweisung nicht lokal, sondern global ist. Dies tun wir durch die Verwendung der global Anweisung. Es ist unmöglich einen Wert einer Variablen außerhalb der Funktion ohne die gloabl Anweisung zuzuordnen.

Ihr könnt den Wert solcher Variablen, die außerhalb der Funktion definiert sind, verwenden, sofern es innerhalb keine Variable mit gleichem Namen gibt. Nichtsdestotrotz empfehlen wir das nicht, da es so schwer für den Leser wird, den Code zu lesen. Die global Anweisung macht den Geltungsbereich für alle Leser klar.

Ein Beispiel:


```python
x = 50

def funk():
    global x
    print('Diese Funktion nutzt jetzt das globale x!')
    print('Durch global wird x zu: ',x)
    x = 2
    print('funk() wurde ausgeführt, x geändert zu: ',x)

print('Bevor wir funk() aufrufen ist x: ',x)
funk()
print('Der Wert von x außerhalb von funk() ist jetzt: ',x)
```

    Bevor wir funk() aufrufen ist x:  50
    Diese Funktion nutzt jetzt das globale x!
    Durch global wird x zu:  50
    funk() wurde ausgeführt, x geändert zu:  2
    Der Wert von x außerhalb von funk() ist jetzt:  2


Die global Anweisung wurde benutzt, um zu definieren, dass x hier eine globale Variable ist. Dadruch ändert sich, wenn wir x innerhalb der Funktion einen Wert zuweisen, auch der des x im Hauptblock des Codes.

Man kann mehrere Variablen auf einmal als global deklarieren. Zum Beispiel:

    global x, y, z
  
## Zusammenfassung

Ihr solltet jetzt ein gutes Verständnis dafür haben, wie sich der Geltungsbereich von Variablen in Python ausdrückt. Ein letzte Anmerkung hierzu ist, dass ihr globals() und locals() nutzen könnt, um zu überprüfen, welche eurer Variablen aktuell als global oder lokal gespeichert sind.

Ein anderer Punkt, den man im Gedächtnis behalten sollte, ist, dass in Python alles Objekte sind. Ich kann Funktionen Variablen zuweisen, so wie ich Zahlen zuweisen kann. Wir werden dies noch einmal brauchen, wenn wir in der Sektion der Dekoratoren sind.

# Funktionen

Quelle: Datamics

## Einführung zu Funktionen

Diese Lektion wird sich damit beschäftigen, was eine Funktion in Python ist und wie sie erstellt wird. Funktionen werden einer unserer Hauptbestandteile sein, wenn wir immer umfangreichere Codes schreiben. 

In anderen Programmiersprachen kennt man sie auch unter den Namen Subroutinen, Routinen, Prozeduren, Methoden und Unterprogrammen. 

<b>Was sind also Funktionen in Python?</b>

Formell gesehen ist eine Funktion ein nützliches Hilfsmittel, um einzelne Statements zu gruppieren, um sie dann mehr als einmal aufrufen zu können. Sie können außerdem Parameter definieren, die uns als Input für die Funktion dienen können.

Ganz grundsätzlich betrachtet erlauben es uns Funktionen, den selben Code nicht immer wieder schreiben zu müssen. Wenn ihr zurückdenkt an unsere Lektion zu Strings und Listen in Python, dann erinnert euch an die Funktion len(), die wir genutzt haben, um die Länge eines Strings bzw. einer Liste zu erhalten. Da die Überprüfung der Länge einer Sequenz eine widerkehrende Aufgabe ist, ist es somit eine solche Aufgabe, die wir in eine Funktion packen wollen würden.

### Die Vorteile von Funktionen

Aus ihren Eigenschaften ergeben sich zwei wichtige Vorteile für die Programmierung bzw. Softwareentwicklung:

* Die Benutzung von Funktionen erhöht die Verständlichkeit und Qualität eines Programmes oder Skriptes.
* Außerdem senkt die Verwendung von Funktionen auch die Kosten für die Softwareentwicklung und die Wartung der Software.

Funktionen werden eine der einfachsten Möglichkeiten sein, um Code in Python wiederzuverwenden. Und es wird uns ermöglichen, über Programm Design nachzudenken (worüber wir später noch viel genauer sprechen werden, sobald es um OOP geht).

## def Anweisungen

Folgendermaßen ist eine Funktion in Python aufgebaut:


```python
def name_der_funktion(par1,par2):
    '''
    Hier kommt die Beschreibung (doc-string) einer Funktion hin
    '''
    # Tue hier Dinge
    # Gebe gewünschtes Ergebnis aus
```

Wir beginnen mit `def` gefolgt von einem Leerzeichen und dem Namen der Funktion. Die Namen sollten möglichst präzise und eindeutig gewählt werden. Ein Beispiel ist die len() Bezeichnung für eine length() Funktion. Außerdem sollte man darauf achten, keine Namen zu verwenden, die durch vorinstallierte (built-in) Python Funktionen belegt sind (wie z.B. len).

Als nächstes kommt ein Paar von Klammern, die die Parametern beinhalten, die jeweils durch Komma getrennt sind. Diese Parameter sind der Input für eure Funktion. Wir können diese innerhalb der Funktion verwenden und auf sie verweisen. Danach setzen wir einen Doppelpunkt.

Danach folgt die Beschreibung (doc-string) der Funktion. Diese stellt eine kurze Beschreibung der Funktion und dessen, was sie tut, dar. Durch die Verwendung von iPython und den Notebooks können wir diese Beschreibung lesen, indem wir Shift + Tab nach einem Funktionsnamen drücken. Beschreibungen sind bei einfachen Funktionen nicht notwendig, aber es ist eine bewährte Verfahrensweise diese einzufügen, damit man selbst oder andere Leute den Code schnell verstehen.

Nach all dem beginnt man den tatsächlichen Code zu schreiben, der ausgeführt werden soll.

Der beste Weg um Funktionen zu lernen ist es, einige Beispiele zu betrachten. Lasst uns dies deshalb tun und Bezug nehmen auf einige Objekte und Daten Strukturen, die wir bereits kennengelernt haben.

### Beispiel 1: Eine einfache print 'hallo' Funktion:


```python
def sag_hallo():
    print('Hallo')
```


```python
# Funktion ausführen
sag_hallo()
```

    Hallo


### Beispiel 2: Eine einfache Begrüßungs Funktion, die Leute mit ihrem Namen begrüßt


```python
def gruß(name):
    print('Hallo',name)
```


```python
#Funktion ausführen
gruß('David')
```

    Hallo David


## return nutzen

Lasst uns einige Beispiele betrachten, die das return Statement benutzen. return erlaubt es einer Funktion ein Ergebnis zurückzugeben, das dann als Variable gespeichert oder in beliebiger anderer Weise verwendet werden kann.

### Beispiel 3: Additions Funktion


```python
def add_num(num1,num2):
    return num1+num2
```


```python
add_num(4,5)
```




    9




```python
# Wir können das Ergebnis auch als Variable speichern
ergebnis = add_num(3,7)
```


```python
print(ergebnis)
```

    10



```python
# Was passiert, wenn wir zwei Strings eingeben?
print(add_num('eins','zwei'))
```

    einszwei


Beachtet, dass dadurch, dass wir keine Variablen Arten in Python definieren, diese Funktion dazu genutzt werden kann, sowohl Nummern als auch Sequenzen zu addieren. Wir werden später lernen, wie wir Kontrollen einbauen können, die überprüfen, ob ein Nutzer korrekte Parameter in die Funktion eingegeben hat. 

Lasst uns außerdem damit beginnen, `break`, `continue` und `pass` Anweisungen zu nutzen. Wir haben sie in der while Lektion eingeführt.

Dazu werden wir abschließend ein Beispiel durchgehen, dass eine Funktion zeigt, die überprüft, ob eine Zahl eine Primzahl ist (eine häufige Aufgabe in Bewerbungsgesprächen).

Wir wissen, dass eine Zahl eine Primzahl ist, wenn sie nur gerade durch 1 und sich selbst teilbar ist. Lasst uns eine erste Funktion schreiben, die dies mit Hilfe von Modulo überprüft.


```python
def ist_prim(num):
    '''
    Erste Methode um Primzahlen zu testen
    '''
    for n in range(2,num):
        if num % n == 0:
            print("Keine Primzahl")
            break
    else:
        print("Primzahl")
```


```python
ist_prim(16)
```

    Keine Primzahl


Achtet darauf, wie wir break nach der print Anweisung benutzen! Wir können diese Überprüfung noch verbessern, indem wir nach der Quadratwurzel der Zielzahl überprüfen. Außerdem können wir alle geraden Zahlen auslassen, sobald wir 2 überprüft haben. Und zusätzlich werden wir zu Boolean Werten wechseln, um zu sehen, wie wir die return Anweisung verwenden:


```python
import math

def ist_prim(num):
    '''
    Bessere Methode, um Primzahlen zu überprüfen
    '''
    if num % 2 == 0 and num > 2:
        return False
    for i in range(3, int(math.sqrt(num)) + 1, 2):
        if num % i == 0:
            return False
    return True
```


```python
ist_prim(9)
```




    False



Großartig! Ihr solltet nun ein Grundverständnis dafür entwickelt haben, wie ihr eure eigenen Funktionen in Python schreiben könnt und  euch so das wiederholte schreiben des gleichen Codes spart.

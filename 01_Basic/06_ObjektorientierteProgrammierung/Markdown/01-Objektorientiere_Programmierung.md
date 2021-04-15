# Objektorientierte Programmierung

Quelle:Datamics

Objektorientierte Programmierung (OOP) ist eine der größten Herausforderungen für Beginner, wenn sie lernen, Python zu programmieren. 

Es gibt viele, wirklich viele Übungen und Lektionen die OOP abdecken. Ihr könnt für zusätzliches Material einfach danach googln. Außerdem stelle ich euch einige nützliche Links zu anderen Übungen ans Ende dieses Notebooks.

Wir werden das Wissen dieser Lektion über OOP auf folgenden Themen aufbauen:

* Objekte
* Nutzen des <i>class</i> Stichworts
* Erstellen von class Attributen
* Erstellen von Methoden in class
* Lernen über Vererbung
* Spezielle Methoden für classes

Lasst uns diese Lektion damit beginnen, uns unser Wissen über grundsätzliche Python Objekte in Erinnerung zu rufen. Zum Beispiel:


```python
l = [1,2,3]
```

Wisst ihr noch, wie wir Methoden auf eine Liste anwenden?


```python
l.count(2)
```




    1



Was wir diese Lektion hauptsächlich untersuchen werden ist, wie wir ein Objekt wie dieses erstellen können. Wir haben ja bereits gelernt, wie wir Funktionen erstellen können. Lasst uns also zunächst Objekte im Allgemeinen anschauen:

## Objekte

In Python ist alles ein Objekt. Erinnert euch daran, dass wir in vorherigen Lektionen type() dazu benutzen, um zu überprüfen, welchen Typ ein Objekt hat:


```python
print(type(1))
print(type([]))
print(type({}))
print(type(()))
```

    <class 'int'>
    <class 'list'>
    <class 'dict'>
    <class 'tuple'>


Wir wissen also, dass all diese Dinge Objekte sind. Wie können wir nun unsere eigenen Objekte erstellen? An dieser Stelle kommt das `class` Stichwort ins Spiel.

## class

Die vom Nutzer definierten Objekte werden durch das class Stichwort erstellt. class ist eine Blaupause, die die Eigenschaften eines zukünftigen Objektes festhält. Von Klassen (classes) können wir Instanzen konstruieren. Eine Instanz ist ein spezifiziertes Objekt, das aus einer bestimmten Klasse geschaffen wurde. Zum Beispiel haben wir oben l erstellt, dass eine Instanz eines Listen Objekts ist.

Lasst uns sehen, wie wir class verwenden:


```python
# Einen neuen Objekt Typ erstellen, der Beispiel heißt
class Beispiel(object):
    pass

# Instanz von Beispiel

x = Beispiel()

print(type(x))
```

    <class '__main__.Beispiel'>


Üblicherweise geben wir Klassen einen Namen, der mit einem Großbuchstaben beginnt. Achtet darauf, wie x jetzt eine Referenz für unsere neue Instanz der Beispiel Klasse ist. 

Innerhalb der Klasse haben wir aktuell nur `pass`. Wir können aber auch Kassen Attribute und Methoden definieren.

Ein Attribut ist eine Charakteristik eines Objekts. Eine Methode ist eine Operation, die wir auf das Objekt anwenden können.

Zum Beispiel können wir eine Klasse erstellen, die Hund heißt. Ein Attribut könnte beispielsweise die Rasse oder der Name sein, während eine Methode des Hundes z.B. bellen() sein könnte. 

Lasst uns ein besseres Verständnis dafür durch ein Beispiel erhalten:

## Attribute

Die Syntax für ein Attribut ist:
    
    self.attribut = etwas
    
Es gibt eine spezielle Methode namens:

    __init__()
    
Diese Methode wird genutzt, um das Attribut eines Objektes zu initiieren. Zum Beispiel:


```python
class Hund(object):
    def __init__(self,rasse):
        self.rasse = rasse
    
sam = Hund(rasse="Lab")
frank = Hund(rasse="Huskie")
```

Lasst uns herunterbrechen, was wir getan haben. Die spezielle Methode

    __init__()
    
wird automatisch aufgerufen, sobald das Objekt erstellt wurde:

    def __init__(self,rasse):
    
Jedes Attribut in einer Klassendefinition beginnt mit einer Referenz auf das Instanz-Objekt. Gewöhnlich nennt man es `self` (selbst). Die Rasse ist das Argument. Der Wert wird während der Klassenerstellung übergeben.

    self.rasse = rasse
    
Jetzt habebn wir zwei Instanzen der Hunde Klasse erstellt. Mit zwei Rassen. Um diese Attribute aufzurufen können wir nun folgendes tun:


```python
sam.rasse
```




    'Lab'




```python
frank.rasse
```




    'Huskie'



Bemerkenswert ist an dieser Stelle, dass wir keine Klammern hinter rasse verwendet haben. Das liegt daran, dass es ein Attribut ist. Diese nehmen keine Parameter auf.

In Python gibt es auch Klassen Objekt Attribute. Diese Klassen Objekt Attribute gelten für alle Instanzen dieser Klasse. Zum Beispiel könnten wir für die Klasse Hund ein Attribut namens spezies einführen. Hunde sind ganz unabhängig von ihrer Rasse und ihrem Namen eins immer mit Sicherheit: Säugetiere. Diese Logik setzen wir folgendermaßen um:


```python
class Hund(object):
    
    # Klassen Objekt Attribut
    spezies = "saeugetier"
    
    def __init__(self,rasse,name):
        self.rasse = rasse
        self.name = name
```


```python
sam = Hund("Lab","Sam")
```


```python
sam.name
```




    'Sam'



Wichtig ist, dass das Klassen Objekt Attribut außerhalb aller Methoden in der Klasse definiert wird. Üblicherweise platzieren wir sie vor dem init.


```python
sam.spezies
```




    'saeugetier'



## Methoden

Methoden sind Funktionen die innerhalb des Körpers einer Klasse definiert sind. Sie werden genutzt, um Operationen mit den Attributen unserer Objekte durchzuführen. Methoden sind entscheidend im Abkapselungskonzept des OOP Paradigmas. Das ist entscheidend, wenn Verantwortungen im Programmieren verteilt werden, insbesondere in großen Anwendungen.

Ihr könnt Methoden grundsätzlich so verstehen, dass es Funktionen auf ein Objekt sind, die das Objekt selbst durch das self Argument berücksichtigen.

Lasst uns als Beispiel eine Kreis Klasse durchgehen:


```python
class Kreis(object):
    pi = 3.14
    
    # Ein Kreis hat einen Radius, der per Standard 1 ist
    def __init__(self,radius=1):
        self.radius = radius
        
    # Die flaeche Methode berechnet die Fläche. Achtet auf die Verwendung von self.
    def flaeche(self):
        return self.radius * self.radius * Kreis.pi
    
    # Methode um den Radius zu definieren
    def radiusEinstellen(self,radius):
        self.radius = radius
        
    # Methode um den Radius auszulesen (das selbe wie .radius aufzurufen)
    def radiusErhalten(self):
        return self.radius
    
c = Kreis()

c.radiusEinstellen(2)
print("Der Radius ist:",c.radiusErhalten())
print("Die Fläche ist:",c.flaeche())
```

    Der Radius ist: 2
    Die Fläche ist: 12.56


Großartig! Achtet darauf, wie wir die self Notation genutzt haben, um Referenz zu Attributen innerhalb der Methode zu nehmen. Schaut euch noch einmal genau an, wie der obige Code funktioniert.

## Vererbung

Vererbung ist ein Weg, um neue Klassen durch bereits existierende Klassen zu erstellen. Die neu erstellten Klassen werden abgeleitete Klassen genannt. Die Klassen die als Referenz genommen werden nennen wir Basisklassen. Wichtige Vorteile von Vererbung sind Codewiederverwertung und die Reduktion von Komplexität im Programm. Die abgeleiteten Klassen überschreiben oder erweitern die Funktionalität der Basisklassen. 

Lasst uns ein Beispiel mit Rückgriff auf unsere Hunde Klasse durchgehen:


```python
class Tier(object):
    def __init__(self):
        print("Tier erschaffen")
        
    def werBinIch(self):
        print("Tier")
        
    def essen(self):
        print("Essen")
        
class Hund(Tier):
    def __init__(self):
        Tier.__init__(self)
        print("Hund erstellt")

    def werBinIch(self):
        print("Hund")

    def bellen(self):
        print("Woof!")
```


```python
d = Hund()
```

    Tier erschaffen
    Hund erstellt



```python
d.werBinIch()
```

    Hund



```python
d.essen()
```

    Essen



```python
d.bellen()
```

    Woof!


In diesem Beispiel haben wir zwei Klassen: Tier und Hund. Das Tier ist die Basisklasse, der Hund ist die abgeleitete Klasse,

Die abgeleitete Klasse erbt die Funktionalität der Basisklasse.

* Zu sehen an der essen() Methode.

Die abgeleitete Klasse bearbeitet bereits bestehendes Verhalten der Basisklasse.

* Zu sehen an der werBinIch() Methode.

Zu guter Letzt erweitert die Funktionalität der Basisklasse.

* Zu sehen an der bellen() Methode.

## Spezielle Methoden

Abschließend können wir über spezielle Methoden sprechen. Klassen in Python können bestimmte Operationen mit speziellen Methoden Namen implementieren. Diese Methoden werden nicht tatsächlich direkt aufgerufen, sondern bei Python interner Syntax. Lasst uns als Beispiel eine Buch Klasse erstellen:


```python
class Buch(object):
    def __init__(self, titel, autor, seiten):
        print("Ein Buch wurde geschrieben!")
        self.titel = titel
        self.autor = autor
        self.seiten = seiten
        
    def __str__(self):
        return "Titel:%s , Autor:%s , Seiten:%s" %(self.titel, self.autor, self.seiten)
        
    def __len__(self):
        return self.seiten
    
    def __del__(self):
        print("Ein Buch wurde zerstört!")
```


```python
buch = Buch("Python rockt!","Dr. Brunner",987)

# Spezielle Methoden
print(buch)
print(len(buch))
del buch
```

    Ein Buch wurde geschrieben!
    Ein Buch wurde zerstört!
    Titel:Python rockt! , Autor:Dr. Brunner , Seiten:987
    987
    Ein Buch wurde zerstört!


Diese speziellen Methoden sind durch Unterstrichte definiert. Sie erlauben es uns, Python spezifische Funktionen auf Objekte anzuwenden, die durch unsere Klasse erstellt werden.

**Toll! Nach dieser Lektion solltet ihr ein Verständnis dafür haben, wie ihr eure eigenen Objekte mit class erstellen könnt. Ihr werdet davon stark Gebrauch machen, in eurem nächsten Meilenstein Projekt.**

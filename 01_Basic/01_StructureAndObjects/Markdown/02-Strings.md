# Strings
Quelle: Datamics

`Strings` werden in Python dazu benutzt, um Textinformationen, wie bspw. Namen, festzuhalten. 

## Sequenzen

Genau genommen sind Strings in Python eine Sequenz. Das bedeutet, dass Python jedes einzelne Element in der Sequenz (in diesem Fall ein String) individuell beachtet. Ein Beispiel ist der String "hallo", den Python als Sequenz der einzelnen Buchstaben in einer **bestimmten Reihenfolge speichert**. Das hat zur Folge, dass wir später in der Lage sein werden zu **indexieren** und so bestimmte Buchstaben (z.B. den ersten oder letzten) aus einem String auszulesen.

Diese Idee einer Sequenz ist wichtig in Python und sie wird uns begleiten.

Zu den Sequenzen in Python gehören:

* Strings
* Listen
* Tupel
* Binärdaten

## Zurück zu Strings

In dieser Lektion werden wir folgendes lernen:

1. Erstellen von Strings
2. Ausgeben von Strings
3. Unterschiede in der Ausgabe von Python 2 und Python 3
4. Indexierung von Strings und Zerteilen
5. String Eigenschaften
6. String Methoden
7. Ausgabe Formatierung

## Erstellen von Strings

Um einen String in Python zu erstellen müssen wir entweder einfache oder doppelte Anführungszeichen benutzen. Zum Beispiel:


```python
# Einzelnes Wort
'hallo'
```




    'hallo'




```python
# Ganze Phrase
'Das ist ein String'
```




    'Das ist ein String'




```python
# Wir können auch doppelte Anführungszeichen benutzen
"String mit doppelten Anführungszeichen"
```




    'String mit doppelten Anführungszeichen'




```python
# Gebt Acht bei der Verwendung von Anführungszeichen
'Ich bin's ein String, der Probleme verursacht'
```


      File "<ipython-input-4-c0d31b96601f>", line 2
        'Ich bin's ein String, der Probleme verursacht'
                 ^
    SyntaxError: invalid syntax




```python
"Ich bin's wieder, aber dieses mal ohne Probleme"
```




    "Ich bin's wieder, aber dieses mal ohne Probleme"



Lasst uns jetzt etwas über die Ausgabe von Strings lernen!

## Ausgabe von Strings

Da wir Jupyter Notebooks benutzen, wird, wenn wir in den Zellen einen String erstellen, dieser automatisch ausgegeben. Die richtige Vorgehensweise, um Strings im Output auszugeben, ist allerdings die Verwendung der `print` Funktion.


```python
# Wir können einen String einfach deklarieren
'Hallo Welt!'
```




    'Hallo Welt!'




```python
# Bemerkenswert, dass wir nicht mehrere Strings ausgeben können
'Hallo Erde'
'Hallo Mond'
```




    'Hallo Mond'



Wir können aber auch das print Statement verwenden, um den String auszugeben.


```python
print('Hallo Erde')
print('Hallo Mond')
print('Nutze \n um in einer neuen Zeile auszugeben')
print('\n')
print('Seht ihr, was ich meine?')

```

    Hallo Erde
    Hallo Mond
    Nutze 
     um in einer neuen Zeile auszugeben
    
    
    Seht ihr, was ich meine?


## String Grundlagen

Wir können die Funktion len() nutzen, um die Länge eines Strings zu ermitteln!


```python
len('Hallo Welt')
```




    10



## String Indexierung

Wir wissen bereits, dass Strings eine Sequenz sind, für die Python einen Index bilden kann, um bestimmte Teile aufzurufen. Lasst uns herausfinden, wie das funktioniert.

In Python nutzen wir [] nach einem Objekt, um den Index aufzurufen. Dabei gilt zu beachten, dass der Index in Python bei 0 beginnt. Wir können jetzt ein neues Objekt erstellen und ein paar Beispiele für Indexierung betrachten.


```python
# Dem Objekt s einen String zuweisen
s = 'Hallo Welt'
```


```python
# Check
s
```




    'Hallo Welt'




```python
# Das Objekt ausgeben
print(s)
```

    Hallo Welt


Jetzt können wir mit dem Indexieren loslegen.


```python
# Zeige das erste Element (in diesem Fall einen Buchstaben)
s[0]
```




    'H'




```python
s[1]
```




    'a'




```python
s[2]
```




    'l'



## Ausschneiden

Wir können einen : verwenden, um Teile eines Strings auszuschneiden (en.: slicing). Der englische Begriff "*Slicing*" wird auch im deutschen Sprachgebrauch häufig verwendet. Ihr solltet ihn also im Kopf behalten.

Beim Slicing wird alles von einer bis zu einer anderen angegebenen Stelle gewählt. Wir können den Start oder Endpunkt weglassen, um verschiedene besondere Effekte zu erzeugen. Zum Beispiel:


```python
# Alles nach dem ersten Index auswählen
s[1:]
```




    'allo Welt'




```python
# Beachtet, dass sich am Original s nichts ändert
s
```




    'Hallo Welt'




```python
# Alles bis zum dritten Index auswählen
s[:3]
```




    'Hal'



Schaut euch die Aufteilung oben genau an. Wir haben Python beauftragt alles von Index 0 bis Index 3 zu nehmen. Dabei wurde der dritte Index nicht eingeschlossen. Ihr werdet feststellen, dass Python Anweisungen und Methoden gewöhnlich im Sinne von "bis zu, aber nicht einschließlich" interpretiert.


```python
# Alles
s[:]
```




    'Hallo Welt'



Wir können außerdem negative Indexierung verwenden, um rückwärts zu gehen.


```python
# Der letzte Buchstabe (einer hinter Index 0, 
# wordurch Python von hinten liest)
s[-1]
```




    't'




```python
# Alles außer dem letzten Buchstaben
s[:-1]
```




    'Hallo Wel'



Zusätzlich können wir den Index nutzen, um Elemente einer Sequenz in bestimmten Schrittgrößen auszuwählen (wobei 1 als Standard gesetzt ist). Das heißt weiter, dass wir zwei Doppelpunkte gefolgt von einer Zahl nutzen können, um die Frequenz zu bestimmen. Ein Beispiel:


```python
# Wähle alles, aber gehe in Schritten der Größe 1
s[::1]
```




    'Hallo Welt'




```python
# Wähle alles, aber gehe in Schritten der Größe 2
s[::2]
```




    'HloWl'




```python
# So können wir einen String rückwärts ausgeben
s[::-1]
```




    'tleW ollaH'



## String Eigenschaften

Es ist wichtig eine bestimmte Eigenschaft von Strings hervorzuheben: ihre Unveränderlichkeit. 

Das bedeutet, dass in einem String, sobald er erstellt wurde, die Elemente nicht geändert oder ersetzt werden können. Zum Beispiel:


```python
s
```




    'Hallo Welt'




```python
# Wir versuchen den ersten Buchstaben zu einem 'x' zu ändern
s[0]='x'
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-43-9c0f1465600a> in <module>()
          1 # Wir versuchen den ersten Buchstaben zu einem 'x' zu ändern
    ----> 2 s[0]='x'
    

    TypeError: 'str' object does not support item assignment


Beachtet, wie der Error uns genau sagt, was wir nicht tun konnten: die Zuordnung des Elements (en.: item assignment) ändern.

Etwas das wir tun können, ist dem String etwas anzuhängen.


```python
s
```




    'Hallo Welt'




```python
# Strings erweitern
s + ' erweitere mich!'
```




    'Hallo Welt erweitere mich!'




```python
# Wir können s jedoch komplett überschreiben
s = s + ' erweitere mich!'
```


```python
print(s)
```

    Hallo Welt erweitere mich!



```python
s
```




    'Hallo Welt erweitere mich!'



Und wir können das Multiplikationszeichen nutzen, um Wiederholungen zu erstellen.


```python
buchstabe = 'z'
```


```python
buchstabe*10
```




    'zzzzzzzzzz'



## Eingebaute grundlegende String Methoden

Objekte in Python haben üblicherweise eingebaute Methoden. Diese Methoden sind Funktionen innerhalb eines Objekts (wir werden später noch viel mehr darüber lernen), die Aktionen oder Kommandos am Objekt selbst ausführen.

Wir rufen diese Methoden durch einen Punkt und den Methodennamen auf. In folgender Form:

    Objekt.Methode(Parameter)

Dabei sind Parameter zusätzliche Argumente die wir der Methode auftragen können. Keine Sorge, falls das aktuell noch nicht 100% klar ist. Später werden wir unsere eigenen Objekte und Methoden erstellen!

Hier sind einige Beispiele eingebauter Methoden für Strings:


```python
s
```




    'Hallo Welt erweitere mich!'




```python
# String in Großbuchstaben
s.upper()
```




    'HALLO WELT ERWEITERE MICH!'




```python
# Kleinbuchstaben
s.lower()
```




    'hallo welt erweitere mich!'




```python
# Einen String bei den 
# Leerzeichen (das ist die Standardeinstellung) trennen
s.split()
```




    ['Hallo', 'Welt', 'erweitere', 'mich!']




```python
# Bei einem speziellen Element trennen
# (wobei das Element nicht enthalten bleibt)
s.split('W')
```




    ['Hallo ', 'elt erweitere mich!']



Es gibt viele weitere Methoden über die hinaus, die hier behandelt wurden. Wenn wir uns Fortgeschrittene Strings anschauen, lernen wir noch mehr davon.

## Print Formatierung

Wir können die .format() Methode benutzen, um formatierte Objekte zu ausgegebenen Strings hinzuzufügen.

Am leichtesten ist dies an einem Beispiel erklärt:


```python
'Fuegt einen weiteren String mit geschwungenen Klammern hinzu: {}'.format('Der eingefuegte String')
```




    'Fuegt einen weiteren String mit geschwungenen Klammern hinzu: Der eingefuegte String'



Wir werden der print Formatierung noch mehr Beachtung schenken, wenn wir in einer späteren Lektion an unseren Projekten arbeiten.

Im nächsten Kapitel beschäftigen wir uns mit: Listen.

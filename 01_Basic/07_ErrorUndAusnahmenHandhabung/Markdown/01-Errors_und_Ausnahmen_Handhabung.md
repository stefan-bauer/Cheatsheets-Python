# Errors und Ausnahmen Handhabung

Quelle:Datamics

## Hintergrund

Die Fehlersuche ist beim Coden von Programmen und Skripten einer der umfangreichsten Schritte. Manche Studien gehen von bis zu 50% aus. Deshalb ist es extrem wichtig, effektive Methoden zur Suche von Fehlern im Code zu kennen. 

Im Allgemeinen gibt es zwei wichtige unterschiedliche Arten von Fehlern.
* Syntaxfehler: Das sind beispielsweise Tippfehler wie ein vergessener `:` nach einem `if`. Das kann natürlich jedem mal passieren. Solche Fehler sind eher "kleine" Probleme. Meistens lassen sie sich schnell finden und beheben.
* Semantische Fehler: Das sind Fehler in der Logik des Programmes. Sie treten dann auf, wenn das Programm nicht das erledigt, was es soll. Das kann auch passieren, wenn syntaktisch alles korrekt ist. Um diese Fehler finden zu können ist es eine Voraussetzung, die Intention hinter dem Code zu kennen.

Innerhalb der *Semantischen Fehler* unterscheiden wir folgende zwei Kategorien:
* Fehler, die aus dem falschen Verständnis der Sprache herrühren. Zum Beispiel die falsche Verwendung der `range` Funktion.
* Fehler, die daher kommen, dass der Programmierer die Intention des Programms nicht verstanden hat bzw. diese nicht richtig umgesetzt hat

## Errors in Python

In dieser Lektion werden wir mehr über Errors und die Handhabung von Ausnahmen lernen! Und bis zu diesem Punkt im Kurs sind wir auch schon dem ein oder anderen Error begegnet. Zum Beispiel:


```python
print("Hello)
```


      File "<ipython-input-1-46b1df83c2e8>", line 1
        print("Helloi)
                      ^
    SyntaxError: EOL while scanning string literal



Seht, wir erhalten einen SyntaxError mit der weiteren Beschreibung, dass es sich um einen EOL (End of Line Error) beim Lesen des Strings handelt. Das ist spezifisch genug, um zu erkennen, dass wir ein Anführungszeichen am Ende des Strings vergessen haben. Diese unterschiedlichen Error Arten zu verstehen wird euch helfen, den Code viel schneller zu debuggen. Debuggen heißt erfolgreich, fehlerlos auszuführen.

Diese Art von Error und Beschreibung wird als Ausnahme (Exception) bezeichnet. Selbst wenn eine Anweisung oder ein Ausdruck syntaktisch korrekt ist, können Errors beim Ausführen auftauchen. Errors die beim Ausführen gefunden werden heißen Ausnahmen und sind nicht unbedingt fatal.

Ihr könnt alle vorgegebenen (built-in)  Ausnahmen [hier](https://docs.python.org/3/library/exceptions.html) nachlesen. Lasst uns jetzt lernen, wie wir mit Errors und Ausnahmen umgehen können.

## try und except

Die grundsätzliche Terminologie und Syntax, die in Python zum Umgang mit Errors verwendet wird, ist die <b>try</b> und <b>except</b> (versuchen und ausnahmen definieren) Anweisung. Der Code, der eine Ausnahme verursachen könnte, wird in den <i>try</i> Block geschrieben. Wie mit den Ausnahmen umgegangen werden soll wird in den <i>except</i> Blocks definiert. Die Syntax sieht folgendermaßen aus:

    try:
       Hier werden die Operationen ausgeführt...
       ...
    except AusnahmeI:
       Kommt es zu AusnahmeI, dann führe diesen Block aus.
    except AusnahmeII:
       Kommt es zu AusnahmeII, dann führe diesen Block aus.
       ...
    else:
       Gibt es keine Ausnahme, dann führe diesen Block aus.
       
Wir können außerdem auch auf alle Ausnahmen überprüfen, indem wir einfach nur `except` eingeben. Um das alles besser zu verstehen schauen wir uns jetzt ein Beispiel an:


```python
try:
    f = open('testdatei','w')
    f.write('Test schreibe dies')
except IOError:
    # Überprüft, ob es einen IOError gibt und führt in dem Fall die print Anweisung aus
   print("Error: Konnte Datei nicht finden oder schreiben")
else:
   print("Inhalt erfolgreich geschrieben")
   f.close()
```

    Inhalt erfolgreich geschrieben


Jetzt können wir schauen, was passiert, wenn wir die Datei ohne Schreiberlaubnis öffnen (nur mit 'r'):


```python
try:
    f = open('testdatei','r')
    f.write('Test schreibe dies')
except IOError:
    # Überprüft, ob es einen IOError gibt und führt in dem Fall die print Anweisung aus
   print("Error: Konnte Datei nicht finden oder schreiben")
else:
   print("Inhalt erfolgreich geschrieben")
   f.close()
```

    Error: Konnte Datei nicht finden oder schreiben


Toll! Seht wie wir nur eine print Anweisung ausgeführt haben. Der Code wurde trotzdem ausgeführt und wir waren in der Lage weitere Aktionen auszuführen. Das ist extrem nützlich, wenn man auf mögliche Input Errors im Code achten muss. So könnt ihr euch auf den Error vorbereiten und den Code weiterlaufen lassen, anstatt den Code abbrechen zu lassen, wie wir es oben gesehen haben.

Wir hätten außerdem auch einfach nur `except` schreiben können, wären wir uns über die Art der Ausnahme nicht sicher gewesen:


```python
try:
    f = open('testdatei','r')
    f.write('Test schreibe dies')
except:
    # Überprüft, ob es einen IOError gibt und führt in dem Fall die print Anweisung aus
   print("Error: Konnte Datei nicht finden oder schreiben")
else:
   print("Inhalt erfolgreich geschrieben")
   f.close()
```

    Error: Konnte Datei nicht finden oder schreiben


Gut! Denn das bedeutet, dass wir uns die Liste der Ausnahmen nicht merken müssen. Was wäre, wenn wir wollten, dass der Code nach der Ausnahme weiterläuft? Hier kommt <b>finally</b> ins Spiel.

## finally

Der `finally` Block im Code wird immer ausgeführt, unabhängig davon, ob eine Ausnahme festgestellt wurde oder nicht. Die Syntax lautet:

    try:
        Code Block hier
        ...
        Durch irgendeine Ausnahme könnte dieser Code übersprungen werden!
    finally:
        Dieser Code Block wird immer ausgeführt!
        
Ein Beispiel:


```python
try:
   f = open("testdatei", "w")
   f.write("Test schreibe dies")
finally:
   print("Führe diesen Code Block immer aus!")
```

    Führe diesen Code Block immer aus!


Wir können dies auch in Verbindung mit `except` nutzen. Lasst uns dazu ein neues Beispiel anschauen, dass darauf achtet, ob ein User falschen Input eingibt:


```python
def intfrage():
    try:
        val = int(input("Bitte gebe eine Zahl ein: "))
    except:
        print("Sieht aus, als ob du keine Zahl eingegeben hast!")
    finally:
        print("Aber immerhin wurde ich ausgeführt!")
    print(val)
```


```python
intfrage()
```

    Bitte gebe eine Zahl ein: 5
    Aber immerhin wurde ich ausgeführt!
    5



```python
intfrage()
```

    Bitte gebe eine Zahl ein: fünf
    Sieht aus, als ob du keine Zahl eingegeben hast!
    Aber immerhin wurde ich ausgeführt!



    ---------------------------------------------------------------------------

    UnboundLocalError                         Traceback (most recent call last)

    <ipython-input-11-c92cc9e7f0d9> in <module>()
    ----> 1 intfrage()
    

    <ipython-input-9-1e6e085460f3> in intfrage()
          6     finally:
          7         print("Aber immerhin wurde ich ausgeführt!")
    ----> 8     print(val)
    

    UnboundLocalError: local variable 'val' referenced before assignment


Wir erhalten hier trotzdem einen Error, wenn wir versuchen val auszugeben. Das liegt daran, dass es nie richtig zugewiesen wurde. Wir können einen weiteren Versuch implementieren:


```python
def intfrage():
    try:
        val = int(input("Bitte gebe eine Zahl ein: "))
    except:
        print("Sieht aus, als ob du keine Zahl eingegeben hast!")
        val = int(input("Bitte gebe eine Zahl ein: "))
    finally:
        print("Aber immerhin wurde ich ausgeführt!")
    print(val)
```


```python
intfrage()
```

    Bitte gebe eine Zahl ein: f
    Sieht aus, als ob du keine Zahl eingegeben hast!
    Bitte gebe eine Zahl ein: f
    Aber immerhin wurde ich ausgeführt!



    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-12-cbb9a584ec3a> in intfrage()
          2     try:
    ----> 3         val = int(input("Bitte gebe eine Zahl ein: "))
          4     except:


    ValueError: invalid literal for int() with base 10: 'f'

    
    During handling of the above exception, another exception occurred:


    ValueError                                Traceback (most recent call last)

    <ipython-input-13-c92cc9e7f0d9> in <module>()
    ----> 1 intfrage()
    

    <ipython-input-12-cbb9a584ec3a> in intfrage()
          4     except:
          5         print("Sieht aus, als ob du keine Zahl eingegeben hast!")
    ----> 6         val = int(input("Bitte gebe eine Zahl ein: "))
          7     finally:
          8         print("Aber immerhin wurde ich ausgeführt!")


    ValueError: invalid literal for int() with base 10: 'f'


Hmm...das hat jetzt nur genau einen weiteren Versuch gestattet. Wie können wir das kontinuierlich überprüfen? Indem wir eine while Schleife verwenden!


```python
def intfrage():
    while True:
        try:
            val = int(input("Bitte gebe eine Zahl ein: "))
        except:
            print("Sieht aus, als ob du keine Zahl eingegeben hast!")
            continue
        else:
            print("Ja, das ist eine Zahl!")
            break
        finally:
            print("Aber immerhin wurde ich ausgeführt!")
    print(val)
```


```python
intfrage()
```

    Bitte gebe eine Zahl ein: fünf
    Sieht aus, als ob du keine Zahl eingegeben hast!
    Aber immerhin wurde ich ausgeführt!
    Bitte gebe eine Zahl ein: vier
    Sieht aus, als ob du keine Zahl eingegeben hast!
    Aber immerhin wurde ich ausgeführt!
    Bitte gebe eine Zahl ein: drei
    Sieht aus, als ob du keine Zahl eingegeben hast!
    Aber immerhin wurde ich ausgeführt!
    Bitte gebe eine Zahl ein: 2
    Ja, das ist eine Zahl!
    Aber immerhin wurde ich ausgeführt!


Großartig! Jetzt wisst ihr, wie ihr mit Errors und Ausnahmen in Python umgehen könnt. Denkt immer an die try, except, else und finally Notation!

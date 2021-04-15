# if, elif und else Anweisungen

Quelle: Datamics


if Anweisungen erlauben uns in Python dem Computer aufzutragen alternative Aktionen in Abhängigkeit von bestimmten Ergebnissen durchzuführen.

Das können wir uns ungefähr so vereinfachen:

"Hey, wenn dieser Fall eintritt, dann mache etwas Bestimmtes."

Diese Idee können wir dann durch `elif` und `else` Anweisungen erweitern, welche uns folgendes ermöglichen:

"Hey, wenn dieser Fall eintritt (if), dann mache etwas Bestimmtes. Wenn ein anderer Fall eintritt (elif), dann mache etwas anderes Bestimmtes. Und sonst (else) - keiner der anderen Fälle trat ein - mache etwas anderes Bestimmtes."

Lasst uns die Syntax dafür betrachten: 

    if Fall 1:
        erste Aktion
    elif Fall 2:
        zweite Aktion
    else:
        dritte Aktion
        
Auch hier kommt das bereits bekannte Konzept der Blöcke durch Zeileneinzug ins Spiel. Die eingerückten Blöcke (hier Aktion 1 bis 3) werden nur ausgeführt, falls die vorherige Überprüfung logisch `true` (dt.: wahr) ist. 

## Erstes Beispiel

Lasst uns ein kurzes Beispiel betrachten:


```python
if True:
    print('Es war wahr!')
```

    Es war wahr!


## Halt! Was ist eigentlich "wahr"?


In Python wird eine Logik zu dieser Definition verwendet, die darauf aufbaut, `true` durch sein Gegenteil zu bestimmen. Das heißt, alles was nicht `false` ist, hat den Wert `true`. Wir brauchen also nur zu definieren, was "falsch", also `false` ist.

Als `false` gilt in Python:

* numerische Null-Werte(0, 0L, 0.0, 0.0+0.0j),
* der Boolean Wert `False`,
* leere Zeichenketten,
* leere Listen, 
* leere Tupel,
* leere Dictionaries,
* sowie der spezielle Wert None. 

Alle anderen Werte betrachtet Python als `true`. 

## else Logik

Eine else Logik hinzufügen:


```python
x = False

if x:
    print('X war wahr!')
else:
    print('Ich werde in jedem Fall ausgegeben, in dem x nicht wahr ist')
```

    Ich werde in jedem Fall ausgegeben, in dem x nicht wahr ist


## Mehrere Zweige

Wir können nun betrachten, wie weit uns if, elif und else bringen können!

Wir schreiben eine eingebettete Struktur. Achtet darauf, wie if, elif und else auf selber Höhe geschrieben sind. Das kann euch helfen, zu verstehen, welche if, elif und else zusammenhängen.

Wir nutzen jetzt die bereits bekannten Vergleichsoperatoren:


```python
loc = 'Bank'

if loc == 'Autohaus':
    print('Willkommen im Autohaus!')
elif loc == 'Bank':
    print('Willkommen in der Bank!')
else:
    print('Wo bist du?')
```

    Willkommen in der Bank!


Das funktioniert so, dass jedes Statement darauf überprüft wird, ob es True (wahr) ist. Sobald das der Fall ist, wird der eingebettete Code ausgeführt. Würde dieser Fall nicht eintreffen, würde das else Statement aktiviert werden. Dabei ist interessant, dass wir so viele elif Statements einbauen können wie wir möchten, bevor wir mit dem else Statement abschließen.

Lasst uns zwei weitere einfache Beispiele für die if, elif und else Anweisungen betrachten:


```python
person = 'Sammy'

if person == 'Sammy':
    print('Wilkommen Sammy!')
else:
    print("Willkommen, wie lautet dein Name?")
```

    Wilkommen Sammy!



```python
person = 'George'

if person == 'Sammy':
    print('Wilkommen Sammy!')
elif person == 'George':
    print('Wilkommen George!')
else:
    print("Willkommen, wie lautet dein Name?")
```

    Wilkommen George!


## Zeileneinzug

Es ist, wie bereits anfangs angedeutet, wichtig, immer auf den Einzug des Codes nach den Anweisungen zu achten. Dieser stellt die korrekte Reihenfolge und Ausführung des Codes sicher. Wir kommen später bei einem anderen Themen noch einmal darauf zurück.

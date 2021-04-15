# while Schleifen

Quelle: Datamics

Die `while` Anweisung in Python ist einer der allgemeinsten Wege, um Iteration durchzuführen. Eine while Anweisung wird so lange ein einzelnes bzw. eine Gruppe von Statements (also einen Codeblock) wiederholen, solange ihre Bedingung `true` (dt.: wahr) ist. Der Grund aus dem es 'Schleife' genannt wird ist, dass Anweisungen so lange wiederholt werden, bis ihre Bedingung nicht mehr erfüllt wird.

Die allgemeine Form einer while Schleife:

    while test:
        code statement
    else
        finales code statement
        
Wir können die `while` Schleife in Python außerdem dazu nutzen, um die "klassische" Schleifenform, die wir im vorherigen Kapitel angesprochen haben, nachzubauen. Hier noch einmal eine kurze Wiederholung der Schleifenform, wie sie bspw. in C verwendet wird:

    for(i = 1; i <= 10; i+)
       printf("i: %d\n", i);
        
In Python müssen wir die Zählvariable *i* vorab definieren und dann mit in den Codeblock der `while` Schleife nehmen, um die Funktionalität zu gewährleisten:

    i = 1
    while i < 10:
        print(i)
        i+=1
        
Etwas theoretischer betrachtet können wir sagen, es gibt insgesamt 3 Typen von Schleifen in Programmiersprachen:
1. Zähler-kontrollierte Schleifen - gibt es in Python nicht, können aber, wie im Beispiel gezeigt, mit einer `while` Schleife nachgebildet werden
2. Bedingungs-kontrollierte Schleifen - entsprechen in Python den `while` Schleifen
3. Sammlungs-kontrollierte Schleifen - entsprechen in Python den `for` Schleifen

Lasst und einige einfache Beispiele für `while` Schleifen in Python durchgehen:


```python
x = 0

while x < 10:
    print('x ist aktuell: ',x)
    print(' x ist immer noch kleiner als 10, 1 zu x hinzufügen')
    x+=1
```

    x ist aktuell:  0
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  1
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  2
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  3
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  4
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  5
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  6
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  7
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  8
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  9
     x ist immer noch kleiner als 10, 1 zu x hinzufügen


Schaut euch an, wir oft das print Statement ausgeführt wurde und wie die while Schleife so lange weiter gemacht hat, solange die Bedingung (x<10) erfüllt war. Soblad x==10 zutraf stoppte der Code. Folgendes Beispiel zeigt, wie wir ein else Statement einbauen könnten:


```python
x = 0

while x < 10:
    print('x ist aktuell: ',x)
    print(' x ist immer noch kleiner als 10, 1 zu x hinzufügen')
    x+=1
else:
    print('Fertig!')
```

    x ist aktuell:  0
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  1
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  2
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  3
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  4
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  5
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  6
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  7
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  8
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x ist aktuell:  9
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    Fertig!


## break, continue, pass

Wir können `break`, `continue` und `pass` Anweisungen in unseren Loops verwenden, um zusätzliche Funktionalität für verschiedenste Fälle einzubauen. Die drei Statements definieren sich folgendermaßen:
    
    break: Bricht aus dem aktuell nähesten umfassenden Loop aus.
    continue: Geht an den Anfang des nähesten umfassenden Loops.
    pass: Tut gar nichts.
    
Wenn wir über break und continue Anweisung nachdenken, sieht die allgemeine Form für while Loops wie folgt aus:

    while test:
        code statement
        if test:
            break
        if test:
            continue
    else:
    
break und continue Statements können überall innerhalb des Schleifen Bodys eigesetzt werden, wir nutzen sie aber üblicherweise in tieferen Ebenen in Kombination mit if Statements. 

Hier sind einige Beispiele:


```python
x = 0

while x < 10:
    print('x ist aktuell: ',x)
    print(' x ist immer noch kleiner als 10, 1 zu x hinzufügen')
    x+=1
    if x == 3:
        print('x==3')
    else:
        print('Fortsetzen...')
        continue
```

    x ist aktuell:  0
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    Fortsetzen...
    x ist aktuell:  1
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    Fortsetzen...
    x ist aktuell:  2
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    x==3
    x ist aktuell:  3
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    Fortsetzen...
    x ist aktuell:  4
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    Fortsetzen...
    x ist aktuell:  5
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    Fortsetzen...
    x ist aktuell:  6
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    Fortsetzen...
    x ist aktuell:  7
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    Fortsetzen...
    x ist aktuell:  8
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    Fortsetzen...
    x ist aktuell:  9
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    Fortsetzen...


Seht wie wir ein print Statement ausgeführt haben, sobald x == 3 war. Lasst uns nun ein break Statement einbauen, sobald x == 3 erfüllt ist:


```python
x = 0

while x < 10:
    print('x ist aktuell: ',x)
    print(' x ist immer noch kleiner als 10, 1 zu x hinzufügen')
    x+=1
    if x == 3:
        print('Bricht ab, da x==3')
        break
    else:
        print('Fortsetzen...')
        continue
```

    x ist aktuell:  0
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    Fortsetzen...
    x ist aktuell:  1
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    Fortsetzen...
    x ist aktuell:  2
     x ist immer noch kleiner als 10, 1 zu x hinzufügen
    Bricht ab, da x==3


Bemerkenswert hieran ist, dass der Code nun direkt endet, sobald break erreicht wird.

Nach diesen kurzen Beispielen solltet ihr euch mit while Schleifen wohl fühlen und sie guten Gewissens in eurem Code verwenden.

<b>Ein Wort der Warnung: Es ist möglich unendliche Schleifen mit while zu erstellen. Wie in folgendem Beispiel, das ihr bitte nicht ausführt:</b>


```python
# Führt diesen Code nicht aus!
while True:
    print('Oh Oh, unendlicher Loop')
```

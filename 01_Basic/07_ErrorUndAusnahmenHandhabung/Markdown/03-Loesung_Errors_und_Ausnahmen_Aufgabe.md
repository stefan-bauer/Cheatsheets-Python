# Errors und Ausnahmen Aufgabe

Quelle: Datamics

## Problem 1

Bearbeite die Ausnahme, die der folgende Code produziert, indem du try und except Blocks verwendest.


```python
try:
    for i in ['a','b','c']:
        print(i**2)
except:
    print("Ein Error trat auf!")
```

    Ein Error trat auf!


## Problem 2

Bearbeite die Ausnahme, die der folgende Code produziert, indem du try und except Blocks verwendest. Nutze dann einen finally Block, um auszugeben "Alles erledigt!".


```python
x = 5
y = 0
try:
    z = x/y
except ZeroDivisionError:
    print("Kann nicht durch Null teilen!")
finally:
    print("Alles erledigt!")
```

    Kann nicht durch Null teilen!
    Alles erledigt!


## Problem 3

Schreibe eine Funktion, die nach einer Ganzzahl fragt und deren Quadrat als Ergebnis ausgibt (print Anweisung). Nutze eine while Schleife mit try, except und else Block, um auf falsche Eingaben vorbereitet zu sein.


```python
def ask():
    
    while True:
        try:
            n = int(input('Eine Ganzzahl eingeben: '))
        except:
            print("Es trat ein Fehler auf. Bitte erneut versuchen!")
            continue
        else:
            break
            
        
    print ("Danke, deine Zahl zum Quadrat ist: ",n**2)
```


```python
ask()
```

    Eine Ganzzahl eingeben: null
    Es trat ein Fehler auf. Bitte erneut versuchen!
    Eine Ganzzahl eingeben: 8
    Danke, deine Zahl zum Quadrat ist:  64


## Gut gemacht!

# Errors und Ausnahmen Aufgabe

Quelle:Datamics

## Problem 1

Bearbeite die Ausnahme, die der folgende Code produziert, indem du try und except Blocks verwendest.


```python
for i in ['a','b','c']:
    print(i**2)
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-2-6ecccec123e7> in <module>()
          1 for i in ['a','b','c']:
    ----> 2     print(i**2)
    

    TypeError: unsupported operand type(s) for ** or pow(): 'str' and 'int'


## Problem 2

Bearbeite die Ausnahme, die der folgende Code produziert, indem du try und except Blocks verwendest. Nutze dann einen finally Block, um auszugeben "Alles erledigt!".


```python
x = 5
y = 0

z = x/y
```


    ---------------------------------------------------------------------------

    ZeroDivisionError                         Traceback (most recent call last)

    <ipython-input-3-3effb78be709> in <module>()
          2 y = 0
          3 
    ----> 4 z = x/y
    

    ZeroDivisionError: division by zero


## Problem 3

Schreibe eine Funktion, die nach einer Ganzzahl fragt und deren Quadrat als Ergebnis ausgibt (print Anweisung). Nutze eine while Schleife mit try, except und else Block, um auf falsche Eingaben vorbereitet zu sein.


```python
def ask():
    pass()
```


```python
ask()
```

## Gut gemacht!

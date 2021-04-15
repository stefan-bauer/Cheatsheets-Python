# Anweisungen Übung - Lösung

Quelle: Datamics

Lass uns dein Wissen überprüfen!

Nutze for, split() und if um eine Anweisung zu schreiben, die die Wörter ausgibt, die mit "s" beginnen:


```python
s = "Gebe nur solche Wörter in diesem Satz aus, die mit einem s starten."
```


```python
# Code hier
for word in s.split():
    if word[0] == 's' or word[0] == 'S':
        print(word)
```

    solche
    Satz
    s
    starten.


Nutze range(), um alle geraden Zahlen von 0 bis 10 auszugeben:


```python
# Code hier
range(0,11,2)
```




    range(0, 11, 2)



Nutze Listen Verständnis, um eine Liste zu erstellen, die alle Zahlen zwischen 1 und 50 enthält, die durch 3 teilbar sind.


```python
# Code hier
[x for x in range(1,50) if x%3 == 0]
```




    [3, 6, 9, 12, 15, 18, 21, 24, 27, 30, 33, 36, 39, 42, 45, 48]



Gehe durch den folgenden String durch und wenn ein Wort eine gerade Anzahl an Zeichen hat gebe "gerade!" aus:


```python
s = "Gebe alle Wörter dieses Satzes aus, die eine gerade Anzahl an Zeichen haben."
```


```python
# Code hier
for word in s.split():
    if len(word) % 2 == 0:
        print(word + "<-- gerade!")
```

    Gebe<-- gerade!
    alle<-- gerade!
    Wörter<-- gerade!
    dieses<-- gerade!
    Satzes<-- gerade!
    aus,<-- gerade!
    eine<-- gerade!
    gerade<-- gerade!
    Anzahl<-- gerade!
    an<-- gerade!
    haben.<-- gerade!


Schreibe ein Programm, das ganze Zahlen von 1 bis 100 ausgibt. Für Vielfache von 3 soll das Programm aber "Fizz" anstatt der Nummer schreiben, und für Vielfache der Zahl 5 soll "Buzz" geschrieben werden. Für Zahlen auf die beides zutrifft soll "FizzBuzz" geschrieben werden.


```python
# Code hier
for num in range(1,101):
    if num % 5 == 0 and num % 3 == 0:
        print("FizzBuzz")
    elif num % 3 == 0:
        print("Fizz")
    elif num % 5 == 0:
        print("Buzz")
    else:
        print(num)
```

    1
    2
    Fizz
    4
    Buzz
    Fizz
    7
    8
    Fizz
    Buzz
    11
    Fizz
    13
    14
    FizzBuzz
    16
    17
    Fizz
    19
    Buzz
    Fizz
    22
    23
    Fizz
    Buzz
    26
    Fizz
    28
    29
    FizzBuzz
    31
    32
    Fizz
    34
    Buzz
    Fizz
    37
    38
    Fizz
    Buzz
    41
    Fizz
    43
    44
    FizzBuzz
    46
    47
    Fizz
    49
    Buzz
    Fizz
    52
    53
    Fizz
    Buzz
    56
    Fizz
    58
    59
    FizzBuzz
    61
    62
    Fizz
    64
    Buzz
    Fizz
    67
    68
    Fizz
    Buzz
    71
    Fizz
    73
    74
    FizzBuzz
    76
    77
    Fizz
    79
    Buzz
    Fizz
    82
    83
    Fizz
    Buzz
    86
    Fizz
    88
    89
    FizzBuzz
    91
    92
    Fizz
    94
    Buzz
    Fizz
    97
    98
    Fizz
    Buzz


Nutze Listen Abstraktion, um eine Liste der ersten Buchstaben aller Wörter des folgenden Strings zu erstellen:


```python
s = "Erstelle eine Liste der ersten Buchstaben aller Wörter."
```


```python
# Code hier
[word[0] for word in s.split()]
```




    ['E', 'e', 'L', 'd', 'e', 'B', 'a', 'W']



## Gute Arbeit!

# Meilenstein Projekt 1: Schritt-für-Schritt Notebook

Quelle: Datamics

Hier findet ihr die Schritte, die euch den Weg zur Lösung weisen sollen:

**Schritt 1**: Schreibt eine Funktion, die das Spielfeld ausgeben kann. Setzt euer Spielfeld als Liste auf, deren Indizes 1-9 mit den Nummern auf dem Zahlenfeld korrespondieren. So erhaltet ihr ein 3 x 3 Feld.


```python
from IPython.display import clear_output
def spielfeld_anzeigen(spielfeld):
    
    pass
```

**Schritt 2**: Schreibe eine Funktion, die die Eingabe des Spielers aufnehmen kann und deren Markierung als 'X' oder 'O' zuweist. Ihr könntet bspw. eine while Schleife verwenden, um so lange zu fragen, bis eine korrekte Antwort gegeben wurde.

*Tipp*: Nutzereingaben kann man mit der Funktion `input()` abfragen. Mehr erfahrt ihr in der [Dokumentation](https://docs.python.org/3/library/functions.html#input).


```python
def spieler_eingabe():
    
    pass
```

**Schritt 3**: Schreibe eine Funktion, die im Spielfeld Listen Objekt eine Markierung ('X' oder 'O') und eine gewünschte Position (Nummer 1-9) nimmt, und sie dem Spielfeld zuweist.


```python
def markierung_setzen(spielfeld, markierung, position):
    
    pass
```

**Schritt 4**: Schreibt eine Funktion, die das Spielfeld und eine Markierung ('X' oder 'O') nimmt, und überprüft, ob diese Markierung gewonnen hat.


```python
def sieg_check(spielfeld, markierung):
    
    pass
```

**Schritt 5**: Schreibt eine Funktion, die das random Modul nutzt, um zufällig zu entscheiden, welcher Spieler beginnen darf. Ihr könntet dazu random.randint() nachschlagen. Gebt einen String aus, der anzeigt, welcher Spieler beginnen darf.


```python
import random
def beginner():
    
    pass
```

**Schritt 6**: Schreibt eine Funktion, die überprüft, ob eine Position frei ist und einen Boolean Wert ausgibt.


```python
def platz_check(spielfeld, position):
    
    pass
```

**Schritt 7**: Schreibt eine Funktion, die überprüft, ob das Spielfeld voll besetzt ist. Ist dies der Fall, soll True ausgegeben werden.


```python
def spielfeld_voll(spielfeld):
    
    pass
```

**Schritt 8**: Schreibt eine Funktion, die den Spieler nach seiner nächsten Position (Nummer 1-9) fragt. Dann soll die Funktion aus Schritt 6 genutzt werden, um zu kontrollieren, ob diese noch frei ist. Sofern sie frei ist, soll die Position für spätere Nutzung übergeben werden.


```python
def spieler_wahl(spielfeld):
    
    pass
```

**Schritt 9**: Schreibt eine Funktion, die die Spieler fragt, ob sie erneut spielen wollen. Tuen sie das, soll True übergeben werden.


```python
def neues_spiel():
    
    pass
```

**Schritt 10**: Jetzt kommt der schwierigste Teil. Nutzt while Schleifen und die Funktion, die ihr bereits erstellt habt, um das Spiel auszuführen!


```python
print("Willkommen bei Tic Tac Toe!")

# while True:
    # Spiel aufbauen
    # pass
    
    # while wird_gespielt:
        # Zug Spieler 1
        
        # Zug Spieler 2
        
            # pass
            
    # if not neues_spiel():
        # break
```

    Willkommen bei Tic Tac Toe!


## Gut gemacht!

# Meilenstein Projekt 1: Schritt-für-Schritt Notebook

Quelle: Datamics

Hier findet ihr die gelösten Schritte, um zu unserem fertigen Spiel zu gelangen.

**Schritt 1**: Schreibt eine Funktion, die das Spielfeld ausgeben kann. Setzt euer Spielfeld als Liste auf, deren Indizes 1-9 mit den Nummern auf dem Zahlenfeld korrespondieren. So erhaltet ihr ein 3 x 3 Feld.


```python
from IPython.display import clear_output
def spielfeld_anzeigen(spielfeld):
    
    clear_output()
    print('   |   |')
    print(' ' + spielfeld[7] + ' | ' + spielfeld[8] + ' | ' + spielfeld[9])
    print('   |   |')
    print('-----------')
    print('   |   |')
    print(' ' + spielfeld[4] + ' | ' + spielfeld[5] + ' | ' + spielfeld[6])
    print('   |   |')
    print('-----------')
    print('   |   |')
    print(' ' + spielfeld[1] + ' | ' + spielfeld[2] + ' | ' + spielfeld[3])
    print('   |   |')
```

**Schritt 2**: Schreibe eine Funktion, die die Eingabe des Spielers aufnehmen kann und deren Markierung als 'X' oder 'O' zuweist. Ihr könntet bspw. eine while Schleife verwenden, um so lange zu fragen, bis eine korrekte Antwort gegeben wurde.

*Tipp*: Nutzereingaben kann man mit der Funktion `input()` abfragen. Mehr erfahrt ihr in der [Dokumentation](https://docs.python.org/3/library/functions.html#input).


```python
def spieler_eingabe():
    
    markierung = ''
    while not (markierung == 'X' or markierung == 'O'):
        markierung = input('Spieler 1: Willst du X oder O sein?').upper()

    if markierung == 'X':
        return ('X', 'O')
    else:
        return ('O', 'X')
```

**Schritt 3**: Schreibe eine Funktion, die im Spielfeld Listen Objekt eine Markierung ('X' oder 'O') und eine gewünschte Position (Nummer 1-9) nimmt, und sie dem Spielfeld zuweist.


```python
def markierung_setzen(spielfeld, markierung, position):
    
    spielfeld[position] = markierung
```

**Schritt 4**: Schreibt eine Funktion, die das Spielfeld und eine Markierung ('X' oder 'O') nimmt, und überprüft, ob diese Markierung gewonnen hat.


```python
def sieg_check(spielfeld, markierung):
    
    return ((spielfeld[7] == markierung and spielfeld[8] == markierung and spielfeld[9] == markierung) or # oben
    (spielfeld[4] == markierung and spielfeld[5] == markierung and spielfeld[6] == markierung) or # mitte
    (spielfeld[1] == markierung and spielfeld[2] == markierung and spielfeld[3] == markierung) or # unten
    (spielfeld[7] == markierung and spielfeld[4] == markierung and spielfeld[1] == markierung) or # linke seite runter
    (spielfeld[8] == markierung and spielfeld[5] == markierung and spielfeld[2] == markierung) or # mitte runter
    (spielfeld[9] == markierung and spielfeld[6] == markierung and spielfeld[3] == markierung) or # rechte seite runter
    (spielfeld[7] == markierung and spielfeld[5] == markierung and spielfeld[3] == markierung) or # diagonal
    (spielfeld[9] == markierung and spielfeld[5] == markierung and spielfeld[1] == markierung)) # diagonal
```

**Schritt 5**: Schreibt eine Funktion, die das random Modul nutzt, um zufällig zu entscheiden, welcher Spieler beginnen darf. Ihr könntet dazu random.randint() nachschlagen. Gebt einen String aus, der anzeigt, welcher Spieler beginnen darf.


```python
import random
def beginner():
    if random.randint(0, 1) == 0:
        return 'Spieler 2'
    else:
        return 'Spieler 1'
```

**Schritt 6**: Schreibt eine Funktion, die überprüft, ob eine Position frei ist und einen Boolean Wert ausgibt.


```python
def platz_check(spielfeld, position):
    
    return spielfeld[position] == ' '
```

**Schritt 7**: Schreibt eine Funktion, die überprüft, ob das Spielfeld voll besetzt ist. Ist dies der Fall, soll True ausgegeben werden.


```python
def spielfeld_voll(spielfeld):
    for i in range(1,10):
        if platz_check(spielfeld, i):
            return False
    return True
```

**Schritt 8**: Schreibt eine Funktion, die den Spieler nach seiner nächsten Position (Nummer 1-9) fragt. Dann soll die Funktion aus Schritt 6 genutzt werden, um zu kontrollieren, ob diese noch frei ist. Sofern sie frei ist, soll die Position für spätere Nutzung übergeben werden.


```python
def spieler_wahl(spielfeld):
    # Wegen des Inputs nutzen wir Strings
    position = ' '
    while position not in '1 2 3 4 5 6 7 8 9'.split() or not platz_check(spielfeld, int(position)):
        
        position = input('Wähle deine nächste Position: (1-9) ')
    return int(position)
```

**Schritt 9**: Schreibt eine Funktion, die die Spieler fragt, ob sie erneut spielen wollen. Tuen sie das, soll True übergeben werden.


```python
def neues_spiel():
    return input('Wollt ihr erneut spielen? Gebt Ja oder Nein ein: ').lower().startswith('j')
```

**Schritt 10**: Jetzt kommt der schwierigste Teil. Nutzt while Schleifen und die Funktion, die ihr bereits erstellt habt, um das Spiel auszuführen!


```python
print("Willkommen bei Tic Tac Toe!")

while True:
    # Das Spielfeld zurücksetzen
    dasFeld = [' '] * 10
    spieler1_markierung, spieler2_markierung = spieler_eingabe()
    zug = beginner()
    print(zug + " darf beginnen.")
    spiel_laeuft = True
    
    while spiel_laeuft:
        if zug == "Spieler 1":
            # Zug von Spieler 1
            
            spielfeld_anzeigen(dasFeld)
            position = spieler_wahl(dasFeld)
            markierung_setzen(dasFeld, spieler1_markierung, position)
            
            if sieg_check(dasFeld, spieler1_markierung):
                spielfeld_anzeigen(dasFeld)
                print("Glückwunsch! Du hast gewonnen!")
                spiel_laeuft = False
            else:
                if spielfeld_voll(dasFeld):
                    spielfeld_anzeigen(dasFeld)
                    print("Dieses Spiel ist ein Unentschieden!")
                    break
                else:
                    zug = "Spieler 2"
        else:
            # Zug von Spieler 2
            
            spielfeld_anzeigen(dasFeld)
            position = spieler_wahl(dasFeld)
            markierung_setzen(dasFeld, spieler2_markierung, position)
            
            if sieg_check(dasFeld, spieler2_markierung):
                spielfeld_anzeigen(dasFeld)
                print("Glückwunsch! Du hast gewonnen!")
                spiel_laeuft = False
            else:
                if spielfeld_voll(dasFeld):
                    spielfeld_anzeigen(dasFeld)
                    print("Dieses Spiel ist ein Unentschieden!")
                    break
                else:
                    zug = "Spieler 1"
                    
    if not neues_spiel():
        break
```

## Gut gemacht!

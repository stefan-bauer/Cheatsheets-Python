# Tic Tac Toe

Quelle: Datamics

Das ist die fortgeschrittene Lösung für das 1. Meilenstein Projekt. Ein zwei Spieler Tic Tac Toe Spiel, erstellt mit einem Jupyter Notebook. Ladet dieses Notebook gerne herunter, um nachzuvollziehen, wie es funktioniert!

Zuerst ein Import und einige globale Variablen:


```python
# Speziell für die iPython Notebooks
from IPython.display import clear_output

# Globale Variablen
feld = [' '] * 10
status = True
auskunft = ""
```

Als nächstes eine Funktion, die das Spielfeld zurücksetzt. Wir nutzen eine Liste, um die Werte zu speichern.


```python
# Hinweis: Das Spiel wird Index 0 ignorieren
def spielfeld_reset():
    global feld, status
    feld = [' '] * 10
    status = True
```

Jetzt erstellen wir eine Funktion, die das Spielfeld anzeigt. Ich nutze das Zahlenfeld als Referenz.


```python
def feld_anzeigen():
    '''Diese Funktion zeigt das Spielfeld an, damit das Zahlenfeld als Referenz genutzt werden kann.'''
    # Aktuellen Zellen Output löschen
    clear_output()
    # Spielfeld anzeigen
    print("  "+feld[7]+" |"+feld[8]+" | "+feld[9]+" ")
    print("------------")
    print("  "+feld[4]+" |"+feld[5]+" | "+feld[6]+" ")
    print("------------")
    print("  "+feld[1]+" |"+feld[2]+" | "+feld[3]+" ")
```

Anschließend definiere ich eine Funktion, die überprüft, ob ein Sieg vorliegt:


```python
def sieg_check(feld, spieler):
    '''Überprüft horizontale, vertikale und diagonale Sieg-Kombinationen.'''
    if (feld[7]  ==  feld[8] ==  feld[9] == spieler) or \
        (feld[4] ==  feld[5] ==  feld[6] == spieler) or \
        (feld[1] ==  feld[2] ==  feld[3] == spieler) or \
        (feld[7] ==  feld[4] ==  feld[1] == spieler) or \
        (feld[8] ==  feld[5] ==  feld[2] == spieler) or \
        (feld[9] ==  feld[6] ==  feld[3] == spieler) or \
        (feld[1] ==  feld[5] ==  feld[9] == spieler) or \
        (feld[3] ==  feld[5] ==  feld[7] == spieler):
        return True
    else:
        return False
```

Eine Funktion, die überprüft ob das Feld schon komplett voll ist und ein Unentschieden vorliegt. Denkt daran, dass Index 0 immer Leer sein wird:


```python
def feld_voll(feld):
    '''Funktion, die überprüft, ob das Spielfeld voll ist'''
    if " " in feld[1:]:
        return False
    else:
        return True
```

Als nächstes stelle ich eine Funktion auf, um die Spielereingabe zu erhalten und einige Kontrollen durchzuführen:


```python
def spieler_fragen(markierung):
    '''Fragt den Spieler wo er X oder O platzieren möchte; überprüft Validität'''
    global feld
    frage = "Wähle wo dein " + markierung + " plaziert werden soll."
    while True:
        try:
            wahl = int(input(frage))
        except ValueError:
            print("Entschuldigung, bitte gebe eine Zahl zwischen 1 und 9 ein.")
            continue
            
        if wahl not in range(1,10):
            print("Entschuldigung, bitte gebe eine Zahl zwischen 1 und 9 ein.")
            continue
        
        if feld[wahl] == " ":
            feld[wahl] = markierung
            break
        else:
            print("Dieses Feld ist nicht frei!")
            continue
```

Nun folgt eine Funktion, die die Wahl des Spielers (per spieler_fragen Funktion) nimmt und den Spielstand ausgibt.


```python
def spieler_wahl(markierung):
    global feld, status, auskunft
    # Auskunft zurücksetzen
    auskunft = ""
    # Spieler Eingabe erhalten
    markierung = str(markierung)
    # Eingabe validieren
    spieler_fragen(markierung)
    
    # Sieg des Spielers überprüfen
    if sieg_check(feld,markierung):
        clear_output()
        feld_anzeigen()
        auskunft = markierung + " gewinnt! Glückwunsch!"
        status = False
        
    # Feld anzeigen
    clear_output()
    feld_anzeigen()
    
    # Unentschieden kontrollieren
    if feld_voll(feld):
        auskunft = "Unentschieden!"
        status = False
        
    return status, auskunft
```

Und zu guter Letzt alles zusammenbringen, um das Spiel zu spielen.


```python
def spiel_starten():
    spielfeld_reset()
    global auskunft
    
    # Markierungen festlegen
    X = "X"
    O = "O"
    while True:
        # Zeige Spielfeld
        clear_output()
        feld_anzeigen()
        
        # Zug Spieler X
        status, auskunft = spieler_wahl(X)
        print(auskunft)
        if status == False:
            break
            
        # Zug Spieler O
        status, auskunft = spieler_wahl(O)
        print(auskunft)
        if status == False:
            break
            
    # Die Spieler nach einem neuen Spiel fragen
    neues_spiel = input("Neues Spiel? j/n")
    if neues_spiel == "j":
        spiel_starten()
    else:
        print("Danke fürs Spielen!")
```

Los geht's!


```python
spiel_starten()
```

        |  |   
    ------------
        |  |   
    ------------
        |  |   


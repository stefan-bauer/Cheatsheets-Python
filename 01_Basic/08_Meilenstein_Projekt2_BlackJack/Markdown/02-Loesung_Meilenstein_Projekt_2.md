# Meilenstein Projekt 2 Lösung

Quelle: Datamics

Hier findet ihr unsere Lösung zu einer einfachen Version von BlackJack. Achtet auf die Nutzung von OOP und Klassen für die Karten und Hände.

Lasst uns damit beginnen einige globale Objekte für die Karten, Tupel und ein Dict zu definieren.


```python
# Zum Karten mischen genutzt
import random

# Boolean, die mitschreibt, ob die Hand gespielt wird
gespielt = False

chip_pool = 100

einsatz = 1

neustart_satz = "Drücke 's' um zu spielen oder drücke 'q' zum Beenden."
```


```python
# Herz, Karo, Kreuz Pik

farben = ("HE","KA","KR","PI")

# Mögliche Kartenhöhe

raenge = ('A', '2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K')

# Punkte Wert Dict (Achtung: Asse können auch 11 sein. Schaut euch für mehr Details self.ass an.)
karten_wert = {'A':1, '2':2, '3':3, '4':4, '5':5, '6':6, '7':7, '8':8, '9':9, '10':10, 'J':10, 'Q':10, 'K':10}
```

Jetzt erstelle ich eine Klasse für die Karten. Sie wird eine grundsätzliche ID Funktion haben und einige Funktionen, um die Farbe und den Rang der Karte zu ermitteln.


```python
# Eine Klasse für die Karten erstellen
class Karte:
    
    def __init__(self,farbe,rang):
        self.farbe = farbe
        self.rang = rang
        
    def __str__(self):
        return self.farbe + self.rang
    
    def karten_farbe(self):
        return self.farbe
    
    def karten_rang(self):
        return self.rang
    
    def ziehen(self):
        print(self.farbe + self.rang)
```

Als nächstes erstelle ich eine Klasse für die Hand. Sie wird Funktionen haben, um die Ass Situation zu berücksichtigen.


```python
# Eine Klasse für die Hand erstellen
class Hand:
    
    def __init__(self):
        self.karten = []
        self.wert = 0
        # Asse können 1 oder 11 sein. Wir müssen es hier definieren
        self.ass = False
        
    def __str__(self):
        '''Einen String der aktuellen Hand Zusammenstellung ausgeben'''
        hand_karten = ""
        
        # Ein besserer Weg das zu tun? Listen Verständnis
        for karte in self.karten:
            karten_name = karte.__str__()
            hand_karten += " " + karten_name
            
        return "Die Hand hat %s" %hand_karten
    
    def karte_ziehen(self,karte):
        '''Eine weitere Karte hinzufügen'''
        self.karten.append(karte)
        
        # Ass überprüfen
        if karte.rang == "A":
            self.ass = True
        self.wert += karten_wert[karte.rang]
        
    def kalk_wert(self):
        '''Den Wert der Hand berechnen. Gib Ass den Wert 11, wenn die Karten nicht abgelegt werden.'''

        if (self.ass == True and self.wert < 12):
            return self.wert + 10
        else:
            return self.wert
        
    def ziehen(self, verborgen):
        if verborgen == True and gespielt == True:
            # Zeige die erste verborgene Karte nicht
            start_karte = 1
        else:
            start_karte = 0
        for x in range(start_karte,len(self.karten)):
            self.karten[x].ziehen()
```

Jetzt erstelle ich noch eine Klasse für das Deck.


```python
class Deck:
    
    def __init__(self):
        '''Ein Deck in der Reihenfolge erstellen'''
        self.deck = []
        for farbe in farben:
            for rang in raenge:
                self.deck.append(Karte(farbe,rang))
                
    def mischen(self):
        '''Das Deck mischen, wofür Python eine Methode bietet.'''
        random.shuffle(self.deck)
        
    def austeilen(self):
        '''Das erste Element im Deck nehmen'''
        einzelne_karte = self.deck.pop()
        return einzelne_karte
    
    def __str__(self):
        deck_zsmstlg = ""
        for karte in self.karten:
            deck += " " + deck_zsmstlg.__str__()
            
        return "Das Deck hat" + deck_zsmstlg
```

Jetzt wo wir die Klassen erstellt haben, kommt der coole Teil: das tatsächliche Spiel!

Zunächst: Einen Einsatz machen. Überprüfen, ob der Einsatz eine Ganzzahl (Integer) ist.


```python
# Erster Einsatz

def einsatz_machen():
    '''Den Spieler nach seinem Einsatz fragen'''
    
    global einsatz
    einsatz = 0
    
    print("Wie viele Ihrer " + str(chip_pool) + " Chips möchten Sie setzen? (Ganzzahl eingeben)")
    
    # While Schleife, um bis zu erfolgreicher Eingabe weiter zu fragen
    while einsatz == 0:
        einsatz_zsmstlg = input() # Wir nutzen einsatz_zsmstlg als Überprüfer
        einsatz_zsmstlg = int(einsatz_zsmstlg)
        # Überprüfen, ob der Einsatz noch verfügbar ist
        if einsatz_zsmstlg >= 1 and einsatz_zsmstlg <= chip_pool:
            einsatz = einsatz_zsmstlg
        else:
            print("Ungültiger Einsatz, Sie haben nur " + str(chip_pool) + " übrig.")
```

Nun können wir eine Funktion erstellen, die das Spiel aufsetzt und Karten austeilt.


```python
def karten_austeilen():
    '''Diese Funktion teilt Karten aus und startet die Runde'''
    
    # Alle globalen Variablen einstellen
    global ergebnis, gespielt, deck, spieler_hand, dealer_hand, chip_pool, einsatz
    
    # Ein Deck erstellen
    deck = Deck()
    
    # Das Deck mischen
    deck.mischen()
    
    # Einen Einsatz machen
    einsatz_machen()
    
    # Spieler und Dealer Hand einrichten
    spieler_hand = Hand()
    dealer_hand = Hand()
    
    # Erste Karten austeilen
    spieler_hand.karte_ziehen(deck.austeilen())
    spieler_hand.karte_ziehen(deck.austeilen())
    
    dealer_hand.karte_ziehen(deck.austeilen())
    dealer_hand.karte_ziehen(deck.austeilen())
    
    ergebnis = "Halten oder nehmen? Drücke entweder h oder n!"
    
    if gespielt == True:
        print("Fold, Entschuldige")
        chip_pool -= einsatz
        
    # 
    gespielt = True
    spiel_schritt()
```

Jetzt erstelle ich die *nehmen* und *halten* Funktion.


```python
def nehmen():
    
    '''Den nehmen Button implementieren'''
    
    # Alle globalen Variablen einstellen
    global ergebnis, gespielt, deck, spieler_hand, dealer_hand, chip_pool, einsatz
    
    # Wenn Hand gespielt wird ziehe Karte
    if gespielt: 
        if spieler_hand.kalk_wert() <=21:
            spieler_hand.karte_ziehen(deck.austeilen())
            
        print("Spieler Hand ist %s" %spieler_hand)
        
        if spieler_hand.kalk_wert() > 21:
            ergebnis = "Verloren!" + neustart_satz
            
            chip_pool -= einsatz
            gespielt = False
            
        else:
            ergebnis = "Entschuldigung, kann nicht nehmen\n" + neustart_satz
            
        spiel_schritt()
```


```python
def halten():
    
    # Alle globalen Variablen einstellen
    global ergebnis, gespielt, deck, spieler_hand, dealer_hand, chip_pool, einsatz
    
    if gespielt == False:
        if spieler_hand.kalk_wert() > 0:
            ergebnis = "Sorry, du kannst nicht halten!"
            
    # Jetzt überprüfen wir alle anderen Regeln
    else:
        
        # Softe 17 Regel
        while dealer_hand.kalk_wert() < 17:
            dealer_hand.karte_ziehen(deck.austeilen())
        
        # Dealer überzieht
        if dealer_hand.kalk_wert() > 21:
            ergebnis = "Dealer hat überzogen! Du gewinnst!\n" + neustart_satz
            chip_pool += einsatz
            gespielt = False
        
        # Spieler hat bessere Hand als Dealer
        elif dealer_hand.kalk_wert() < spieler_hand.kalk_wert():
            ergebnis = "Du besiegst den Dealer, du gewinnst!\n" + neustart_satz
            chip_pool += einsatz
            gespielt = False
        
        # Unentschieden
        elif dealer_hand.kalk_wert() == spieler_hand.kalk_wert():
            ergebnis = "Unentschieden, weiter geht's" + neustart_satz
            gespielt = False
        
        # Dealer besiegt Spieler
        else:
            ergebnis = "Dealer gewinnt!" + neustart_satz
            chip_pool -= einsatz
            gespielt = False
        
    spiel_schritt()
```

Funktion, die das Ergebnis ausgibt und den Spieler nach dem nächsten Schritt fragt.


```python
def spiel_schritt():
    '''Funktion die den Spielschritt/Status ausgibt'''
    
    # Spieler Hand anzeigen
    print("")
    print("Die Hand des Spielers ist:"),
    spieler_hand.ziehen(verborgen = False)
    
    print("Die Hand des Spielers beträgt: " + str(spieler_hand.kalk_wert()))
    
    # Dealer Hand anzeigen
    print("Die Hand des Dealers ist:"),
    dealer_hand.ziehen(verborgen = True)
    
    # Wenn eine Spielrunde vorbei ist
    if gespielt == False:
        print("--- für ein Ergebnis von " + str(dealer_hand.kalk_wert() ))
        print("Chip Summe: " + str(chip_pool))
    # Andernfalls wissen wir die zweite Karte noch nicht
    else:
        print(" mit einer weiteren verdeckten Karte")
    
    # Gebe das Ergebnis von halten oder nehmen
    print(ergebnis)
    
    spieler_eingabe()
```

Funktion, um das Spiel zu beenden:


```python
def spiel_ende():
    print("Danke für's Spielen!")
    exit()
```

Funktion, die die Spielerhandlung abfragt:


```python
def spieler_eingabe():
    '''Lese die Eingabe des Nutzers'''
    spein = input().lower()
    
    if spein == "n":
        nehmen()
    elif spein == "h":
        halten()
    elif spein == "s":
        karten_austeilen()
    elif spein == "q":
        spiel_ende()
    else:
        print("Ungültige Eingabe... Gebe n,h,s oder q ein:")
        spieler_eingabe()
```

Kleines Intro zum Spiel:


```python
def intro():
    aussage = '''Willkommen zu BlackJack! Komme so nah wie möglich an 21, ohne drüber zu liegen!
    Dealer nehmen, bis sie 17 erreichen. Asse zählen als 1 oder 11. 
    '''
    print(aussage)
```

Jetzt können wir spielen!


```python
'''Der folgende Code wird das Spiel ausführen. Alle Code Zellen müssen zuvor ausgeführt werden!'''

# Ein Deck erstellenb
deck = Deck()
# Deck mischen
deck.mischen()
# Spieler und Dealer Hand erstellen
spieler_hand = Hand()
dealer_hand = Hand()
# Gebe das Intro aus
intro()
# Karten austeilen und Spiel starten
karten_austeilen()
```


```python

```

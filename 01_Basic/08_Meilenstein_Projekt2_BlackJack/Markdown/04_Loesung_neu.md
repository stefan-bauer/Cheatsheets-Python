# Meilenstein Projekt 2 - Lösung

Quelle: Datamics

In diesem Notebook wird unsere Lösung zum Meilensteinprojekt Blackjack vorgestellt. Unsere Lösung ist nur ein möglicher Lösungsansatz - deine Lösung wird vermutlich anders aussehen!

## Spielzug - Prozedur
Beim spielen einer Hand Blackjack müssen folgende Schritte vorgenommen werden:
1. Erzeuge ein Deck mit 52 Karten
2. Mische das Deck
3. Frage den Spieler nach seinem Einsatz
4. Stelle sicher, dass der Einsatz nicht den Chipstand eines Spielers überschreitet
5. Deale dem Spieler und dem Dealer (Computergegner) zwei Karten
6. Zeige nur eine Karte des Dealers, die andere bleibt verborgen
7. Zeige beide Karten des Spielers
8. Frage den Spieler, ob er nehmen oder halten möchte
9. Frage den Spieler, ob er eine weitere Karte nehmen möchte, falls der Spieler nicht über 21 gelangt ist
10. Spiele die Hand des Dealers, wenn der Spieler hält. Der Dealer nimmt solange Karten, bis sein Wert größer gleich 17 ist
11. Bestimme den Gewinner
12. Frage den Spieler, ob er erneut spielen möchte

## Spielkarten
Ein Satz Spielkarten hat insgesamt 52 Karten mit vier Farben (Herz, Karo, Pik und Kreuz) und dreizehn Rängen (zwei bis zehn sowie Bube, Dame, König und Ass) je Farbe. Buben, Damen und Könige haben alle den Rang 10. Asse haben den Rang 11 oder 1, je nachdem, was am nähesten unter 21 liegt (wenn möglich). Als Ausgangspunkt solltest du die Farben und Ränge in Variablen speichern, und dann die Ränge mit einem Dictionary in Werte konvertieren.

## Das Spiel
### Importe und globale Variablen
**Schritt 1: Kartenvariablen definieren**<br>
Importe das Modul random. Mit diesem werden die Karten vor jedem Austeilen gemischt. Speichere dann die Farben, Ränge und Werte der Karten in Variablen. Verwende dazu eigene oder die folgenden Datenstrukturen. Programmiere dann eine Kontrollvariable **spielend** mit einem bool'schen Wert. Dies ist ein gebräuchlicher Ansatz zur Kontrolle des Programmflusses.

    farben = ('Herz', 'Karo', 'Pik', 'Kreuz')
    raenge = ('Zwei', 'Drei', 'Vier', 'Fuenf', 'Sechs', 'Sieben', 'Acht', 'Neun', 'Zehn', 'Bube', 'Dame', 'Koenig', 'Ass')
    werte = {'Zwei':2, 'Drei':3, 'Vier':4, 'Fuenf':5, 'Sechs':6, 'Sieben':7, 'Acht':8, 'Neun':9, 'Zehn':10, 'Bube':10, Dame':10, 'Koenig':10, 'Ass':11}


```python
import random

farben = ('Herz', 'Karo', 'Pik', 'Kreuz')
raenge = ('Zwei', 'Drei', 'Vier', 'Fuenf', 'Sechs', 'Sieben', 'Acht', 'Neun', 'Zehn', 'Bube', 'Dame', 'Koenig', 'Ass')
werte = {'Zwei':2, 'Drei':3, 'Vier':4, 'Fuenf':5, 'Sechs':6, 'Sieben':7, 'Acht':8, 'Neun':9, 'Zehn':10, 'Bube':10,
         'Dame':10, 'Koenig':10, 'Ass':11}

spielend = True
```

### Klassen
Entwirf eine Klasse Karte, in der jedes Objekt Karte eine Farbe und einen Rang hat. Programmiere ausserdem eine Klasse Stapel, welche alle 52 Karte-Objekte enthält, und weiterhin eine Klasse Hand, welche die dem Spieler (oder Dealer) zugeteilten Karte-Objekte speichert.

**Schritt 2: Erzeuge eine Klasse Stapel**<br>
Ein Objekt Karte benötigt lediglich zwei Attribute: Farbe und Rang. Du könntest ein Attribut für Wert hinzufügen - in unserer Lösung behandeln wir den Wert später mit der Klasse Hand. <br>
Überlege dir, zusätzlich zu der \_\_init\_\_-Methode  der Klasse Karte eine \_\_str\_\_-Methode zu implementieren, die Farbe und Rang einer Karte in menschenlesbarer Form ausgibt, z.B. "Herz-Zwei".


```python
class Karte:

    def __init__(self, farbe, rang):
        self.farbe = farbe
        self.rang = rang
        
    def __str__(self):
        return self.farbe + '-' + self.rang
```

**Schritt 3: Erzeuge eine Klasse Stapel**<br>
In Stapel sollen alle 52 verschiedenen Kartenobjekte in einer Liste gespeichert und später dann gemischt werden. Dazu müssen alle 52 verschiedenen Kartenobjekte *instanziiert* und der Liste hinzugefügt werden. Dazu wird einfach in der \_\_init\_\_-Methode des Stapels mit Schleifen über alle möglichen Farb- und Rangkombinationen iteriert und dementsprechend Karte-Instanzen erzeugt. Die Schleife sieht also in etwa so aus:

    for farbe in farben:
        for rang in raenge:

Ausser der \_\_init\_\_-Methode brauchen wir Methoden zum mischen des Stapels und zum austeilen von Karten im Spiel. <br><br>
OPTIONAL: Es ist vielleicht nicht nötig, eine Methode zur Ausgabe des Stapels im Spiel zu entwicklen, allerdings kann es sehr bei der Suche nach Bugs und der Analyse des Programmes helfen. Hierzu könntest du der Klasse eine Methode \_\_str\_\_ hinzufügen.


```python
class Stapel:
    
    def __init__(self):
        self.stapel = []  # Beginne mit einer leeren Liste
        for farbe in farben:
            for rang in raenge:
                self.stapel.append(Karte(farbe, rang))  # Erzeuge Karte-Objekte und füge sie der Liste hinzu
    
    def __str__(self):
        stapel_gesamt = ''  # Beginne mit einem leeren String
        for karte in self.stapel:
            stapel_gesamt += '\n ' + karte.__str__() # Füge die print-Ausgabe jeder Karte hinzu
        return 'Der Stapel hat: ' + stapel_gesamt

    def mischen(self):
        random.shuffle(self.stapel)
        
    def austeilen(self):
        einzelkarte = self.stapel.pop()
        return einzelkarte
```

TEST: Lasst uns den Stapel ausgeben, um zu überprüfen, dass alles richtig implementiert wurde.


```python
test_stapel = Stapel()
print(test_stapel)
```

    Der Stapel hat: 
     Herz-Zwei
     Herz-Drei
     Herz-Vier
     Herz-Fuenf
     Herz-Sechs
     Herz-Sieben
     Herz-Acht
     Herz-Neun
     Herz-Zehn
     Herz-Bube
     Herz-Dame
     Herz-Koenig
     Herz-Ass
     Karo-Zwei
     Karo-Drei
     Karo-Vier
     Karo-Fuenf
     Karo-Sechs
     Karo-Sieben
     Karo-Acht
     Karo-Neun
     Karo-Zehn
     Karo-Bube
     Karo-Dame
     Karo-Koenig
     Karo-Ass
     Pik-Zwei
     Pik-Drei
     Pik-Vier
     Pik-Fuenf
     Pik-Sechs
     Pik-Sieben
     Pik-Acht
     Pik-Neun
     Pik-Zehn
     Pik-Bube
     Pik-Dame
     Pik-Koenig
     Pik-Ass
     Kreuz-Zwei
     Kreuz-Drei
     Kreuz-Vier
     Kreuz-Fuenf
     Kreuz-Sechs
     Kreuz-Sieben
     Kreuz-Acht
     Kreuz-Neun
     Kreuz-Zehn
     Kreuz-Bube
     Kreuz-Dame
     Kreuz-Koenig
     Kreuz-Ass


Super! Lasst uns nun die Klasse Hand implementieren.

**Schritt 4: Implementiere die Klasse Hand**<br>
Die Klasse Hand muss die an den Spieler ausgeteilten Karte-Objekte beinhalten und sollte ausserdem den Wert einer Hand berechnen können. Dabei muss der Spezialfall Ass beachtet werden, welches dem Wert 1 oder 11 entsprechen kann, je nachdem, was besser für den Spieler ist.


```python
class Hand:
    def __init__(self):
        self.karten = []  # Beginne wie in der Klasse Stapel mit einer leeren Liste
        self.wert = 0   # Beginne mit dem Wert 0
        self.asse = 0    # Variable zum speichern der Anzahl von Assen
    
    def karte_hinzufuegen(self, karte):
        self.karten.append(karte)
        self.wert += werte[karte.rang]
    
    def asse_einrechnen(self):
        pass
```

TEST: Lasst uns vor dem Implementieren der zwei möglichen Werte für ein Ass sicherstellen, dass wir der Hand des Spielers zwei Karten hinzufügen und ihren Wert berechnen können:


```python
test_stapel = Stapel()
test_stapel.mischen()
test_spieler = Hand()
test_spieler.karte_hinzufuegen(test_stapel.austeilen())
test_spieler.karte_hinzufuegen(test_stapel.austeilen())
test_spieler.wert
```




    15



Ausgabe der erzeugten Karten:


```python
for karte in test_spieler.karten:
    print(karte)
```

    Pik-Fuenf
    Kreuz-Bube


Super! Lasst uns jetzt die Asse angehen. Wenn ein Handwert 21 übersteigt, aber ein Ass enthält, können wir den Wert des Asses von 11 auf 1 reduzieren und fortfahren.


```python
class Hand:
    def __init__(self):
        self.karten = []  # Beginne wie in der Klasse Stapel mit einer leeren Liste
        self.wert = 0   # Beginne mit dem Wert 0
        self.asse = 0    # Variable zum speichern der Anzahl von Assen
    
    def karte_hinzufuegen(self, karte):
        self.karten.append(karte)
        self.wert += werte[karte.rang]
        
        if karte.rang == 'Ass':
            self.asse += 1  # Ass-Zähler erhöhen
    
    def asse_einrechnen(self):
        while self.wert > 21 and self.asse:
            self.wert -= 10
            self.asse -= 1 
```

Wir haben die Methode karte_hinzufuegen so erweitert, dass der Ass-Zähler self.asse für jedes Ass um 1 erhöht wird. Ausserdem haben wir die Methode asse_einrechnen implementiert, so dass für Asse 1 statt 11 gezählt wird, falls der Wert der Hand sonst über 21 liegt.

**Schritt 5: Implementiere eine Klasse Chips**<br>
Ausser dem Kartenstapel und der Handklasse brauchen wir noch eine Möglichkeit, den Chipstand der Spieler mitzutragen. Das könnte auch mit einer globalen Variablen gelöst werden, aber lasst uns für diese Aufgabe bei einer objektorientierten Implementation bleiben und eine Klasse Chips entwickeln!


```python
class Chips:
    
    def __init__(self):
        self.gesamt = 100  # 100 Chips als Standartwert
        self.wette = 0
        
    def wette_gewinnen(self):
        self.gesamt += self.wette
    
    def wette_verlieren(self):
        self.gesamt -= self.wette
```

HINWEIS ZUM STANDARTWERT:<br>
Alternativ könnte ein Standartwert als Parameter in der \_\_init\_\_ übergeben werden. Das würde es uns erlauben, den Standartwert bei der Erzeugung eines Chips-Objektes zu übergeben wie hier gezeigt:

    def __init__(self, gesamt=100):
        self.gesamt = gesamt
        self.wette = 0

Beide Ansätze sind korrekt, es ist nur davon abhängig, wie du die Spielparameter implementieren möchtest.

### Funktionsdefinitionen
Viele der Schritte sind repetitiv. Dabei können uns Funktionen helfen. Die folgenden Schritte sind nur eine Richtlinie - entferne oder ergänze Funktionen je nach Bedarf deines Programmes.

**Schritt 6: Schreibe eine Funktion zur Annahme von Wetten**<br>
Da wir den Nutzer nach einem Integerwert fragen, ist dies eine gute Gelegenheit zur Verwendung von  <code>try</code>/<code>except</code>. Bedenke, dass der Spieler nicht mehr als seinen Chipstand setzen kann!


```python
def wette_annehmen(chips):
    
    while True:
        try:
            chips.wette = int(input('Wie viele Chips möchtest du gerne setzen? '))
        except ValueError:
            print('Entschuldige, gib bitte einen Integerwert ein!')
        else:
            if chips.wette > chips.gesamt:
                print("Entschuldige, du kannst nicht mehr setzen als ", chips.gesamt)
            else:
                break
```

Wir verwenden hier eine <code>while</code>-Schleife, um den Spieler so lange um eine Eingabe zu bitten, bis diese sowohl Integer ist als auch höchstens der Anzahl verbleibender Chips entspricht. 

HINWEIS ZU FUNKTIONEN:<br>
Wenn wir von vorneherein wüßten, wie das Chips-Objekt des Spielers heisst, hätten wir obige Funktion auch so implementieren können:

    def wette_annehmen():
    
    while True:
        try:
            spieler_chips.wette = int(input('Wie viele Chips möchtest du gerne setzen? '))
        except ValueError:
            print('Entschuldige, gib bitte einen Integerwert ein!')
        else:
            if spieler_chips.wette > spieler_chips.gesamt:
                print("Entschuldige, du kannst nicht mehr setzen als ", spieler_chips.gesamt)
            else:
                break

In dem Fall würde die Funktion keinen Parameter benötigen. Das ist allerdings keine gute Idee! Allgemein sollten Funktionen möglichst unabhängig von externen Variablen etc. sein. In diesem Beispiel müsste die Funktion angepasst werden, wenn spieler_chips umbenannt wird.

**Schritt 7: Schreibe eine Funktion zum Nehmen weiterer Karten**<br>
Jeder Spieler kann Karten nehmen, bis 21 überschritten wird. Diese Funktion wird im Spiel immer dann aufgerufen, wenn ein Spieler eine Karte nehmen will, oder die Hand des Dealers unter 17 liegt. Sie sollte Stapel- und Handobjekte als Parameter annehmen, und eine Karte dem Stapel entnehmen und der Hand hinzufügen. Dabei müssen Asse wie oben beschrieben eingerechnet werden.


```python
def nehmen(stapel, hand):
    
    hand.karte_hinzufuegen(stapel.austeilen())
    hand.asse_einrechnen()
```

**Schritt 8: Schreibe eine Funktion, die erfragt, ob der Spieler eine weitere Karte nimmt**<br>
Diese Funktion sollte den Stapel und die Hand des Spielers als Parameter annehmen und eine globale Variable <code>spielend</code> zur Kontrolle des Spielflusses beinhalten.<br>
Wenn der Spieler nimmt, so ist obige <code>nehmen</code>-Funktion auszuführen. Nimmt der Spieler keine Karte, wird spielend auf False gesetzt - damit wird im weiteren Verlauf eine äußere <code>while</code>-Schleife kontrolliert.


```python
def nehmen_oder_halten(stapel, hand):
    global spielend  # Um eine äußere while-Schleife zu kontrollieren
    
    while True:
        x = input("Willst du nehmen oder halten? Gib 'n' oder 'h' ein ")
        
        if x[0].lower() == 'n':
            nehmen(stapel, hand)  # Vorher definierte Funktion nehmen()

        elif x[0].lower() == 'h':
            print("Spieler hält. Dealer spielt.")
            spielend = False

        else:
            print("Entschuldige, bitte versuche es erneut")
            continue
        break
```

**Schritt 9: Schreibe Funktionen zur Anzeige der Karten**<br>
Wenn das Spiel beginnt und jedes mal wenn der Spieler eine Karte nimmt, ist die erste Karte des Dealers verborgen und alle Karten des Spielers sichtbar. Nach der Hand werden alle Karten gezeigt, am besten zusammen mit dem Gesamtwert. Schreibe Funktionen für alle diese Szenarien.


```python
def zeige_teil(spieler, dealer):
    print("\nDealerhand:")
    print(" <verborgene Karte>")
    print('',dealer.karten[1])  
    print("\nSpielerhand:", *spieler.karten, sep='\n ')
    
def zeige_alle(spieler, dealer):
    print("\nDealerhand:", *dealer.karten, sep='\n ')
    print("Dealerhand =", dealer.wert)
    print("\nSpielerhand:", *spieler.karten, sep='\n ')
    print("PSpielerhand =", spieler.wert)
```

HINWEISE ZU DEN PRINT-STATEMENTS:<br>

* Der Sternoperator <code>*</code> entpackt die Liste .karten; mit dem <code>sep='\n '</code> werden diese dann zeilenweise ausgebeben.

* In der Zeile

      print('', dealer.karten[1])
    
    wird mit dem Leerstring ein bisschen Platz hinzugefügt.

- Hier verwenden wir Kommans zur Trennung der Ausgabe in einer Zeile. Wenn du die Strings lieber mit <code>+</code> verbinden möchtest, dann musst du die Methode \_\_str\_\_ der Karte-Objekte explizit ausführen, siehe

      print(' ' + dealer.karten[1].__str__())

**Schritt 10: Schreibe Funktionen, um das Spielende zu behandeln**<br>
Verwende nach Bedarf die Hand des Spielers, des Dealers und den Chipstand.


```python
def spieler_ueberschreitet(spieler, dealer, chips):
    print("Spieler überschreitet!")
    chips.wette_verlieren()

def spieler_gewinnt(spieler, dealer, chips):
    print("Spieler gewinnt!")
    chips.wette_gewinnen()

def dealer_ueberschreitet(spieler, dealer, chips):
    print("Dealer überschreitet!")
    chips.wette_gewinnen()
    
def dealer_gewinnt(spieler, dealer, chips):
    print("Dealer gewinnt!")
    chips.wette_verlieren()
    
def unentschieden(spieler, dealer):
    print("Dealer und Spieler haben den gleihen Wert, es ist ein unentschieden.")
```

### Und jetzt zum Spiel!!!


```python
while True:
    # Ausgabe einer Einleitung
    print('Wilkommen bei BlackJack! Komme so nahe wie möglich an 21, ohne den Wert zu überschreiten! Der Dealer nimmt, bis er 17 erreicht. Asse zählen als 1 oder 11.')
    
    # Create & shuffle the deck, deal two cards to each player
    # Erzeuge und mische den Stapel, gib jedem Spieler zwei Karten.
    stapel = Stapel()
    stapel.mischen()
    
    spieler_hand = Hand()
    spieler_hand.karte_hinzufuegen(stapel.austeilen())
    spieler_hand.karte_hinzufuegen(stapel.austeilen())
    
    dealer_hand = Hand()
    dealer_hand.karte_hinzufuegen(stapel.austeilen())
    dealer_hand.karte_hinzufuegen(stapel.austeilen())
            
    # Spieler-Chips erzeugen
    spieler_chips = Chips()  # Standartwert ist 100    
    
    # Frage den Spieler nach seinem Einsatz
    wette_annehmen(spieler_chips)
    
    # Zeige die Karten (ausser einer Karte des Dealers)
    zeige_teil(spieler_hand, dealer_hand)
    
    while spielend:  # Globale Variable aus der Funktion halten_oder_nehmen
        
        # Frage den Spieler, ob er nimmt oder hält
        nehmen_oder_halten(stapel, spieler_hand) 
        
        # Zeige die Karten (ausser einer Karte des Dealers)
        zeige_teil(spieler_hand, dealer_hand)  
        
        # Führe spieler_ueberschreitet aus und beende die Schleife, wenn der Spieler mehr als 21 hat
        if spieler_hand.wert > 21:
            spieler_ueberschreitet(spieler_hand, dealer_hand, spieler_chips)
            break        


    # Gib dem Dealer Karten, bis er 17 erreicht, falls der Spieler nicht überschritten hat
    if spieler_hand.wert <= 21:
        
        while dealer_hand.wert < 17:
            nehmen(stapel, dealer_hand)    
    
        # Zeige alle Karten
        zeige_alle(spieler_hand, dealer_hand)
        
        # Evaluiere Endszenarien
        if dealer_hand.wert > 21:
            dealer_ueberschreitet(spieler_hand, dealer_hand, spieler_chips)

        elif dealer_hand.wert > spieler_hand.wert:
            dealer_gewinnt(spieler_hand, dealer_hand, spieler_chips)

        elif dealer_hand.wert < spieler_hand.wert:
            spieler_gewinnt(spieler_hand, dealer_hand, spieler_chips)

        else:
            unentschieden(spieler_hand, dealer_hand)        
    
    # Zeige den Chipstand des Spielers an
    print("\nDie Anzahl von Chips des Spielers ist ", spieler_chips.gesamt)
    
    # Frage nach erneutem Spiel
    neues_spiel = input("Möchtest du eine weitere Runde spielen? Gib 'j' oder 'n' ein")
    
    if neues_spiel[0].lower()=='j':
        spielend=True
        continue
    else:
        print("Danke fürs spielen!")
        break
```

Und das war's! Bedenke, diese Schritte können signifikant von deiner eigenen Lösung abweichen. Das ist in Ordnung! Arbeite in den verschiedenen Abschnitten deines Programmes, bis du mit dem Ergebnis zufrieden bist. Das braucht viel Zeit und Geduld!
Wende dich bei Fragen und Kommentaren wie immer an unser Forum.

# Gut gemacht!

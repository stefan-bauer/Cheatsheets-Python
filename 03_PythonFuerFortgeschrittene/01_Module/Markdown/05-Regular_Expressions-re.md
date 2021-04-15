# Regular Expression

Quelle: Datamics

## Hintergrund

Der Begriff "*Regular Expression*" (dt.: Regulärer Ausdruck) stammt aus der Automatentheorie und der Theorie der formalen Sprachen. Das sind zwei Gebiete der theoretischen Informatik. In dieser dienen sie zur formalen Definition von Sprachfamilien mit bestimmten Eigenschaften, den sogenannten regulären Sprachen. 

## Regular Expression in Python

Regular Expressions sind in unserem Python Kontext zum Text passende Muster, die in einer formellen Syntax ausgedrückt sind. Ihr werdet sie häufig als 'regex' oder 'regexp' bezeichnet vorfinden, bspw. in Gesprächen. 

Regular Expressions können eine Vielzahl an Regeln beinhalten, vom Finden von Wiederholungen bis zu Text Übereinstimmung und vielem mehr. So wie ihr in Python fortschreitet werdet ihr feststellen, dass viele eurer Parsen Probleme mit Regular Expressions gelöst werden können. Sie werden auch gerne in Vorstellungsgesprächen thematisiert.

*Parsen ist der Vorgang mit dem Parser, der eine Software ist, die den Datenstrom eines Dokumentes analysiert und entsprechend der Syntax aufbereitet.*

Wenn ihr Perl kennt, dann werdet ihr feststellen, dass die Syntax der in Python sehr ähnlich ist. Wir werden das `re` Modul von Python in dieser Lektion nutzen. Es bietet eine Vielzahl an nützlichen Funktionen und Methoden zum Arbeiten mit regulären Ausdrücken bietet.

Lasst uns beginnen!

## Textmuster suchen

Eine der häufigsten Anwendungen des `re` Modul ist die Mustererkennung in Texten. Wir können uns ein schnelles Beispiel mit der `search` (dt.: suchen) Methode des `re` Modul anschauen:


```python
import re

# Liste mit Mustern die wir suchen
muster_liste = ["begriff1","begriff2"]

# Text zu parsen
text = "Das ist ein String mit begriff1, aber ohne den anderen Begriff."

for muster in muster_liste:
    print("Suche nach '%s' in: \n '%s'" %(muster,text))
    
    #Übereinstimmung prüfen
    if re.search(muster, text):
        print("\n")
        print("Übereinstimmung gefunden.")
    else:
        print("\n")
        print("Keine Übereinstimmung gefunden.")
```

    Suche nach 'begriff1' in: 
     'Das ist ein String mit begriff1, aber ohne den anderen Begriff.'
    
    
    Übereinstimmung gefunden.
    Suche nach 'begriff2' in: 
     'Das ist ein String mit begriff1, aber ohne den anderen Begriff.'
    
    
    Keine Übereinstimmung gefunden.


Wir haben gesehen, dass re.search() das Muster nimmt, im Text nach einer Übereinstimmung sucht und ein **Match** Objekt zurückgibt. Wenn keines der Muster gefunden wird, erhalten wir **None**. Um dieses Match Objekt zu verdeutlichen, hier noch eine weitere Zelle dazu:


```python
# Mustern das wir suchen
muster = "begriff1"
# Text zu parsen
text = "Das ist ein String mit begriff1, aber ohne den anderen Begriff."

match = re.search(muster, text)

type(match)
```




    _sre.SRE_Match



Dieses **Match** Objekt ist mehr als nur ein Boolean oder None. Es beinhaltet Information über die Übereinstimmung, einschließlich des originalen Input String, der Regular Expression, die genutzt wurde, und der Position, an der die Übereinstimmung gefunden wurde. Lasst uns die Methoden anschauen, die wir mit einem **Match** verwenden können:


```python
# Start der Übereinstimmung zeigen
match.start()
```




    23




```python
# Ende der Übereinstimmung zeigen
match.end()
```




    31



## Trennen mit Regular Expressions

Wir können den Text auch durch die re Syntax trennen. Das sollte ähnlich dazu aussehen, wie wir die split() Methode auf Strings angewendet haben.


```python
# Begriff, bei dem getrennt werden soll
trennbegriff = "@"

satz = "Wie lautet die Domain zu jemandem mit der Adresse: hallo@gmail.com"

# Den Satz trennen
re.split(trennbegriff, satz)
```




    ['Wie lautet die Domain zu jemandem mit der Adresse: hallo', 'gmail.com']



Achtet darauf, dass re.split() eine Liste ausgibt, die die getrennten Teile des Satzes beinhaltet. Ihr könnt euch selbst weitere Beispiele überlegen, um sicher zu gehen, dass ihr re.split() versteht.

## Alle Erscheinungen eines Musters finden

Ihr könnt re.findall() dazu verwenden, um alle Erscheinungen eines Musters in einem String zu finden. Ein Beispiel:


```python
# Gibt Liste aller Übereinstimmungen zurück
re.findall("Treffer","Test Satz mit Treffer in der Mitte")
```




    ['Treffer']



## re Syntax für Muster

Dieser Teil ist der größte dieser Lektion über den Umgang mit re in Python. Regular Expressions unterstützt eine viel größere Zahl von Mustern, als nur zu finden, wo ein String auftaucht. 

Wir können *Metazeichen* (metacharacters) in Verbindung mit re nutzen, um spezielle Arten von Mustern zu finden.

Da wir mehrere re Syntax Formen testen werden, sollten wir uns eine Funktion erstellen, die Ergebnisse ausgibt, die von einer Liste zahlreicher Regular Expressions und einem Satz zum Parsen abhängen:


```python
def multi_re_funde(muster_liste, satz):
    '''
    Nimmt eine Liste verschiedener regex Muster als Input.
    Gibt eine Liste aller Funde aus.
    ''' 
    
    for muster in muster_liste:
        print("Suche den Satz mit dem re check: %r" %muster)
        print(re.findall(muster, satz))
        print("\n")
```

### Wiederholungen Syntax

Es gibt 5 Wege. um Wiederholung in einem Muster auszudrücken:

1. Ein Muster gefolgt vom Metazeichen * ist 0 oder häufiger wiederholt.
2. Wenn wir * durch + ersetzen, dann muss das Muster mindestens einmal erscheinen.
3. Benutzen wir ? erscheint das Muster 0 oder 1 mal erscheinen.
4. Um eine bestimmte Anzahl von Erscheinungen zu spezifizieren nutzen wir {m}. m ersetzen wir dann durch die Anzahl mit der sich das Muster wiederholen soll.
5. Nutzt {m,n} um eine Mindest- (m) und Höchstanzahl (n) anzugeben. {m,} ohne n heißt, der Wert erscheint mindestens m mal, ohne Maximum.

Jetzt werden wir ein Beispiel für jeden dieser Wege sehen, indem wir unsere multi_re_funde Funktion benutzen:


```python
test_satz = "sdsd..sssddd...sdddsddd...dsds...dsssss...sdddd"

test_muster = [ 'sd*',      # s gefolgt von 0 oder mehr d's
                'sd+',      # s gefolgt von 1 oder mehr d's
                'sd?',      # s gefolgt von 0 oder 1 d's
                'sd{3}',    # s gefolgt von 3 d's
                'sd{2,3}',  # s gefolgt von 2 oder 3 d's
                ]

multi_re_funde(test_muster,test_satz)
```

    Suche den Satz mit dem re check: 'sd*'
    ['sd', 'sd', 's', 's', 'sddd', 'sddd', 'sddd', 'sd', 's', 's', 's', 's', 's', 's', 'sdddd']
    
    
    Suche den Satz mit dem re check: 'sd+'
    ['sd', 'sd', 'sddd', 'sddd', 'sddd', 'sd', 'sdddd']
    
    
    Suche den Satz mit dem re check: 'sd?'
    ['sd', 'sd', 's', 's', 'sd', 'sd', 'sd', 'sd', 's', 's', 's', 's', 's', 's', 'sd']
    
    
    Suche den Satz mit dem re check: 'sd{3}'
    ['sddd', 'sddd', 'sddd', 'sddd']
    
    
    Suche den Satz mit dem re check: 'sd{2,3}'
    ['sddd', 'sddd', 'sddd', 'sddd']
    
    


### Zeichen Sets

Zeichensets werden genutzt, wenn man einen Treffer für ein Zeichen aus einer Gruppe von Zeichen haben will. Klammern werden genutzt, um die Zeichen Set Inputs zu erstellen. Zum Beispiel: Der Input [ab] sucht für Erscheinungen von entweder a oder b. Einige Beispiele:


```python
test_satz = "sdsd..sssddd...sdddsddd...dsds...dsssss...sdddd"

test_muster = [ '[sd]',     # entweder s oder d
                's[sd]+']   # s gefolgt von 1 oder mehreren s oder d
                

multi_re_funde(test_muster,test_satz)
```

    Suche den Satz mit dem re check: '[sd]'
    ['s', 'd', 's', 'd', 's', 's', 's', 'd', 'd', 'd', 's', 'd', 'd', 'd', 's', 'd', 'd', 'd', 'd', 's', 'd', 's', 'd', 's', 's', 's', 's', 's', 's', 'd', 'd', 'd', 'd']
    
    
    Suche den Satz mit dem re check: 's[sd]+'
    ['sdsd', 'sssddd', 'sdddsddd', 'sds', 'sssss', 'sdddd']
    
    


Es ergibt Sinn, dass das erste [sd] alle Instanzen zurückgibt. Ebenso gibt der zweite Input einfach alles zurück, was in diesem speziellen Satz mit s beginnt.

### Ausschluss

Wir können ^ benutzen um Terme auszuschließen, indem wir es in die Klammer Syntax Notation eingeben. Zum Beispiel [^...] ergibt jedes Zeichen, dass nicht in der Klammer enthalten ist. Betrachten wir einige Beispiele:


```python
test_satz = "Das ist ein String! Aber er beinhaltet Zeichensetzung. Wie können wir sie entfernen?"
```

Nutzt [^!.? ], um nach Treffern zu suchen, die weder !, noch ., noch ? oder Leerzeichen sind. Fügt ein + hinzu, um zu definieren, dass die Funde mindestens einmal erscheinen sollen. So erhalten wir die Wörter, statt nur die Zeichen.


```python
re.findall("[^!.? ]+",test_satz)
```




    ['Das',
     'ist',
     'ein',
     'String',
     'Aber',
     'er',
     'beinhaltet',
     'Zeichensetzung',
     'Wie',
     'können',
     'wir',
     'sie',
     'entfernen']



### Zeichen Bereiche

Wenn die Zeichen Sets größer werden, dann wird es mühsam jedes Zeichen, das erscheinen soll (oder nicht), zu tippen. Eine kompaktere Form ist die Verwendung von Zeichen Bereichen, die uns ein Start- und Endzeichen festlegen lassen. Alle fortlaufenden Zeichen dazwischen werden miteingeschlossen. Das Format ist [Start-Ende].

Ein Anwendungsfall könnte zum Beispiel die Suche nach bestimmten Zeichen aus dem Alphabet sein, beispielsweise [a-f]. Wir erhielten alle Treffer mit Buchstaben zwischen a und f als Ergebnis.

Schauen wir uns einige Beispiele an:


```python
test_satz = "Das ist ein beispielhafter Satz. Lasst uns schauen, ob wir einige Buchstaben finden."

test_muster = [ '[a-z]+',      # Sequenz der Kleinbuchstaben
                '[A-Z]+',      # Sequenz der Großbuchstaben
                '[a-zA-Z]+',   # Sequenz von Klein- oder Großbuchstaben
                '[A-Z][a-z]+'] # Ein Großbuchstabe, gefolgt von einem Kleinbuchstabe
                
multi_re_funde(test_muster,test_satz)
```

    Suche den Satz mit dem re check: '[a-z]+'
    ['as', 'ist', 'ein', 'beispielhafter', 'atz', 'asst', 'uns', 'schauen', 'ob', 'wir', 'einige', 'uchstaben', 'finden']
    
    
    Suche den Satz mit dem re check: '[A-Z]+'
    ['D', 'S', 'L', 'B']
    
    
    Suche den Satz mit dem re check: '[a-zA-Z]+'
    ['Das', 'ist', 'ein', 'beispielhafter', 'Satz', 'Lasst', 'uns', 'schauen', 'ob', 'wir', 'einige', 'Buchstaben', 'finden']
    
    
    Suche den Satz mit dem re check: '[A-Z][a-z]+'
    ['Das', 'Satz', 'Lasst', 'Buchstaben']
    
    


### Escape Codes

Wir können diese speziellen Escape Codes (dt.: Ausbruch Codes) nutzen, um spezielle Arten von Mustern in unseren Daten zu finden. Dazu gehören Ziffer, Leerzeichen und mehr. Einige Beispiele:

<table border="1" class="docutils">
<colgroup>
<col width="14%" />
<col width="86%" />
</colgroup>
<thead valign="bottom">
<tr class="row-odd"><th class="head">Code</th>
<th class="head">Bedeutung</th>
</tr>
</thead>
<tbody valign="top">
<tr class="row-even"><td><tt class="docutils literal"><span class="pre">\d</span></tt></td>
<td>Eine Ziffer</td>
</tr>
<tr class="row-odd"><td><tt class="docutils literal"><span class="pre">\D</span></tt></td>
<td>Eine Nicht-Ziffer</td>
</tr>
<tr class="row-even"><td><tt class="docutils literal"><span class="pre">\s</span></tt></td>
<td>Leetzeichen (Tab, Leerzeichen, neue Zeile, etc.)</td>
</tr>
<tr class="row-odd"><td><tt class="docutils literal"><span class="pre">\S</span></tt></td>
<td>Nicht-Leerzeichen</td>
</tr>
<tr class="row-even"><td><tt class="docutils literal"><span class="pre">\w</span></tt></td>
<td>Alphanumerisch</td>
</tr>
<tr class="row-odd"><td><tt class="docutils literal"><span class="pre">\W</span></tt></td>
<td>Nicht-Alphanumerisch</td>
</tr>
</tbody>
</table>

Escapes werden durch einen Backslash angezeigt. Unglücklicherweise müssen Backslashs in normalen Python Strings selbst auch ausgebrochen (escaped) werden. Das würde unleserliche Ausdrücke zur Folge haben. Durch die Nutzung von rohen (row) Strings, erstellt durch das Präfix r, für Regular Expressions können wir dieses Problem umgehen und die Leserlichkeit aufrechterhalten.

Persönlich denke ich, dass es genau diese Nutzung von r, um den Backslash auszubrechen, ist, die Leute, die regex in Python nicht kennen, davon abhält, den Code zu verstehen. Hoffentlich wird das alles klarer, nachdem wir den nächsten Code betrachtet haben.


```python
test_satz = "Das ist ein String mit einigen Ziffern 1234 und einem Symbol #Hastag"

test_muster = [ r'\d+', # Sequenz von Ziffern
                r'\D+', # Sequenz von Nicht-Ziffern
                r'\s+', # Sequenz von Leerzeichen
                r'\S+', # Sequenz von Nicht-Leerzeichen
                r'\w+', # Alphanumerische Zeichen
                r'\W+', # Nicht-Alphanumerische Zeichen
                ]

multi_re_funde(test_muster,test_satz)
```

    Suche den Satz mit dem re check: '\\d+'
    ['1234']
    
    
    Suche den Satz mit dem re check: '\\D+'
    ['Das ist ein String mit einigen Ziffern ', ' und einem Symbol #Hastag']
    
    
    Suche den Satz mit dem re check: '\\s+'
    [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ']
    
    
    Suche den Satz mit dem re check: '\\S+'
    ['Das', 'ist', 'ein', 'String', 'mit', 'einigen', 'Ziffern', '1234', 'und', 'einem', 'Symbol', '#Hastag']
    
    
    Suche den Satz mit dem re check: '\\w+'
    ['Das', 'ist', 'ein', 'String', 'mit', 'einigen', 'Ziffern', '1234', 'und', 'einem', 'Symbol', 'Hastag']
    
    
    Suche den Satz mit dem re check: '\\W+'
    [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' #']
    
    


## Schlusswort

Durch diese Lektion solltet ihr ein solides Verständnis dafür erhalten haben, wie man Regular Expressions nutzt. Anstatt alle einzelnen der unzähligen Fälle durchzugehen könnt ihr in die [Dokumentation](https://docs.python.org/3/howto/regex.html) schauen.

Gut gemacht!

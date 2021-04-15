# Fortgeschrittene Strings

Quelle: Datamics

String Objekte bieten eine Vielzahl an Methoden, die uns Zeit sparen und Funktionalität erhöhen. In dieser Lektion werden wir einige davon ausprobieren:


```python
s = "hallo Welt"
```

## Groß-/Kleinschreibung

Wir können Methoden nutzen, um den ersten Buchstaben groß zu schreiben oder alle Wörter eines Strings klein bzw. groß zu schreiben.


```python
# Den ersten Buchstaben eines Strings groß schreiben
s.capitalize()
```




    'Hallo welt'




```python
s.upper()
```




    'HALLO WELT'




```python
s.lower()
```




    'hallo welt'



## Platzierung und Zählung


```python
s.count('o')
```




    1




```python
s.find('o')
```




    4



## Formatierung

Die center() Methode erlaubt es uns, unseren String in der Mitte innerhalb eines Strings mit einer bestimmten Länge zu platzieren. Aber um ehrlich zu sein, kam diese Methode in keiner meiner Codes zum Einsatz.


```python
s.center(20,'z')
```




    'zzzzzHallo Weltzzzzz'




```python
# expandtabs() wandelt Tab Notation \t in Leerzeichen
'hallo\thi'.expandtabs()
```




    'hallo   hi'



## is Check Methoden

Diese folgenden Methoden überprüfen, ob der String bestimmte Bedingungen erfüllt. Schauen wir sie uns an:


```python
s = 'Hallo'
```

isalnum() gibt True (wahr) aus, wenn alle Zeichen im String alphanumerisch sind.


```python
s.isalnum()
```




    True



isalpha() gibt True zurück, falls alle Zeichen im String dem Alphabet zugehörig sind.


```python
s.isalpha()
```




    True



islower() gibt True aus, falls alle Zeichen im String klein geschrieben sind. Andernfalls erhalten wir False.


```python
s.islower()
```




    False



Um zu überprüfen ob alle Zeichen eines Strings Leerzeichen sind, verwendet man isspace().


```python
s.isspace()
```




    False



istitle() ergibt True, wenn ein String groß- und kleingeschrieben ist wie ein Titel.


```python
s.istitle()
```




    True



isupper() gibt True aus, falls alle Zeichen im String groß geschrieben sind. Andernfalls erhalten wir False.


```python
s.isupper()
```




    False



Eine weitere Methode ist endswith(), was im Endeffekt eine Boolean Überprüfung von s[-1] ist.


```python
s.endswith('o')
```




    True



## Vorinstallierte Regular Expression

Strings haben einige vorinstallierte Methoden, die Regular Expression Operationen wiederspiegeln können. Wir könne split() benutzen, um den String bei einem bestimmten Element zu trennen und das Ergebnis in einer Liste auszugeben.

Wir können außerdem partition() benutzen, um ein Tupel zu erzeugen, das den Teiler (erste Erscheinung) sowie die vordere und hintere Hälfte beinhaltet.


```python
s.split('a')
```




    ['H', 'llo']




```python
s.partition('l')
```




    ('Ha', 'l', 'lo')




```python
s
```




    'Hallo'



Wunderbar! Ihr solltet euch jetzt wohl fühlen im Umgang der zahlreichen vorinstallierten String Methoden in Python!

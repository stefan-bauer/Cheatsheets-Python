# Python 2.7.x vs. Python 3.x

Quelle: Datamics

In dieser Bonuslektion möchten wir auf die wichtigsten Unterschiede zwischen den Python Versionen 2.7.x und 3.x eingehen. Wir werden insgesamt folgende Unterkapitel behandeln:

1. Das __future__ Modul
2. Die print Funktion
3. Integer Division
4. xrange
5. Ausnahmen erzeugen
6. Ausnahmen handhaben
7. Die next() Funktion und die .next() Methode
8. For-Schleifen Variablen und das globale Namensbereich Leck
9. User-Inputs via input() verarbeiten
10. Iterierbare Objekte statt Listen zurückgeben
11. Banker Rundungen

*Notiz zur Ausführung: Da wir aktuell in einer Python 3 Umgebung arbeiten, können nicht alle Ergebnisse durch Ausführen des Codes erzeugt werden. Wir haben sie in den Kommentaren (#) hinterlegt.* 

## 1. Das __future__ Modul

Python 3.x führte einige Python 2 inkompatible Stichworte und Features ein. Sie können durch das `__future__` Modul in Python 2 importiert werden. Das `__future__` Modul zu nutzen wird immer dan empfohlen, wenn Python 3.x Support für euren Python 2 Code vorgesehen ist. Ein Beispiel:


```python
from __future__ import division
```

Mehr Features, die durch `__future__` importiert werden können sehr ihr in dieser Tabelle:

<table class="table table-bordered">
<tr>
<th style="width:30%">Feature</th>
<th style="width:20%">Optional in</th>
<th style="width:20%">Erfordert in</th>
<th>Effekt</th>
</tr>
<tr>
<td>nested_scopes</td>
<td>2.1.0b1</td>
<td>2.2</td>
<td>[PEP 227](https://www.python.org/dev/peps/pep-0227/)</td>
</tr>
<tr>
<td>gernerators</td>
<td>2.2.0a1</td>
<td>2.3</td>
<td>[PEP 255](https://www.python.org/dev/peps/pep-0255/)</td>
</tr>
<tr>
<td>division</td>
<td>2.2.0a2</td>
<td>3.0</td>
<td>[PEP 238](https://www.python.org/dev/peps/pep-0238/)</td>
</tr>
<tr>
<td>absolute_import</td>
<td>2.5.0a1</td>
<td>3.0</td>
<td>[PEP 328](https://www.python.org/dev/peps/pep-0328/)</td>
</tr>
<tr>
<td>with_statement</td>
<td>2.5.0a1</td>
<td>2.6</td>
<td>[PEP 343](https://www.python.org/dev/peps/pep-0343/)</td>
</tr>
<tr>
<td>print_function</td>
<td>2.6.0a2</td>
<td>3.0</td>
<td>[PEP 3105](https://www.python.org/dev/peps/pep-3105/)</td>
</tr>
<tr>
<td>unicode_literals</td>
<td>2.6.0a2</td>
<td>3.0</td>
<td>[PEP 3112](https://www.python.org/dev/peps/pep-3112/)</td>
</tr>
</table>

## 2. Die print Funktion

Eine relativ triviale Änderung, die gleichzeitig die vermutlich bekannteste ist: die `print` Funktion. Die print Anweisung aus Python 2 wurde durch die print() Funktion ersetzt. 

Die Abwärtskompatibilität ist insofern gewährleistet, als dass Python 2 kein Problem mit zusätzlichen Klammern hat. Python 3 hingegen würde einen `SyntaxError` ausgeben, wenn wir unsere Anweisung in der Python 2 Schreibweise erteilen. 

### Python 2


```python
print "Python"
print "Hallo, Welt!"
print("Hallo, Welt!")
```

### Python 3


```python
print("Python")
print("Hallo, Welt!")
print("Klammern sind in Python 3 ein Muss!")
```

## 3. Integer Division

An dieser Stelle ist besondere Vorsicht geboten, sollte man Code von Python 2 zu 3 übertragen. Oder, wenn man Python 3 Code in Python 2 ausführt. Das rührt daher, dass die Umstellung der Integer Division keinen `Syntaxerror` erzeugt. 

Python 3 führt *echte Division* durch, wohingegen Python 2 *klassische Division* nutzt. Der Unterschied liegt darin, dass bei klassischer Division keine Nachkommastellen berücksichtigt werden. Es gibt einen *Rest*.

Um Probleme in Python 2 zu vermeiden, kann man auch in Python 3 dabei bleiben `float(3)/2` oder `3/2.0` zu schreiben. Und in Python 2 bietet es sich an, folgenden Code einzubauen: 

    from __future__ import division

### Python 2


```python
3/2          # = 1
3.0/2        # = 1.5
float(3)/2   # = 1.5
```

### Python 3


```python
3/2          # = 1.5
3.0/2        # = 1.5
float(3)/2   # = 1.5
```

## 4. xrange

Die Benutzung von `xrange()` ist in Python 2.x sehr verbreitet, um ein iterierbares Objekt bspw. in einer for-Schleife oder einer Listen Abstraktion zu erstellen. Das Verhalten von xrange ähnelte dem eines Generators stark, wobei die Iteration nicht endlich war. D.h. wir konnten über ein solches Objekt unendlich oft iterieren. 

In Python 3 wurde die `range()` Funktion direkt wie `xrange()` (aus Python 2) implementiert. Eine explizite `xrange()` Funktion existiert nicht mehr und deren Aufruf würde zu einem `NameError` führen.


```python
import timeit

n = 10000
def test_range(n):
    for i in range(n):
        pass

def test_xrange(n):
    for i in xrange(n):
        pass
```

### Python 2


```python
print 'Zeit messen für range()'
%timeit test_range(n)

print '\nZeit messen für xrange()'
%timeit test_xrange(n)

# Zeit messen für range()
# 1000 loops, best of 3: 433 µs per loop
# Zeit messen für xrange()
# 1000 loops, best of 3: 350 µs per loop
```

### Python 3


```python
print 'Zeit messen für range()'
%timeit test_range(n)

print '\nZeit messen für xrange()'
%timeit test_xrange(n)

# Zeit messen für range()
# 1000 loops, best of 3: 520 µs per loop
# NameError: name 'xrange' is not defined
```

## 5. Ausnahmen erzeugen

Wo Python 2 noch die "alte" und "neue" Syntax zum Erzeugen einer Ausnahme erlaubt hat, können wir in Python 3 lediglich die "neue" verwenden.

### Python 2


```python
raise IOError, "file error"  # IOError: file error
raise IOError("file error")  # IOError: file error
```

### Python 3


```python
raise IOError, "file error"  # invalid syntax
raise IOError("file error")  # IOError: file error
```

## 6. Ausnahmen handhaben

Neben dem Erzeugen von Ausnahmen gab es auch Änderungen an der Handhabung von ihnen. Wir müssen in Python 3 das "as" Stichwort benutzen.

### Python 2


```python
try:
    lasst_uns_einen_NameError_erzeugen
except NameError, err:
    print err, "--> Unsere Error Meldung"
    
# name 'lasst_uns_einen_NameError_erzeugen' is not defined ---> Unsere Error Meldung
```

### Python 3


```python
try:
    lasst_uns_einen_NameError_erzeugen
except NameError as err:
    print err, "--> Unsere Error Meldung"
    
# name 'lasst_uns_einen_NameError_erzeugen' is not defined ---> Unsere Error Meldung
```

## 7. Die next() Funktion und die .next() Methode

Da die `next()` (`.next()`) Funktion (Methode) so häufig verwendet werden, möchten wir auch hier auf die Änderung eingehen: In Python 2 konnte man beides nutzen, um das nächste Element eines Iterierbaren Obbjekts zu erhalten.

In Python 3 wurde nur die `next()` Funktion erhalten. Rufen wir die `.next()` Methode auf, so erhalten wir einen `AttributeError`.

### Python 2


```python
generator = (buchstabe for buchstabe in "abcdefg")

next(generator)  # = a
generator.next() # = b
```

### Python 3


```python
generator = (buchstabe for buchstabe in "abcdefg")

next(generator)  # = a
generator.next() # = AttributeError
```

## 8. For-Schleifen Variablen und das globale Namensbereich Leck

In Python 3 werden die Variablen aus for-Schleifen nicht länger an den globalen Namensbereich übergeben! Das möchten wir an einem Beispiel verdeutlichen:

### Python 2


```python
i = 1
print "Zuerst: i = ", i                       # i = 1
print "Abstarktion: ", [i for i in range(5)]  # [0, 1, 2, 3, 4]
print "Danach: i = ", i                       # 1 = 4
```

### Python 3


```python
i = 1
print("Zuerst: i = ", i)                       # i = 1
print("Abstarktion: ", [i for i in range(5)])  # [0, 1, 2, 3, 4]
print("Danach: i = ", i)                       # 1 = 1
```

## 9. User-Inputs via input() verarbeiten

Die `input()` Funktion wurde so überarbeitet, dass der User-Input in Python 3 immer als `str` Objekt gespeichert wird. So kann verhindert werden, dass andere (potentiell gefährdende) Datentypen eigegeben werden.

Um diese potentielle Gefahr in Python 2 zu umgehen, müssen wir `raw_input()` verwenden.

### Python 2


```python
mein_input = input("Gib eine Zahl ein: ")
# Gibt eine Zahl ein: 123
type(mein_input)    # <type 'int'>

mein_input = raw_input("Gib eine Zahl ein: ")
# Gibt eine Zahl ein: 123
type(mein_input)    # <type 'str'>
```

### Python 3


```python
mein_input = input("Gib eine Zahl ein: ")
# Gibt eine Zahl ein: 123
type(mein_input)    # <class 'str'>
```

## 10. Iterierbare Objekte statt Listen zurückgeben

Wie wir bereits bei **4. xrange** gesehen haben, geben manche Funktionen und Methoden in Python 3 iterierbare Objekte zurück, anstatt wie in Python 2 Listen.

Da wir meistens nur einmal über solche Objekte iterieren, ergibt diese Umstellung insofern Sinn, als dass sie Speicherkapazität spart. 

Wenn wir wirklich ein `list`-Objekt benötigen, dann können wir diese Objekte einfach mit der `list()` Funktion konvertieren.

### Python 2


```python
print range(3)        # [0, 1, 2]
print type(range(3))  # <type 'list'>
```

### Python 3


```python
print(range(3))        # range(0, 3)
print(type(range(3)))  # <class 'range'>
print(list(range(3)))  # [0, 1, 2]
```

## 11. Banker Rundungen

Python 3 adaptierte den neuen Standard, um Dezimalzahlen zu runden, wenn wir .5 an der letzten relevanten Stelle vorfinden. Jetzt, in Python 3, werden solche Zahlen zur nächsten geraden Zahl gerundet. So soll der Tendenz zu großen Zahlen entgegengewirkt werden. Für weitere Informationen empfehlen wir folgende (*englische*) Artikel auf Wikipedia:

* [Rounding](https://en.wikipedia.org/wiki/Rounding#Round_half_to_even)
* [Floating Point](https://en.wikipedia.org/wiki/IEEE_floating_point#Roundings_to_nearest)

### Python 2


```python
round(15.5) # = 16
round(16.5) # = 17
```

### Python 3


```python
round(15.5) # = 16
round(16.5) # = 16
```

## Abschluss
Damit sind wir am Ende dieser Lektion angelangt. Ich hoffe ihr konntet somit alle wesentlichen Unterschiede zwischen Python 3.x und Python 2.7.x nachvollziehen und verstehen. Dieses Bonuskapitel sollte euch insbesondere auf den Fall vorbereiten, indem ihr auf die Kompatibilität eures Codes mit beiden Python Versionen achten müsst.

### Weiterhin viel Erfolg mit Python!

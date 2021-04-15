# Objekte und Datenstrukturen Übung - Aufgabe

Quelle: Datamics

## Teste dein Wissen

#### Beantworte die folgenden Fragen:

Schreibe eine kurze Beschreibung aller folgenden Objekt Typen und Daten Strukturen:

Zahlen:

Strings:

Listen:

Tupel:

Dictionaries:


## Zahlen

Schreibe eine Gleichung, die Multiplikation, Division, einen Exponenten, Addition und Subtraktion nutzt und 100.25 ergibt.

Hinweis: Es geht nur darum, die grundsätzlichen Funktionen der Arithmetik zu kennen, ihr könnt vom Ergebnis aus starten.


```python

```

Erkläre, was die nächste Zelle ergeben wird und warum. Kannst du es so ändern, damit das Ergebnis richtig ist?


```python
2/3
```

Beantworte diese 3 Fragen, ohne den Code zu schreiben. Dann schreibe den Code und überprüfe deine Ergebnisse.

1| Was ist das Ergebnis der folgenden Berechnungen?
    
    4 * (6 + 5)
    
    4 * 6 + 5 
    
    4 + 6 * 5 


```python

```

2| Welchem <i>Typ</i> entspricht das Ergebnis der Gleichung 3 + 1.5 + 4?


```python

```

3| Was würdest du verwenden, um die Quadratwurzel einer Zahl zu erhalten und was für die Quadratur?


```python

```

## Strings

Wir nehmen den String "Hallo" als Ausgangsposition. Nutze ein Index Kommando, dass den Buchstaben "a" zurückgibt. Nutze die nächste Zelle:


```python
s = "Hallo"
# Gebe "a" aus, indem du Index verwendest

# Code hier
```

Den String "Hallo" rückwärst schreiben:


```python
s = "Hallo"
# Schreibe s rückwärts, indem du Index verwendest

# Code hier
```

Zeige zwei Methoden, um den Buchstaben "o" durch Index zu erhalten:


```python
s = "Hallo"
# Lösung 1

# Lösung 2

```

## Listen

Erstelle die Liste [0,0,0] auf zwei unterschiedliche Arten.


```python

```

Ersetze in dieser verschachtelten Liste "Hallo", um stattdessen "Auf Wiedersehen" zu sagen.


```python
l = [1,2[3,4,'Hallo']]
```

Sortiere die folgende Liste:


```python
l = [3,4,5,5,6]
```

## Dictionaries

Schnappe dir das "Hallo" aus folgendem Dictionary, indem du Keys und Index benutzt:


```python
d = {'Einfacher_Key':'Hallo'}
# Das "Hallo" ausgeben

```


```python
d = {'k1':{'k2':'Hallo'}}
# Das "Hallo" ausgeben

```


```python
# Es wird etwas tiefer
d = {'k1':[{'key_ebene2':['das ist tief',['Hallo']]}]}
# Das "Hallo" ausgeben

```


```python
# Das wird jetzt schwer und etwas nervig!
d = {'k1':[1,2,{'k2':['etwas kompliziert',{'schwer':[1,2,['Hallo']]}]}]}
# Das "Hallo" ausgeben

```

Kann man ein Dictionary sortieren? Warum oder warum nicht?

## Tupel

Was ist der Hauptunterschied zwischen Tupeln und Listen?


Wie erstellt man ein Tupel?

## Set

Was ist einzigartig an Sets?

Benutze ein Set, um die einzigartigen Werte der folgenden Liste zu finden:


```python
l = [1,2,2,33,4,4,11,22,3,3,2]
```

## Booleans

Für das folgende Quiz, bekommen wir hier eine Vorschau für die Vergleichsoperatoren:
<table class="table table-bordered">
<tr>
<th style="width:10%">Operator</th><th style="width:45%">Beschreibung</th><th>Beispiel</th>
</tr>
<tr>
<td>==</td>
<td>Wenn der Wert zweier Operanten gleich ist, wird die Bedingung True (wahr).</td>
<td> (a == b) ist nicht True.</td>
</tr>
<tr>
<td>!=</td>
<td>Wenn der Wert zweier Operanten nicht gleich ist, wird die Bedingung True (wahr).</td>
<td>(a != b) ist True</td>
</tr>
<tr>
<td>&gt;</td>
<td>Wenn der Wert des linken Operanten größer als der des rechten ist, dann wird die Bedingung True (wahr).</td>
<td> (a &gt; b) ist nicht Wahr.</td>
</tr>
<tr>
<td>&lt;</td>
<td>Wenn der Wert des linken Operanten kleiner als der des rechten ist, dann wird die Bedingung True (wahr).</td>
<td> (a &lt; b) ist True (wahr).</td>
</tr>
<tr>
<td>&gt;=</td>
<td>Wenn der Wert des linken Operanten größer als oder gleich dem des rechten ist, dann wird die Bedingung True (wahr).</td>
<td> (a &gt;= b) ist nicht True (wahr). </td>
</tr>
<tr>
<td>&lt;=</td>
<td>Wenn der Wert des linken Operanten kleiner als oder gleich dem des rechten ist, dann wird die Bedingung True (wahr).</td>
<td> (a &lt;= b) ist True (wahr). </td>
</tr>
</table>

Was wird der Boolean Wert sein, den folgende Codes erzeugen? Antwortet bevor ihr die Zellen ausführt!


```python
# Zuerst beantworten, dann ausführen
2 > 3
```


```python
# Zuerst beantworten, dann ausführen
3 <= 2
```


```python
# Zuerst beantworten, dann ausführen
3 == 2.0
```


```python
# Zuerst beantworten, dann ausführen
3.0 == 3
```


```python
# Zuerst beantworten, dann ausführen
4**0.5 != 2
```

Letzte Frage: Was ergibt der folgende Codeblock?


```python
# Zwei verschachtelte Listen
l_one = [1,2,[3,4]]
l_two = [1,2,{'k1':4}]

#True or False?
l_one[2][0] >= l_two[2]['k1']
```

## Gut gemacht! Das war deine erste Übung.

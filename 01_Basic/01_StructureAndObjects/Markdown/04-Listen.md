# Listen
Quelle: Datamics
Zuvor als wir über Strings sprachen, haben wir das Konzept von Sequenzen eingeführt. Listen können als die allgemeinste Form von Sequenzen in Python verstanden werden. Anders als Strings sind sie änderbar, was bedeutet, dass die die Elemente in einer Liste geändert werden können!

In dieser Lektion werden wir folgendes lernen:

1. Erstellen von Listen
2. Indexierung und Zerteilung von Listen
3. Grundlegende Listen Methoden
4. Verschachtelte Listen
5. Einführung zur Zusammenfassung von Listen

Listen werden mit Klammern [] erstellt und ihre Elemente durch Kommas getrennt.

Lasst uns loslegen und einige Listen erstellen!


```python
# Eine Liste der Variablen liste zuweisen
liste = [1,2,3]
```

Wir haben soeben eine Liste von Zahlen erstellt, wobei Listen verschiedene Arten von Objekten beinhalten können. Zum Beispiel:


```python
liste = ['Ein String',23,100.232,'H']
```

Genau wie bei Strings gibt uns die len() Funktion die Anzahl der Listenelemente die in der Sequenz beinhaltet sind.


```python
len(liste)
```




    4



## Indexierung und Aufteilen

Beides funktioniert so wie bei Strings. Lasst uns eine Liste erstellen und die Funktionsweise auffrischen:


```python
liste = ['Eins','Zwei','Drei',4,5]
```


```python
# Das Element bei Index 0
liste[0]
```




    'Eins'




```python
# Index 1 und alle Elemente danach
liste[1:]
```




    ['Zwei', 'Drei', 4, 5]




```python
# Alle Elemente bis zum Index 3
liste[:3]
```




    ['Eins', 'Zwei', 'Drei']



Wir können - genau wie bei Strings - Listen durch ein + erweitern.


```python
liste + ['Neues Item']
```




    ['Eins', 'Zwei', 'Drei', 4, 5, 'Neues Item']



Beachtet, dass dies die eigentliche Liste nicht ändert!


```python
liste
```




    ['Eins', 'Zwei', 'Drei', 4, 5]



Wir müssten die Liste neu zuordnen, um eine permanente Ergänzung durchzuführen.


```python
# Neue Zuordnung
liste = liste + ['Neues permanentes Item']
```


```python
liste
```




    ['Eins', 'Zwei', 'Drei', 4, 5, 'Neues permanentes Item']



Wir können außerdem durch ein * die wiederholte Ausgabe erzeugen:


```python
# Die Liste verdoppel
liste * 2
```




    ['Eins',
     'Zwei',
     'Drei',
     4,
     5,
     'Neues permanentes Item',
     'Eins',
     'Zwei',
     'Drei',
     4,
     5,
     'Neues permanentes Item']




```python
# Auch Verdopplung ist nicht permanent
liste
```




    ['Eins', 'Zwei', 'Drei', 4, 5, 'Neues permanentes Item']



## Grundlegende Listen Methoden

Sofern du andere Programmiersprachen kennst könntest du an diesem Punkt Parallelen zwischen Listen und Arrays ziehen. Listen in Python sind allerdings aus zwei guten Gründen flexibler als Arrays in anderen Sprachen: Sie haben keine fixierte Größe und sie haben keine Beschränkung der Objektart.

Lasst uns ein paar weitere spezielle Methoden für Listen kennenlernen:


```python
# Neue Liste erstellen
l = [1,2,3]
```

Durch die `append` Methoden können wir Items permanent zur Liste hinzufügen:


```python
# Append
l.append('Hinzugefuegt!')
```


```python
# Check
l
```




    [1, 2, 3, 'Hinzugefuegt!']



Nutzt `pop` um Items aus der Liste zu löschen. Per Standard löscht pop das letzte Item aus der Liste, aber wir können auch bestimmen, welcher Index gelöscht werden soll. Hier ist ein Beispiel:


```python
# Das Item am Index 0 löschen
l.pop(0)
```




    1




```python
# Check
l
```




    [2, 3, 'Hinzugefuegt!']




```python
# Das gelöschte Item einer Variablen zuweisen
# Denkt daran, das per Standard das letze Item gelöscht wird
poped = l.pop()
```


```python
# Check
poped
```




    'Hinzugefuegt!'




```python
# Check
l
```




    [2, 3]



Es sollte außerdem festgehalten werden, das die Indexierung einen Error erzeugt, sofern kein Element am angegebenen Index existiert. So, wie hier:


```python
l[100]
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-22-e2a0c2623844> in <module>
    ----> 1 l[100]
    

    IndexError: list index out of range



```python
neue_liste = ['a','e','u','o','i']
```


```python
# Anzeigen
neue_liste
```




    ['a', 'e', 'u', 'o', 'i']




```python
# Nutzt reverse, um die umgekehrte Reihenfolge zu erzeugen (permanent!)
neue_liste.reverse()
```


```python
# Check
neue_liste
```




    ['i', 'o', 'u', 'e', 'a']




```python
# Nutzt sort um die Liste zu Sortieren
# Strings nach Alphabet, Zahlen aufsteigen
neue_liste.sort()
```


```python
# Check
neue_liste
```




    ['a', 'e', 'i', 'o', 'u']



## Verschachtelte Listen

Ein tolles Feature von Python Daten Strukturen ist, dass sie Einbinden/Verschachteln unterstützen. Das bedeutet, wir können Daten Strukturen innerhalb von Daten Strukturen haben. Zum Beispiel: Eine Liste in einer Liste.

Lasst uns betrachtet, wie das funktioniert!


```python
# Drei Listen erstellen
lst_1 = [1,2,3]
lst_2 = [4,5,6]
lst_3 = [7,8,9]

# Eine Liste aus den Listen erstellen
matrix = [lst_1,lst_2,lst_3]
```


```python
# Check
matrix
```




    [[1, 2, 3], [4, 5, 6], [7, 8, 9]]



Und jetzt können wir wieder Indexierung verwenden, um auf Elemente zuzugreifen. Dabei ist wichtig, dass es nun zwei Ebenen gibt. Schaut hier:


```python
# Das erste Element der Matrix
matrix[0]
```




    [1, 2, 3]




```python
# Das erste Element des ersten Elements der Matrix
matrix[0][0]
```




    1



## Listen Abstraktion

Python bietet ein fortgeschrittenes Feature namens Listen Abstraktion (list comprehensions). Sie ermöglichen das schnelle Erstellen von Listen. Für das volle Verständnis von Listen Abstraktion müssen wir Loops verstehen. Also keine Sorge, falls jetzt noch nicht alles klar ist. Ihr könnt diese Sektion überspringen, da wir später darauf zurückkommen.

Aber solltet ihr interessiert sein, hier ist ein Beispiel:


```python
# Eine Listen Abstraktion erstellen, die einen for loop nutzt
erste_spalte = [zeile[0] for zeile in matrix]
```


```python
# Check
erste_spalte
```




    [1, 4, 7]



Wir haben Listen Abstraktion genutzt, um die erste Spalte der Matrix, d.h. das erste Element jeder Zeile, als Liste zu erstellen. Wir werden uns dies später noch viel detaillierter ansehen. 

Für mehr fortgeschrittenen Methoden und Features von Listen in Python könnt ihr später im Kurs die Lektion "Fortgeschrittene Listen" anschauen!

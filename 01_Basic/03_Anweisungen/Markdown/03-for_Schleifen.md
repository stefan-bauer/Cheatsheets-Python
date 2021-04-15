# for Schleifen

Quelle: Datamics

Eine `for` Schleife (en.: for loop) fungiert als Iteration in Python, die durch Items geht, die in einer Sequenz (oder jeder anderen iterierbaren Form) stehen. Objekte die wir bereits behandelt haben und auf die wir diese Iteration anwenden können sind Strings, Listen, Tupel und bereits vorinstallierte Iterationen für Dictionaries, wie bspw. keys und values.

"Klassische" numerische Schleifen, wie sie C und C++ kennen, besitzen eine Schleifenvariable. Diese wird mit einem Startwert gestartet und dieser Wert nach jedem Durchlauf des Codeblocks verändert. Meistens wird sie um einen bestimmten Wert (z.B. 1) erhöht oder vermindert, bis ein bestimmter Zielwert erreicht ist. Diese Schleifenform wird auch als Zählschleife bezeichnet. Das hängt damit zusammen, dass die Schleifenvariable und somit auch der Startwert, der Endwert und die Schrittweite numerisch sein müssen.

Im Beispiel sehen wir eine for-Schleife in C, die die Zahlen von 1 bis 10 ausdruckt: 
    
    for(i = 1; i <= 10; i+)
       printf("i: %d\n", i);

Diese Form der Schleife existiert so nicht direkt in Python. Vergleichbar ist die Version hier mit einer *foreach* Schleife, die man aus anderen Sprachen kennen könnte.

Wir haben das for Statement in Python bereits ein klein wenig in vorherigen Lektionen kennengelernt. Lasst es uns trotzdem noch einmal formalisieren, um es besser zu verstehen.

Hier ist eine allgemeine Form dafür, wie eine for Schleife in Python aussieht:

    for Item in Objekt:
        Statement, um etwas zu tun
        
Der Name, der für das Item verwendet wird, obliegt vollkommen dem Coder. Das ermöglicht uns den nach eigenem Ermessen am besten passenden Namen auszuwählen. Der festgelegte Item Name kann dann innerhalb der Schleifen als Referenz verwendet werden. Zum Beispiel, wenn wir ein if Statement für das Item durchführen wollen.

Weiter geht es mit einigen Beispielen für for Schleifen in Kombination mit einer Vielzahl von Objekt Arten. Wir beginnen simpel und steigern das Niveau fortlaufend.

## Listen


```python
# Wie wir solche Listen automatisieren können lernen wir in der nächsten Lektion
l = [1,2,3,4,5,6,7,8,9,10]
```


```python
for num in l:
    print(num)
```

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10


Gut! Hoffentlich ergibt das Sinn für euch. Lasst uns nun ein if Statement einbauen, um auf gerade Zahlen zu überprüfen. Dazu führen wir noch ein neues Konzept ein - das modulo.

## Modulo

Das Modulo erlaubt es uns, den Rest einer Division zu erhalten, indem wir % verwenden. Zum Beispiel:


```python
17 % 5
```




    2



Das ergibt Sinn, da 17 geteilt durch 5 als Ergebnis 3 hat mit einem Rest von 2. Einige weitere kurze Beispiele:


```python
10 % 3
```




    1




```python
18 % 7
```




    4




```python
4 % 2
```




    0



Sofern eine Zahl vollständig teilbar ist und keinen Rest hat, ist das Ergebnis von Modulo 0. Das können wir ausnutzen, um zu testen, ob eine Zahl eine ganze Zahl ist. 

Zurück zur for Schleife!

## Nur gerade Nummern


```python
for num in l:
    if num % 2 == 0:
        print(num)
```

    2
    4
    6
    8
    10


Wir können auch ein else Statement einbauen:


```python
for num in l:
    if num % 2 == 0:
        print(num)
    else:
        print('Ungerade')
```

    Ungerade
    2
    Ungerade
    4
    Ungerade
    6
    Ungerade
    8
    Ungerade
    10


## Laufende Summe

Eine weitere übliche Idee ist es, während eines for Loops eine Art von Laufender Summe zu erfassen. Zum Beispiel: Eine for Schleife, die die Summe einer Liste bildet.


```python
# Start der Summe bei 0
l_sum = 0

for num in l:
    l_sum = l_sum + num
    
print(l_sum)
```

    55


Toll! Schaut euch das obige Beispiel so lange an, bis ihr genau versteht, was passiert! Das hätten wir übrigens auch mit einem += lösen können. Seht her:


```python
# Start der Summe bei 0
l_sum = 0

for num in l:
    l_sum += num
    
print(l_sum)
```

    55


## Strings

Wir haben for Schleifen bereits für Listen verwendet, aber wie sieht es mit Strings aus? Ruft euch in Erinnerung, dass Strings eine Sequenz sind. Wenn wir darüber eine Iteration laufen lassen, dann greifen wir auf jedes Item in diesem String zu.


```python
for zeichen in 'Das ist ein String!"':
    print(zeichen)
```

    D
    a
    s
     
    i
    s
    t
     
    e
    i
    n
     
    S
    t
    r
    i
    n
    g
    !
    "


## Tupel

Lasst uns als nächstes auch noch Tupel betrachten:


```python
tup = (1,2,3,4,5)

for t in tup:
    print(t)
```

    1
    2
    3
    4
    5


Tupel bieten eine besondere Qualität, wenn es zu for Schleifen kommt. Wenn ihr eine Iteration über eine Sequenz laufen lasst, die Tupel beinhaltet, wird das Tupel selbst zum Item. Das ist ein Beispiel für das stufenweise entpacken von Tupeln. Durch die for Schleife werden wir die einzelnen Tupel innerhalb der Sequenz entpacken und können auf die einzelnen Items im Tupel selbst zugreifen.


```python
l = [(2,4),(6,8),(10,12)]
```


```python
for tup in l:
    print(tup)
```

    (2, 4)
    (6, 8)
    (10, 12)



```python
# Jetzt mit Entpacken
for (t1,t2) in l:
    print(t1)
```

    2
    6
    10


Cool! Mit Tupeln in einer Sequenz können wir durch Entpacken auf die Items innerhalb der Tupel zugreifen. Der Grund aus dem das wichtig ist ist der, dass viele Objekte ihre Iterationen in Form von Tupeln ausgeben. Lasst uns als nächstes Iterationen für Dictionaries betrachten, um das genauer zu verstehen!

## Dictionaires


```python
d = {'k1':1,'k2':2,'k3':3}
```


```python
for item in d:
    print(item)
```

    k3
    k2
    k1


Ist euch aufgefallen, wie das nur die Keys ausgibt? Wie können wir also an die Werte kommen? Oder wie erhalten wir beides, Keys und Werte?

### Python 2: Nutzt .iteritems() um Iteration zu betreiben

In Python 2 solltet ihr .iteritems() benutzen, um durch Keys und Werte zu iterieren. Das erstellt einen Generator (mit denen wir uns später im Kurs noch genauer befassen werden) der Keys und Values unseres Dictionary generiert. So sieht das praktisch aus:


```python
# Generator erstellen
d.iteritems()
```




    <dictionary-itemiterator at 0x1118baec0>



Die iteritems() Methode aufzurufen gibt eine Liste von Tupeln zurück. Wir können jetzt durch sie iterieren, wie wir es in vorherigen Beispielen getan haben.


```python
# Generator erstellen
for k,v in d.iteritems():
    print(k)
    print(v)
```

    k3
    3
    k2
    2
    k1
    1


### Python 3: items()

In Python 3 solltet ihr .items() nutzen, um durch Keys und Werte eines Dictionary zu iterieren. Zum Beispiel:


```python
# Für Python 3
for k,v in d.items():
    print(k)
    print(v)
```

    k3
    3
    k2
    2
    k1
    1


Eventuell fragt ihr euch, wie das in Python 2 funktionieren konnte. Das liegt daran, dass Generatoren in den frühen Jahren von Python eingeführt wurden. (Wir werden Generatoren wie gesagt in einer folgenden Lektion noch genauer betrachten. Das Grundprinzip ist, dass sie Daten nicht im Speicher ablegen, sondern einfach ausgeben, während sie durch ein iterierbares Item gehen).

Ursprünglich bildete items() eine Liste aus Tupeln und gibt diese zurück. Das konnte potenziell sehr viel Speicher einnehmen.

Dann wurden Generatoren eingeführt und die Methode wurde als Iterator-Generator Methode names iteritems() überarbeitet. Das Original blieb für Rückwärtskompatibilität erhalten.

Eine der Änderungen in Python 3 ist, dass items() dort nun Iteratoren ausgibt und die Liste nie vollständig erstellt wird. Die iteritems() Methode ist auch hinfällig, da items() in Python 2 jetzt wie iteritems() funktioniert.

## Schlussfolgerung

Wir haben gelernt wie wir for Loops nutzen können, um durch Tupel, Listen, Strings und Dictionaries zu iterieren. Es wird ein wichtiges Tool für uns werden, deshalb ist es wichtig, dass ihr es vollständig versteht.

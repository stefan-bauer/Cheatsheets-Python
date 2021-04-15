# Den Code timen

Quelle: Datamics

Manchmal ist es wichtig, zu wissen, wie lange dein Code zur Ausführung benötigt oder wenigstens, ob eine bestimmte Zeile den Code verlangsamt. Python hat ein vorinstalliertes Modul, um das herauszufinden.

Dieses Modul bieten eine einfache Möglichkeit, um die Zeit kleiner Codeeinheiten in Python zu messen. Es bietet sowohl ein Kommandozeilen Interface als auch ein aufrufbares. Es umgeht einige übliche Hindernisse beim Messen von Ausführungsdauer.

Lasst uns `timeit` lernen!


```python
import timeit
```

Jetzt können wir timeit benutzen um verschiedene Methoden zum Erstellen des Strings "0-1-2-3-...-99" zu messen. 

Wir werden zwei Parameter übergeben. Erstens die tatsächliche Codezeile, die ausgeführt werden soll. Zweitens die Anzahl der Wiederholungen. Dabei verwenden wir 10.000 Durchläufe, um einen merkbaren Unterschied zwischen den Methoden ermitteln zu können.


```python
# For Schleife
timeit.timeit('"-".join(str(n) for n in range(100))', number=10000)
```




    0.3447215079795569




```python
# List Comprehension
timeit.timeit('"-".join([str(n) for n in range(100)])', number=10000)
```




    0.3068382430355996




```python
# Map()
timeit.timeit('"-".join(map(str, range(100)))', number=10000)
```




    0.25435698591172695



Klasse! Wir sehen einen signifikanten  Zeitunterschied durch die Nutzung von map()! Das ist gut zu wissen und wir sollten es im Gedächtnis behalten.

Jetzt können wir iPython's magische Funktion %timeit vorstellen.

iPython's %timeit führt eine bestimmte Zeile Code 7 mal in einer Schleife durch und gibt die schnellste Durchführungszeit aus.

Lasst uns die obigen Methoden mit %timeit wiederholen.


```python
%timeit "-".join(str(n) for n in range(100))
```

    30.9 µs ± 1.37 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)



```python
%timeit "-".join([str(n) for n in range(100)])
```

    27.1 µs ± 1.94 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)



```python
%timeit "-".join(map(str, range(100)))
```

    20 µs ± 409 ns per loop (mean ± std. dev. of 7 runs, 10000 loops each)


Toll! Wir gelangen zur selben Schlussfolgerung. Es ist an dieser Stelle noch wichtig zu erwähnen, dass iPython die Dauer an echter Zeit limitiert, die es für timeit aufwendet. Stellt es fest, dass beispielsweise 100.000 Schleifen 10 Minuten gedauert haben, würde iPython die Zahl der Durchläufe automatisch zu etwas Sinnvollerem wie 100 oder 1000 reduzieren.

Soweit so gut! Ihr solltet jetzt damit vertraut sein, wie ihr einzelnen Zeilen eures Codes bzw. deren Durchführungsdauer timen könnt. Sowohl innerhalb von iPython als auch außerhalb. Ihr könnt für mehr Informationen in die [Dokumentation](https://docs.python.org/3/library/timeit.html) schauen!

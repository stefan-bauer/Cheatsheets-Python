# Verknüpfte Vergleichsoperatoren

Quelle: Datamics

Ein interessantes Feature von Python ist die Möglichkeit mehrere Vergleiche zu verknüpfen und so komplexere Überprüfungen durchzuführen. Wir können diese verknüpften Vergleiche als Kurzschrift für größere Boolean Ausdrücke verwenden.

In dieser Lektion werden wir lernen, wie wir mehrere Vergleiche verknüpfen können, sowie zwei weitere wichtige Statements in Python: <b>and</b> und <b>or</b>.

Hier ein paar Beispiele für Verknüpfungen:


```python
1 < 2 < 3
```




    True



Das obige Statement überprüft, ob 1 kleiner als 2 ist <b>und</b> 2 gleichzeitig kleiner als 3 ist. Wir hätten dies auch mit dem <b>and</b> Statement schreiben können:


```python
1<2 and 2<3
```




    True



Das <b>and</b> Statement stellt sicher, dass zwei Vergleiche zur selben Zeit True (wahr) sind. Lasst uns ein weiteres Beispiel betrachten:


```python
1 < 3 > 2
```




    True



Das obige Statement überprüft, ob 3 größer als die beiden anderen Werte ist. Erneut könnten wir das and Statement verwenden:


```python
1<3 and 3>2
```




    True



Es ist wichtig festzuhalten, dass Python beide einzelnen Vergleiche überprüft. Wir können außerdem auch <b>or</b> verwenden, um Vergleiche durchzuführen. Zum Beispiel so:


```python
1==2 or 2<3
```




    True



Durch das or Statement muss nun nur einer der beiden Vergleiche True (wahr) sein, damit das Gesamtergebnis True (wahr) ist. Hier noch ein weiteres Beispiel, um dies deutlich zu machen:


```python
1==1 or 100==1
```




    True



Toll! Als kleine Zusammenfassung dieser Lektion: Ihr solltet ein gutes Verständnis für <b>and</b> und <b>or</b> und deren Verwendung bekommen haben. Außerdem darüber, wie man verknüpfte Vergleiche liest und erstellt.

Weiter geht es in einem kurzen Quiz zu dieser Sektion!

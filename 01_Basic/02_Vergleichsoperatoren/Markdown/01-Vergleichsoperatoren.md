# Vergleichsoperatoren

Quelle: Datamics

In dieser Lektion werden wir etwas über Vergleichsoperatoren lernen. Diese Operatoren erlauben es uns, Variablen zu vergleichen und einen Boolean Wert (`True` oder `False`) auszugeben.

Sofern eine gewisse Erfahrung mit Mathematik bekannt ist, sollten diese relativ selbsterklärend sein.

Zuerst präsentieren wir hier eine Tabelle der Vergleichsoperatoren und gehen dann einige Beispiele durch.

Stellen wir uns die Variablen a = 3 und b = 5 vor:

## Tabelle der Vergleichsoperatoren
<table class="table table-bordered">
<tr>
<th style="width:10%">Operator</th><th style="width:45%">Beschreibung</th><th>Beispiel</th>
</tr>
<tr>
<td>==</td>
<td>Wenn der Wert zweier Operanten gleich ist, wird die Bedingung True (wahr).</td>
<td> (a == b) ist nicht True (wahr).</td>
</tr>
<tr>
<td>!=</td>
<td>Wenn der Wert zweier Operanten nicht gleich ist, wird die Bedingung True (wahr).</td>
<td>(a != b) ist True (wahr).</td>
</tr>
<tr>
<td>&gt;</td>
<td>Wenn der Wert des linken Operanten größer als der des rechten ist, dann wird die Bedingung True (wahr).</td>
<td> (a &gt; b) ist nicht True (wahr).</td>
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

Last uns jetzt einige Beispiele durchgehen:

### Gleich


```python
2 == 2
```




    True




```python
1 == 0
```




    False



### Nicht Gleich


```python
2 != 1
```




    True




```python
2 != 2
```




    False



### Größer als


```python
2 > 1
```




    True




```python
2 > 4
```




    False



### Kleiner als


```python
2 < 4
```




    True




```python
2 < 1
```




    False



### Größer als oder gleich


```python
2 >= 2
```




    True




```python
2 >= 1
```




    True



### Kleiner als oder gleich


```python
2 <= 2
```




    True




```python
2 <= 4
```




    True



Großartig! Schaut euch jeden der Vergleichsoperatoren solange an, bis ihr genau versteht, was jeder bedeutet. Hoffentlich war das soweit relativ einfach für euch.

Es folgt: Verbundene Vergleichsoperatoren.

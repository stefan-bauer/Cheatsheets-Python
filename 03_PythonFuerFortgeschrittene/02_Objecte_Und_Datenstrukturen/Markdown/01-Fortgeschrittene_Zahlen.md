# Fortgeschrittene Zahlen

Quelle: Datamics

In dieser Lektion werden wir mehr über neue Darstellungen von Zahlen in Python lernen.

## Hexadezimal

Durch die Nutzung der Funktion hex() können wir Zahlen in das Hexadaziamlformat umwandeln:


```python
hex(123)
```




    '0x7b'




```python
hex(897)
```




    '0x381'



## Binär

Die Funktion bin() wandelt Zahlen in Binärformat um:


```python
bin(9876)
```




    '0b10011010010100'




```python
bin(45)
```




    '0b101101'




```python
bin(34569284)
```




    '0b10000011110111110001000100'



## Potenz

pow() mit zwei Parametern, die x^y entsprechen, berechnet.


```python
pow(3,2)
```




    9



## Absoluter Wert bzw. Betrag


```python
abs(-83)
```




    83




```python
abs(3)
```




    3



## Runden

Die Funktion round() rundet eine Zahl auf eine bestimmte Stelle (Standard: 0 Stellen). Das gibt immer eine Gleitkommazahl zurück!


```python
round(3)
```




    3




```python
round(3.1234532,2)
```




    3.12



Python verfügt über eine vorinstallierte math (Mathematik) Bibliothek, die ebenfalls nützlich ist, um mit mathematischen Operationen umzugehen. [Hier](https://docs.python.org/3.0/library/math.html) geht's zur Dokumentation!

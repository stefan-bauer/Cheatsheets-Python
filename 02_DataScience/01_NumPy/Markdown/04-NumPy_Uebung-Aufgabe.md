# NumPy Übung - Aufgabe

Quelle: Datamics

Jetzt wo wir schon einiges über NumPy gelernt haben können wir unser Wissen überprüfen. Wir starten dazu mit einigen einfachen Aufgaben und steigern uns zu komplizierteren Fragestellungen.

**Importiere NumPy als np**


```python

```

**Erstelle ein Array von 10 Nullen**


```python

```




    array([ 0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.,  0.])



**Erstelle ein Array von 10 Einsen**


```python

```




    array([ 1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.,  1.])



**Erstelle ein Array von 10 Fünfen**


```python

```




    array([ 5.,  5.,  5.,  5.,  5.,  5.,  5.,  5.,  5.,  5.])



**Erstelle ein Array der Zahlen von 10 bis 50**


```python

```




    array([10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26,
           27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43,
           44, 45, 46, 47, 48, 49, 50])



**Erstelle ein Array aller gerader Zahlen zwischen 10 und 50**


```python

```




    array([10, 12, 14, 16, 18, 20, 22, 24, 26, 28, 30, 32, 34, 36, 38, 40, 42,
           44, 46, 48, 50])



**Erstelle eine 3x3 Matrix, die die Zahlen von 0 bis 8 beinhaltet**


```python

```




    array([[0, 1, 2],
           [3, 4, 5],
           [6, 7, 8]])



**Erstelle eine 3x3 Einheitsmatrix**


```python

```




    array([[ 1.,  0.,  0.],
           [ 0.,  1.,  0.],
           [ 0.,  0.,  1.]])



**Nutze NumPy, um eine Zufallszahl zwischen 0 und 1 zu erstellen**


```python

```




    array([ 0.81555966])



**Nutze NumPy, um ein Array von 25 Zufallszahlen, die einer Standardnormalverteilung folgen, zu erstellen**


```python

```




    array([-0.51161353,  1.2339811 , -1.58511846, -1.26642544, -0.57329076,
            0.43142059, -0.00602832,  0.14251496,  0.69070198,  0.49039449,
           -0.08035674, -1.62460532, -0.57644663,  0.81009858,  0.43083981,
            0.94419797,  0.02978022, -0.1103703 ,  0.63857005,  0.45090301,
            0.28772462, -0.82507961, -1.56721001, -0.58890871, -0.16899995])



**Erstelle die folgende Matrix:**


```python

```




    array([[ 0.01,  0.02,  0.03,  0.04,  0.05,  0.06,  0.07,  0.08,  0.09,  0.1 ],
           [ 0.11,  0.12,  0.13,  0.14,  0.15,  0.16,  0.17,  0.18,  0.19,  0.2 ],
           [ 0.21,  0.22,  0.23,  0.24,  0.25,  0.26,  0.27,  0.28,  0.29,  0.3 ],
           [ 0.31,  0.32,  0.33,  0.34,  0.35,  0.36,  0.37,  0.38,  0.39,  0.4 ],
           [ 0.41,  0.42,  0.43,  0.44,  0.45,  0.46,  0.47,  0.48,  0.49,  0.5 ],
           [ 0.51,  0.52,  0.53,  0.54,  0.55,  0.56,  0.57,  0.58,  0.59,  0.6 ],
           [ 0.61,  0.62,  0.63,  0.64,  0.65,  0.66,  0.67,  0.68,  0.69,  0.7 ],
           [ 0.71,  0.72,  0.73,  0.74,  0.75,  0.76,  0.77,  0.78,  0.79,  0.8 ],
           [ 0.81,  0.82,  0.83,  0.84,  0.85,  0.86,  0.87,  0.88,  0.89,  0.9 ],
           [ 0.91,  0.92,  0.93,  0.94,  0.95,  0.96,  0.97,  0.98,  0.99,  1.  ]])



**Erstelle ein Array aus 20 gleichmäßig verteilten Punkten zwischen 0 und 1**


```python

```




    array([ 0.        ,  0.05263158,  0.10526316,  0.15789474,  0.21052632,
            0.26315789,  0.31578947,  0.36842105,  0.42105263,  0.47368421,
            0.52631579,  0.57894737,  0.63157895,  0.68421053,  0.73684211,
            0.78947368,  0.84210526,  0.89473684,  0.94736842,  1.        ])



## NumPy Indexing und Selection

Du wirst nun einige Matrizen sehen und deine Aufgabe ist es, die angezeigten Ergebnis-Outputs zu reproduzieren:


```python

```




    array([[ 1,  2,  3,  4,  5],
           [ 6,  7,  8,  9, 10],
           [11, 12, 13, 14, 15],
           [16, 17, 18, 19, 20],
           [21, 22, 23, 24, 25]])




```python
# Schreibe deinen Code hier, der das Ergebnis reproduzieren soll
# Achte darauf, die untere Zelle nicht auszuführen, sonst
# wirst du das Ergebnis nicht mehr sehen können
```


```python

```




    array([[12, 13, 14, 15],
           [17, 18, 19, 20],
           [22, 23, 24, 25]])




```python
# Schreibe deinen Code hier, der das Ergebnis reproduzieren soll
# Achte darauf, die untere Zelle nicht auszuführen, sonst
# wirst du das Ergebnis nicht mehr sehen können
```


```python

```




    20




```python
# Schreibe deinen Code hier, der das Ergebnis reproduzieren soll
# Achte darauf, die untere Zelle nicht auszuführen, sonst
# wirst du das Ergebnis nicht mehr sehen können
```


```python

```




    array([[ 2],
           [ 7],
           [12]])




```python
# Schreibe deinen Code hier, der das Ergebnis reproduzieren soll
# Achte darauf, die untere Zelle nicht auszuführen, sonst
# wirst du das Ergebnis nicht mehr sehen können
```


```python

```




    array([21, 22, 23, 24, 25])




```python
# Schreibe deinen Code hier, der das Ergebnis reproduzieren soll
# Achte darauf, die untere Zelle nicht auszuführen, sonst
# wirst du das Ergebnis nicht mehr sehen können
```


```python

```




    array([[16, 17, 18, 19, 20],
           [21, 22, 23, 24, 25]])



## Mache jetzt folgendes

**Erzeuge die Summe aller Werte in der Matrix**


```python

```




    325



**Erhalte die Standardabweichung der Werte in der Matrix**


```python

```




    7.2111025509279782



**Erhalte die Summe aller Spalten in der Matrix**


```python

```




    array([55, 60, 65, 70, 75])



# Gut gemacht!

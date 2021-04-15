# NumPy

Quelle: Datamics

NumPy (oder Numpy) ist eine Lineare Algebra Library für Python. Dass sie so wichtig für Data Science mit Python ist, liegt daran, dass fast alle Libraries im PyData Ökosystem auf NumPy zurückgreifen.

NumPy ist außerdem extrem schnell, da es Anbindung an die C Library hat. Für mehr Informationen darüber, warum man Arrays statt Listen verwenden sollte, könnt ihr diesen tollen [StackOverflow Post](http://stackoverflow.com/questions/993984/why-numpy-instead-of-python-lists) lesen.

Wir werden nur die Grundlagen von NumPy lernen und es installieren, um damit arbeiten zu können.

## Installationsanleitung

**Ich empfehle ausdrücklich Python durch Verwendung der Anaconda Distribution zu installieren. So können wir sicher sein, dass alle zugrundeliegenden Notwendigkeiten (wie z.B. Lineare Algebara Libraries) installiert sind. Wenn ihr Anaconda nutzt, dann installiert NumPy, indem ihr zu eurem Terminal oder der Kommandozeile geht und eingebt:**

    conda install numpy
    
**Wenn du kein Anaconda nutzt und NumPy so nicht installieren kannst, dann schaue bitte in die [offizielle Dokumentation von Numpy.](http://docs.scipy.org/doc/numpy-1.10.1/user/install.html)**

## NumPy nutzen

Sobald wir NumPy installiert haben, können wir es als Library installieren:


```python
import numpy as np
```

NumPy bietet viele eingebaute Funktionen und Möglichkeiten. Wir werden nicht alle davon abdecken, sondern eine Vorauswahl der höchst relevanten Aspekte von Numpy betrachten: Vektoren, Arrays, Matrizen und Zahlen Erzeugung. Wir beginnen mit den Arrays:

## NumPy Arrays

NumPy Arrays sind die Sache, die wir am häufigsten von NumPy nutzen werden. NumPy Arrays gibt es in zwei verschiedenen Arten: Vektoren und Matrizen. Vektoren sind immer eindimensionale Arrays und Matrizen sind zweidimensional (können allerdings auch nur eine Spalte oder eine Zeile haben).

Lass uns damit beginnen zu untersuchen, wie wir Arrays mit NumPy erstellen.

### Arrays erstellen

#### Aus einer Python Liste

Wir können Arrays erstellen, indem wir sie direkt aus einer Liste konvertieren.


```python
meine_liste = [1,2,3]
meine_liste
```




    [1, 2, 3]




```python
np.array(meine_liste)
```




    array([1, 2, 3])




```python
meine_matrix = [[1,2,3],[4,5,6],[7,8,9]]
meine_matrix
```




    [[1, 2, 3], [4, 5, 6], [7, 8, 9]]




```python
np.array(meine_matrix)
```




    array([[1, 2, 3],
           [4, 5, 6],
           [7, 8, 9]])



### Eingebaute Methoden

#### arange

Gibt gleichmäßig verteilte Werte innerhalb eines Intervalls zurück.


```python
np.arange(0,10)
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])




```python
np.arange(0,11,2)
```




    array([ 0,  2,  4,  6,  8, 10])



#### zeros und ones

Erzeugt Arrays von Nullen oder Einsen


```python
np.zeros(3)
```




    array([ 0.,  0.,  0.])




```python
np.zeros((5,5))
```




    array([[ 0.,  0.,  0.,  0.,  0.],
           [ 0.,  0.,  0.,  0.,  0.],
           [ 0.,  0.,  0.,  0.,  0.],
           [ 0.,  0.,  0.,  0.,  0.],
           [ 0.,  0.,  0.,  0.,  0.]])




```python
np.ones(3)
```




    array([ 1.,  1.,  1.])




```python
np.ones((3,3))
```




    array([[ 1.,  1.,  1.],
           [ 1.,  1.,  1.],
           [ 1.,  1.,  1.]])



#### linspace

Gibt gleichmäßig verteilte Zahlen eines bestimmten Intervalls zurück.


```python
np.linspace(0,10,3)
```




    array([  0.,   5.,  10.])




```python
np.linspace(0,10,50)
```




    array([  0.        ,   0.20408163,   0.40816327,   0.6122449 ,
             0.81632653,   1.02040816,   1.2244898 ,   1.42857143,
             1.63265306,   1.83673469,   2.04081633,   2.24489796,
             2.44897959,   2.65306122,   2.85714286,   3.06122449,
             3.26530612,   3.46938776,   3.67346939,   3.87755102,
             4.08163265,   4.28571429,   4.48979592,   4.69387755,
             4.89795918,   5.10204082,   5.30612245,   5.51020408,
             5.71428571,   5.91836735,   6.12244898,   6.32653061,
             6.53061224,   6.73469388,   6.93877551,   7.14285714,
             7.34693878,   7.55102041,   7.75510204,   7.95918367,
             8.16326531,   8.36734694,   8.57142857,   8.7755102 ,
             8.97959184,   9.18367347,   9.3877551 ,   9.59183673,
             9.79591837,  10.        ])



#### eye

Erstellt eine Einheitsmatrix.


```python
np.eye(4)
```




    array([[ 1.,  0.,  0.,  0.],
           [ 0.,  1.,  0.,  0.],
           [ 0.,  0.,  1.,  0.],
           [ 0.,  0.,  0.,  1.]])



### Random

NumPy kann außerdem auf viele verschiedene Weisen Zufallszahlen erzeugen.

#### rand

Erstellt ein Array der gegebenen Form und füllt es mit Zufallszahlen einer Gleichverteilung über [0,1].


```python
np.random.rand(2)
```




    array([ 0.72229082,  0.08828056])




```python
np.random.rand(5,5)
```




    array([[ 0.0391439 ,  0.49292979,  0.24884482,  0.67526063,  0.80980052],
           [ 0.79761638,  0.75760951,  0.62291122,  0.9614057 ,  0.35169501],
           [ 0.63482038,  0.77748979,  0.02072133,  0.79381864,  0.22559012],
           [ 0.69879407,  0.1945143 ,  0.05460497,  0.05076038,  0.90568237],
           [ 0.40211974,  0.65469811,  0.18430184,  0.40719576,  0.18271866]])



#### randn

Gibt ein Sample (oder mehrere) einer "standard normal" Verteilung zurück. Anders als `rand`, dass gleichverteilt ist.


```python
np.random.randn(2)
```




    array([-1.0159284 ,  0.64170983])




```python
np.random.randn(3,3)
```




    array([[-1.55514171, -1.02596317,  0.4066948 ],
           [-0.04013328, -0.60941581, -0.67303581],
           [ 1.2308265 , -0.13921099,  1.5292816 ]])



#### randint

Gibt Zufallszahlen von `low`(inklusive) bis `high`(exklusive) zurück.


```python
np.random.randint(1,100)
```




    12




```python
np.random.randint(1,100,10)
```




    array([51,  3, 62, 56,  4, 48, 70, 98, 49, 32])



### Array Attribute und Methoden

Wir werden jetzt einige nützliche Attribute und Methoden von Arrays betrachten:


```python
arr = np.arange(25)
ranarr = np.random.randint(0,50,10)
```


```python
arr
```




    array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16,
           17, 18, 19, 20, 21, 22, 23, 24])




```python
ranarr
```




    array([ 2, 49, 12, 21,  7, 45, 14, 33, 44, 44])



#### Reshape

Gibt ein Array zurück, das dieselben Daten in neuer Form enthält.


```python
arr.reshape(5,5)
```




    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
           [10, 11, 12, 13, 14],
           [15, 16, 17, 18, 19],
           [20, 21, 22, 23, 24]])



#### max, min, argmax, argmin

Diese Methoden sind nützlich, um Mindest- oder Höchstwerte zu finden. Oder dafür, deren Index zu finden.


```python
ranarr
```




    array([ 2, 49, 12, 21,  7, 45, 14, 33, 44, 44])




```python
ranarr.max()
```




    49




```python
ranarr.argmax()
```




    1




```python
ranarr.min()
```




    2




```python
ranarr.argmin()
```




    0



#### Shape

Shape ist eines der Attribute, die Arrays haben. Es ist keine Methode.


```python
# Vektor
arr.shape
```




    (25,)




```python
# Achte auf die zwei Paare von Klammern
arr.reshape(1,25)
```




    array([[ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16,
            17, 18, 19, 20, 21, 22, 23, 24]])




```python
arr.reshape(1,25).shape
```




    (1, 25)




```python
arr.reshape(25,1)
```




    array([[ 0],
           [ 1],
           [ 2],
           [ 3],
           [ 4],
           [ 5],
           [ 6],
           [ 7],
           [ 8],
           [ 9],
           [10],
           [11],
           [12],
           [13],
           [14],
           [15],
           [16],
           [17],
           [18],
           [19],
           [20],
           [21],
           [22],
           [23],
           [24]])




```python
arr.reshape(25,1).shape
```




    (25, 1)



#### dtype

Du kannst außerdem den Datentyp des Objekts in einem Array feststellen:


```python
arr.dtype
```




    dtype('int64')



# Gut gemacht!

# NumPy Operations

Quelle: Datamics

## Arithmetik

Wir können einfach Array mit Array Arithmetik durchführen. Hier einige Beispiele:


```python
import numpy as np
arr = np.arange(0,10)
```


```python
arr + arr
```




    array([ 0,  2,  4,  6,  8, 10, 12, 14, 16, 18])




```python
arr * arr
```




    array([ 0,  1,  4,  9, 16, 25, 36, 49, 64, 81])




```python
arr - arr
```




    array([0, 0, 0, 0, 0, 0, 0, 0, 0, 0])




```python
# Bei Division durch Null gibt es nur eine Warnung, keinen Error!
# Das "Ergebnis" wird durch "nan" ersetzt
arr/arr
```

    /Users/davidmika/anaconda/envs/python3/lib/python3.6/site-packages/ipykernel_launcher.py:3: RuntimeWarning: invalid value encountered in true_divide
      This is separate from the ipykernel package so we can avoid doing imports until





    array([ nan,   1.,   1.,   1.,   1.,   1.,   1.,   1.,   1.,   1.])




```python
# Ebenso eine Warnung, aber kein Error bei Unendlichkeit
1/arr
```

    /Users/davidmika/anaconda/envs/python3/lib/python3.6/site-packages/ipykernel_launcher.py:2: RuntimeWarning: divide by zero encountered in true_divide
      





    array([        inf,  1.        ,  0.5       ,  0.33333333,  0.25      ,
            0.2       ,  0.16666667,  0.14285714,  0.125     ,  0.11111111])




```python
arr**3
```




    array([  0,   1,   8,  27,  64, 125, 216, 343, 512, 729])



## Universelle Array Funktionen

NumPy beinhaltet viele [universelle Array Funktionen](http://docs.scipy.org/doc/numpy/reference/ufuncs.html), die im Grunde eigentlich nur mathematische Operationen sind, die man auf ein ganzes Array anwenden kann. Schauen wir uns einige  übliche Beispiele an:


```python
# Die Quadratwurzel ziehen
np.sqrt(arr)
```




    array([ 0.        ,  1.        ,  1.41421356,  1.73205081,  2.        ,
            2.23606798,  2.44948974,  2.64575131,  2.82842712,  3.        ])




```python
# Den Exponent (e^) berechnen
np.exp(arr)
```




    array([  1.00000000e+00,   2.71828183e+00,   7.38905610e+00,
             2.00855369e+01,   5.45981500e+01,   1.48413159e+02,
             4.03428793e+02,   1.09663316e+03,   2.98095799e+03,
             8.10308393e+03])




```python
np.max(arr) # was das gleiche ist wie arr.max()
```




    9




```python
np.sin(arr)
```




    array([ 0.        ,  0.84147098,  0.90929743,  0.14112001, -0.7568025 ,
           -0.95892427, -0.2794155 ,  0.6569866 ,  0.98935825,  0.41211849])




```python
np.log(arr)
```

    /Users/davidmika/anaconda/envs/python3/lib/python3.6/site-packages/ipykernel_launcher.py:1: RuntimeWarning: divide by zero encountered in log
      """Entry point for launching an IPython kernel.





    array([       -inf,  0.        ,  0.69314718,  1.09861229,  1.38629436,
            1.60943791,  1.79175947,  1.94591015,  2.07944154,  2.19722458])



# Gut gemacht!

Das ist alles, was wir bis hierher benötigen!

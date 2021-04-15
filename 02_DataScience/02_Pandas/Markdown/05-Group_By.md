# Group By

Quelle: Datamics

Die `groupby` Methode (dt. gruppieren nach) erlaubt es uns Zeilen zu gruppieren und Aggregationsfunktionen aufzurufen.


```python
import pandas as pd
# Data Frame erstellen
data = {'Firma':['GOOG','GOOG','MSFT','MSFT','FB','FB'],
       'Person':['Sam','Charlie','Amy','Vanessa','Carl','Sarah'],
       'Sales':[200,120,340,124,243,350]}
```


```python
df = pd.DataFrame(data)
```


```python
df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Firma</th>
      <th>Person</th>
      <th>Sales</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>GOOG</td>
      <td>Sam</td>
      <td>200</td>
    </tr>
    <tr>
      <th>1</th>
      <td>GOOG</td>
      <td>Charlie</td>
      <td>120</td>
    </tr>
    <tr>
      <th>2</th>
      <td>MSFT</td>
      <td>Amy</td>
      <td>340</td>
    </tr>
    <tr>
      <th>3</th>
      <td>MSFT</td>
      <td>Vanessa</td>
      <td>124</td>
    </tr>
    <tr>
      <th>4</th>
      <td>FB</td>
      <td>Carl</td>
      <td>243</td>
    </tr>
    <tr>
      <th>5</th>
      <td>FB</td>
      <td>Sarah</td>
      <td>350</td>
    </tr>
  </tbody>
</table>
</div>



**Jetzt könne wir die .groupby() Methode nutzen, um Zeilen zu gruppieren.**

Dies geschieht nach einem Zeilennamen. Zum Beispiel können wir nach der Firma gruppieren. Das erzeugt ein `DataFrameGroupBy`
Objekt.


```python
df.groupby('Firma')
```




    <pandas.core.groupby.DataFrameGroupBy object at 0x10c9023c8>



Wir können dieses Objekt als neue Variable speichern:


```python
nach_firma = df.groupby('Firma')
```

Dadurch können wir Aggregationsmethoden anwenden:


```python
nach_firma.mean()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Sales</th>
    </tr>
    <tr>
      <th>Firma</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>FB</th>
      <td>296.5</td>
    </tr>
    <tr>
      <th>GOOG</th>
      <td>160.0</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>232.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.groupby('Firma').mean()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Sales</th>
    </tr>
    <tr>
      <th>Firma</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>FB</th>
      <td>296.5</td>
    </tr>
    <tr>
      <th>GOOG</th>
      <td>160.0</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>232.0</td>
    </tr>
  </tbody>
</table>
</div>



Weitere Beispiele für Aggregationsmethoden:


```python
nach_firma.std()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Sales</th>
    </tr>
    <tr>
      <th>Firma</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>FB</th>
      <td>75.660426</td>
    </tr>
    <tr>
      <th>GOOG</th>
      <td>56.568542</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>152.735065</td>
    </tr>
  </tbody>
</table>
</div>




```python
nach_firma.min()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Person</th>
      <th>Sales</th>
    </tr>
    <tr>
      <th>Firma</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>FB</th>
      <td>Carl</td>
      <td>243</td>
    </tr>
    <tr>
      <th>GOOG</th>
      <td>Charlie</td>
      <td>120</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>Amy</td>
      <td>124</td>
    </tr>
  </tbody>
</table>
</div>




```python
nach_firma.max()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Person</th>
      <th>Sales</th>
    </tr>
    <tr>
      <th>Firma</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>FB</th>
      <td>Sarah</td>
      <td>350</td>
    </tr>
    <tr>
      <th>GOOG</th>
      <td>Sam</td>
      <td>200</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>Vanessa</td>
      <td>340</td>
    </tr>
  </tbody>
</table>
</div>




```python
nach_firma.count()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Person</th>
      <th>Sales</th>
    </tr>
    <tr>
      <th>Firma</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>FB</th>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>GOOG</th>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>2</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
nach_firma.describe()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th colspan="8" halign="left">Sales</th>
    </tr>
    <tr>
      <th></th>
      <th>count</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>25%</th>
      <th>50%</th>
      <th>75%</th>
      <th>max</th>
    </tr>
    <tr>
      <th>Firma</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>FB</th>
      <td>2.0</td>
      <td>296.5</td>
      <td>75.660426</td>
      <td>243.0</td>
      <td>269.75</td>
      <td>296.5</td>
      <td>323.25</td>
      <td>350.0</td>
    </tr>
    <tr>
      <th>GOOG</th>
      <td>2.0</td>
      <td>160.0</td>
      <td>56.568542</td>
      <td>120.0</td>
      <td>140.00</td>
      <td>160.0</td>
      <td>180.00</td>
      <td>200.0</td>
    </tr>
    <tr>
      <th>MSFT</th>
      <td>2.0</td>
      <td>232.0</td>
      <td>152.735065</td>
      <td>124.0</td>
      <td>178.00</td>
      <td>232.0</td>
      <td>286.00</td>
      <td>340.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
nach_firma.describe().transpose()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Firma</th>
      <th>FB</th>
      <th>GOOG</th>
      <th>MSFT</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="8" valign="top">Sales</th>
      <th>count</th>
      <td>2.000000</td>
      <td>2.000000</td>
      <td>2.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>296.500000</td>
      <td>160.000000</td>
      <td>232.000000</td>
    </tr>
    <tr>
      <th>std</th>
      <td>75.660426</td>
      <td>56.568542</td>
      <td>152.735065</td>
    </tr>
    <tr>
      <th>min</th>
      <td>243.000000</td>
      <td>120.000000</td>
      <td>124.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>269.750000</td>
      <td>140.000000</td>
      <td>178.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>296.500000</td>
      <td>160.000000</td>
      <td>232.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>323.250000</td>
      <td>180.000000</td>
      <td>286.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>350.000000</td>
      <td>200.000000</td>
      <td>340.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
nach_firma.describe().transpose()['GOOG']
```




    Sales  count      2.000000
           mean     160.000000
           std       56.568542
           min      120.000000
           25%      140.000000
           50%      160.000000
           75%      180.000000
           max      200.000000
    Name: GOOG, dtype: float64



# Gut gemacht!

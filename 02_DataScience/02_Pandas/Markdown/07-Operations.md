# Operations

Quelle: Datamics

Es gibt einige weitere nützliche Operationen, die aber nicht in eine bestimmte Kategorie fallen. Diesen ist diese Lektion gewidmet.


```python
import pandas as pd
df = pd.DataFrame({'spa1':[1,2,3,4],'spa2':[444,555,666,444],'spa3':['abc','def','ghi','xyz']})
df.head()
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
      <th>spa1</th>
      <th>spa2</th>
      <th>spa3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>444</td>
      <td>abc</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>555</td>
      <td>def</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>666</td>
      <td>ghi</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>444</td>
      <td>xyz</td>
    </tr>
  </tbody>
</table>
</div>



## Information über Unique Values (dt. einzigartige Werte)


```python
df['spa2'].unique()
```




    array([444, 555, 666])




```python
df['spa2'].nunique()
```




    3




```python
df['spa2'].value_counts()
```




    444    2
    555    1
    666    1
    Name: spa2, dtype: int64



## Daten wählen


```python
# Vom Data Frame durch Bedingungen von mehreren Spalten auswählen
newdf = df[(df['spa1']>2) & (df['spa2']==444)]
```


```python
newdf
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
      <th>spa1</th>
      <th>spa2</th>
      <th>spa3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>444</td>
      <td>xyz</td>
    </tr>
  </tbody>
</table>
</div>



## Funktionen anwenden


```python
def mal2(x):
    return x*2
```


```python
df['spa1'].apply(mal2)
```




    0    2
    1    4
    2    6
    3    8
    Name: spa1, dtype: int64




```python
df['spa3'].apply(len)
```




    0    3
    1    3
    2    3
    3    3
    Name: spa3, dtype: int64




```python
df['spa1'].sum()
```




    10



## Spalten dauerhaft entfernen


```python
del df["spa1"]
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
      <th>spa2</th>
      <th>spa3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>444</td>
      <td>abc</td>
    </tr>
    <tr>
      <th>1</th>
      <td>555</td>
      <td>def</td>
    </tr>
    <tr>
      <th>2</th>
      <td>666</td>
      <td>ghi</td>
    </tr>
    <tr>
      <th>3</th>
      <td>444</td>
      <td>xyz</td>
    </tr>
  </tbody>
</table>
</div>



## Spalten und Index Namen erhalten


```python
df.columns
```




    Index(['spa2', 'spa3'], dtype='object')




```python
df.index
```




    RangeIndex(start=0, stop=4, step=1)



## Einen Data Frame sortieren und ordnen


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
      <th>spa2</th>
      <th>spa3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>444</td>
      <td>abc</td>
    </tr>
    <tr>
      <th>1</th>
      <td>555</td>
      <td>def</td>
    </tr>
    <tr>
      <th>2</th>
      <td>666</td>
      <td>ghi</td>
    </tr>
    <tr>
      <th>3</th>
      <td>444</td>
      <td>xyz</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.sort_values(by='spa2') #inplace=False per Standard
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
      <th>spa2</th>
      <th>spa3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>444</td>
      <td>abc</td>
    </tr>
    <tr>
      <th>3</th>
      <td>444</td>
      <td>xyz</td>
    </tr>
    <tr>
      <th>1</th>
      <td>555</td>
      <td>def</td>
    </tr>
    <tr>
      <th>2</th>
      <td>666</td>
      <td>ghi</td>
    </tr>
  </tbody>
</table>
</div>



## Nullwerte finden bzw. darauf prüfen


```python
df.isnull()
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
      <th>spa2</th>
      <th>spa3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>False</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Zeilen mit NaN Werten fallen lassen
df.dropna()
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
      <th>spa2</th>
      <th>spa3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>444</td>
      <td>abc</td>
    </tr>
    <tr>
      <th>1</th>
      <td>555</td>
      <td>def</td>
    </tr>
    <tr>
      <th>2</th>
      <td>666</td>
      <td>ghi</td>
    </tr>
    <tr>
      <th>3</th>
      <td>444</td>
      <td>xyz</td>
    </tr>
  </tbody>
</table>
</div>



### Nullwerte mit etwas Anderem füllen


```python
import numpy as np
```


```python
df = pd.DataFrame({'spa1':[1,2,3,np.nan],
                   'spa2':[np.nan,555,666,444],
                   'spa3':['abc','def','ghi','xyz']})
df.head()
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
      <th>spa1</th>
      <th>spa2</th>
      <th>spa3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>NaN</td>
      <td>abc</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2.0</td>
      <td>555.0</td>
      <td>def</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
      <td>666.0</td>
      <td>ghi</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>444.0</td>
      <td>xyz</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.fillna('FILL')
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
      <th>spa1</th>
      <th>spa2</th>
      <th>spa3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>FILL</td>
      <td>abc</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>555</td>
      <td>def</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>666</td>
      <td>ghi</td>
    </tr>
    <tr>
      <th>3</th>
      <td>FILL</td>
      <td>444</td>
      <td>xyz</td>
    </tr>
  </tbody>
</table>
</div>



# Pivotieren


```python
data = {'A':['foo','foo','foo','bar','bar','bar'],
     'B':['one','one','two','two','one','one'],
       'C':['x','y','x','y','x','y'],
       'D':[1,3,2,5,4,1]}

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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>foo</td>
      <td>one</td>
      <td>x</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>foo</td>
      <td>one</td>
      <td>y</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>foo</td>
      <td>two</td>
      <td>x</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>bar</td>
      <td>two</td>
      <td>y</td>
      <td>5</td>
    </tr>
    <tr>
      <th>4</th>
      <td>bar</td>
      <td>one</td>
      <td>x</td>
      <td>4</td>
    </tr>
    <tr>
      <th>5</th>
      <td>bar</td>
      <td>one</td>
      <td>y</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.pivot_table(values='D',index=['A', 'B'],columns=['C'])
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
      <th>C</th>
      <th>x</th>
      <th>y</th>
    </tr>
    <tr>
      <th>A</th>
      <th>B</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">bar</th>
      <th>one</th>
      <td>4.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>two</th>
      <td>NaN</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">foo</th>
      <th>one</th>
      <td>1.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>two</th>
      <td>2.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



# Gut gemacht!

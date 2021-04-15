# Missing Data und Imputation

Quelle: Datamics

Dieses Problem der fehlenden Daten tritt relativ häufig auf:
-  unvollständige Datensätze aufgrund technischer Pannen oder eines Datenverlustes
-  wenn einige befragte Personen aufgrund mangelnden Wissens oder unzureichender Antwortmotivation auf bestimmte Fragen bewusst keine Antwort geben 

Nun werden wir einige der üblichen Wege (z.B. Eliminierungsverfahren und Imputation) kennenlernen, um mit *Missing Data* (dt. fehlenden Daten) umzugehen. 


```python
import numpy as np
import pandas as pd
```


```python
df = pd.DataFrame({'A':[1,2,np.nan],
                  'B':[5,np.nan,np.nan],
                  'C':[1,2,3]})
```


```python
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>5.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2.0</td>
      <td>NaN</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>



# Eliminierungsverfahren

Das Eliminierungsverfahren (auch: Complete-case analysis) zählt zu den gängigen Missing-Data-Techniken. Dabei werden sämtliche Datensätze, bei denen eines oder mehrere Erhebungsmerkmale fehlende Werte aufweisen, aus der Datenmatrix gestrichen. Dieses Verfahren ist zwar sehr einfach, hat aber erhebliche Nachteile: 
1. Insbesondere hat es einen erheblichen Informationsverlust zur Folge.
1. Ferner kann diese Technik zu einer Verfälschung der verbleibenden Stichprobe führen. Als häufiges Beispiel gelten Umfragen bezüglich des Einkommens, bei denen es durchaus vorkommen kann, dass gerade Personen mit einem relativ hohen Einkommen dieses ungerne angeben und es daher in solchen Fällen tendenziell zu Missing Data kommt. 


```python
df.dropna()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>5.0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.dropna(axis=1)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.dropna(thresh=2)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>5.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2.0</td>
      <td>NaN</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>



# Imputation

Um dieses Problem der Eliminierungsverfahren möglichst in den Griff zu bekommen, wurden Imputationsverfahren entwickelt, bei denen versucht wird, fehlende Daten nicht einfach zu ignorieren, sondern stattdessen durch plausible Werte zu ersetzen, die unter anderem mit Hilfe der beobachteten Werte des gleichen Datensatzes geschätzt werden können.


```python
df.fillna(value='Füllwert')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>5</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Füllwert</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Füllwert</td>
      <td>Füllwert</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['A'].fillna(value=df['A'].mean())
```




    0    1.0
    1    2.0
    2    1.5
    Name: A, dtype: float64



# Gut gemacht!

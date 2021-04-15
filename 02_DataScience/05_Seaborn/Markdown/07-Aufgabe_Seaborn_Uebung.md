# Seaborn Übung - Aufgabe

Quelle: Datamics

Zeit unsere neu gelernten Seaborn Fähigkeiten anzuwenden! Versucht die gezeigten Diagramme selbst nachzustellen. Dabei ist die Farbgebung nicht entscheidend, es geht um die Inhalte.
## Die Daten
Wir werde dazu ein berühmten Datensatz zur Titanic benutzen. Später im Machine Learning Teil des Kurses kommen wir auf diesen Datensatz zurück, um Überlebenswahrscheinlichkeiten zu berechnen.


```python
import seaborn as sns
import matplotlib.pyplot as plt
%matplotlib inline
```


```python
titanic = sns.load_dataset('titanic')
```


```python
titanic.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>survived</th>
      <th>pclass</th>
      <th>sex</th>
      <th>age</th>
      <th>sibsp</th>
      <th>parch</th>
      <th>fare</th>
      <th>embarked</th>
      <th>class</th>
      <th>who</th>
      <th>adult_male</th>
      <th>deck</th>
      <th>embark_town</th>
      <th>alive</th>
      <th>alone</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>7.2500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>71.2833</td>
      <td>C</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Cherbourg</td>
      <td>yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>3</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>7.9250</td>
      <td>S</td>
      <td>Third</td>
      <td>woman</td>
      <td>False</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>53.1000</td>
      <td>S</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>8.0500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



## Übung
Versucht die gezeigten Diagramme selbst nachzustellen. Dabei ist die Farbgebung nicht entscheidend, es geht um die Inhalte.

Achtet außerdem darauf, die Zelle direkt über dem Diagramm nicht zu verwenden. So könnt ihr verhindern, dass das Diagramm verloren geht. Wir haben eine extra Zelle zum Coden eingebaut.


```python
# Hier eigenen Code schreiben
# Nächste Zelle nicht nutzen
```


```python

```




    <seaborn.axisgrid.JointGrid at 0x1098d8a20>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/07-Aufgabe_Seaborn_Uebung_6_1.png)
    



```python
# Hier eigenen Code schreiben
# Nächste Zelle nicht nutzen
```


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x110e14550>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/07-Aufgabe_Seaborn_Uebung_8_1.png)
    



```python
# Hier eigenen Code schreiben
# Nächste Zelle nicht nutzen
```


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x1111b7fd0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/07-Aufgabe_Seaborn_Uebung_10_1.png)
    



```python
# Hier eigenen Code schreiben
# Nächste Zelle nicht nutzen
```


```python
sns.swarmplot(x='class', y='age', data=titanic, palette='Set2')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x119006f60>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/07-Aufgabe_Seaborn_Uebung_12_1.png)
    



```python
# Hier eigenen Code schreiben
# Nächste Zelle nicht nutzen
```


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x11132d080>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/07-Aufgabe_Seaborn_Uebung_14_1.png)
    



```python
# Hier eigenen Code schreiben
# Nächste Zelle nicht nutzen
```


```python

```




    <matplotlib.text.Text at 0x1115a2198>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/07-Aufgabe_Seaborn_Uebung_16_1.png)
    



```python
# Hier eigenen Code schreiben
# Nächste Zelle nicht nutzen
```


```python
g = sns.FacetGrid(data=titanic, col='sex')
g.map(sns.distplot,'age')
```




    <seaborn.axisgrid.FacetGrid at 0x119673cf8>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/07-Aufgabe_Seaborn_Uebung_18_1.png)
    


# Gut gemacht!

Das sei soweit genug. Wir werden Seaborn noch viel mehr verwenden, sobald wir zum Machine Learning Teil des Kurses gekommen sind!

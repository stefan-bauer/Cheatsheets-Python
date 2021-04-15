# Grids

Quelle: Datamics

Grids sind ein recht allgemeiner Typ von Plots, die es uns erlauben mehrerer Diagramme entlang von Zeilen und Spalten darzustelen. Das hilft besonders dabei gleiche Diagramme zu erstellen, die sich in Hinsicht auf einen Aspekt unterscheiden.


```python
import seaborn as sns
import matplotlib.pyplot as plt
%matplotlib inline
```


```python
iris = sns.load_dataset('iris')
```


```python
iris.head()
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
      <th>sepal_length</th>
      <th>sepal_width</th>
      <th>petal_length</th>
      <th>petal_width</th>
      <th>species</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.6</td>
      <td>3.1</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
      <td>3.6</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>setosa</td>
    </tr>
  </tbody>
</table>
</div>



## PairGrid
*Pairgrid* ist ein Subplot mit dem wir paarweise Bezeihungen in einem Datensatz anzeigenkönnen.


```python
# Das reine Grid
sns.PairGrid(iris)
```




    <seaborn.axisgrid.PairGrid at 0x11a04c940>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/05-Grids_5_1.png)
    



```python
# Dann können wir auf dem Grid zeichnen
g = sns.PairGrid(iris)
g.map(plt.scatter)
```




    <seaborn.axisgrid.PairGrid at 0x11dd93b00>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/05-Grids_6_1.png)
    



```python
# Platzierungen mit upper, lower und diagonal
g = sns.PairGrid(iris)
g.map_diag(plt.hist)
g.map_upper(plt.scatter)
g.map_lower(sns.kdeplot)
```




    <seaborn.axisgrid.PairGrid at 0x11e768fd0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/05-Grids_7_1.png)
    


## pairplot

Das *pairplot* ist eine einfachere Version des PairGrid


```python
sns.pairplot(iris)
```




    <seaborn.axisgrid.PairGrid at 0x11e7ed860>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/05-Grids_9_1.png)
    



```python
sns.pairplot(iris,hue='species',palette='rainbow')
```




    <seaborn.axisgrid.PairGrid at 0x1208380b8>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/05-Grids_10_1.png)
    


## FacetGrid

*FacetGrid* ist der allgemeine Weg, um eine Vielzahl an Diagrammen in einem Grid zu erstellen:


```python
tips = sns.load_dataset('tips')
```


```python
tips.head()
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
      <th>total_bill</th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
      <th>day</th>
      <th>time</th>
      <th>size</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16.99</td>
      <td>1.01</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10.34</td>
      <td>1.66</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>21.01</td>
      <td>3.50</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>23.68</td>
      <td>3.31</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>24.59</td>
      <td>3.61</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Nur das Grid
g = sns.FacetGrid(tips, col="time", row="smoker")
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/05-Grids_14_0.png)
    



```python
g = sns.FacetGrid(tips, col="time",  row="smoker")
g = g.map(plt.hist, "total_bill")
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/05-Grids_15_0.png)
    



```python
g = sns.FacetGrid(tips, col="time",  row="smoker",hue='sex')
# Achtet darauf, dass die Argumente nach plt.scatter geschrieben werden
g = g.map(plt.scatter, "total_bill", "tip").add_legend()
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/05-Grids_16_0.png)
    


## JointGrid
JointGrid ist die allgemeine Version für `jointplot()` Grids. Ein einfaches Beispiel:


```python
g = sns.JointGrid(x="total_bill", y="tip", data=tips)
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/05-Grids_18_0.png)
    



```python
g = sns.JointGrid(x="total_bill", y="tip", data=tips)
g = g.plot(sns.regplot, sns.distplot)
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/05-Grids_19_0.png)
    


# Gut gemacht!

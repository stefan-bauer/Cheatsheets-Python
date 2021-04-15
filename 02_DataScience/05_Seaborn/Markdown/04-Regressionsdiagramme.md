# Regression Plots

Quelle: Datamics

Seaborn hat viele eingebaute Fähigkeiten um Diagramme für Regressionen zu erstellen. Jedoch werden wir Regressionen erst richtig im Machine Learning Teil des Kurses besprechen. Deshalb werden wir an dieser Stelle nur die `lmplot()` Funktion kennenlernen.

*lmplot* ermöglicht es uns lineare Modelle zu visualisieren. Zusätzlich werden aber auch Funktionen zum Aufteilen und Einfärben von Daten anhand einzelner Variablen gegeben. Schauen wir uns das im Detail an!


```python
import seaborn as sns
%matplotlib inline
```


```python
tips = sns.load_dataset("tips")
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



## lmplot()


```python
sns.lmplot(x="total_bill",y="tip", data=tips)
```




    <seaborn.axisgrid.FacetGrid at 0x10f962208>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/04-Regressionsdiagramme_5_1.png)
    



```python
sns.lmplot(x='total_bill',y='tip',data=tips,hue='sex')
```




    <seaborn.axisgrid.FacetGrid at 0x112d47dd8>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/04-Regressionsdiagramme_6_1.png)
    



```python
sns.lmplot(x='total_bill',y='tip',data=tips,hue='sex',palette='coolwarm')
```




    <seaborn.axisgrid.FacetGrid at 0x112e03fd0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/04-Regressionsdiagramme_7_1.png)
    


### Mit Markierungen arbeiten
lmplot wird durch *regplot* verarbeitet. Das ist einfach eine etwas allgemeinere Form des *lmplot*. *regplot* wiederum hat einen `scatter_kws` Parameter. Innerhalb dessen definieren wir *s* in einem Dictionary, um die Markierungsgröße festzulegen (etwas verwirrend).


```python
# http://matplotlib.org/api/markers_api.html
sns.lmplot(x='total_bill',y='tip',data=tips,hue='sex',palette='coolwarm',
           markers=['o','v'],scatter_kws={'s':100})
```




    <seaborn.axisgrid.FacetGrid at 0x11316d2b0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/04-Regressionsdiagramme_9_1.png)
    


## Ein Grid nutzen

Wir können weitere Differenzierung durch Spalten und Zeilen hinzufügen, indem wir ein Grid nutzen. Dazu einfach die `col` und `row` Parameter spezifizieren:


```python
sns.lmplot(x='total_bill',y='tip',data=tips,col='sex')
```




    <seaborn.axisgrid.FacetGrid at 0x112cadda0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/04-Regressionsdiagramme_11_1.png)
    



```python
sns.lmplot(x="total_bill", y="tip", row="sex", col="time",data=tips)
```




    <seaborn.axisgrid.FacetGrid at 0x1135991d0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/04-Regressionsdiagramme_12_1.png)
    



```python
sns.lmplot(x='total_bill',y='tip',data=tips,col='day',hue='sex',palette='coolwarm')
```




    <seaborn.axisgrid.FacetGrid at 0x1138a9f98>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/04-Regressionsdiagramme_13_1.png)
    


## Perspektive und Größe
Seaborn Diagramme können in ihrer Größe und Perspektive angepasst werden:


```python
sns.lmplot(x='total_bill',y='tip',data=tips,col='day',hue='sex',palette='coolwarm',
          aspect=0.6,size=8)
```




    <seaborn.axisgrid.FacetGrid at 0x1144bb390>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/04-Regressionsdiagramme_15_1.png)
    


Ihr wundert euch evtl. wie sich Schriftgröße und andere optische Aspekte anpassen lassen. Dazu gibt es die Lektion "Style und Farbe"!
# Gut gemacht!

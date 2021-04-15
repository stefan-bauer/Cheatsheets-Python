# Kategorische (Daten) Plots

Quelle: Datamics

Als nächstes können wir *seaborn* dazu verwenden, um kategorische Daten zu visualisieren. Dafür gibt es einige wesentliche Diagramme:
* factorplot
* boxplot
* violinplot
* stripplot
* swarmplot
* barplot
* countplot

Wir können uns zu jedem davon ein Beispiel anschauen!


```python
import seaborn as sns
%matplotlib inline
```


```python
tips = sns.load_dataset("tips")
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



## barplot

*barplot* ist ein Diagramm, das uns erlaubt die kategorischen Daten gegeben einer Funktion zu aggregieren. Per Standard ist dies der Durchschnitt.


```python
sns.barplot(x="sex",y="total_bill",data=tips)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1171d7b00>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/02-Kategorische_Plots_4_1.png)
    



```python
import numpy as np
```

Wir können außerdem den Schätzer zu unserer eigenen Funktion ändern:


```python
sns.barplot(x="sex", y="total_bill", data=tips, estimator=np.std)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11a5157b8>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/02-Kategorische_Plots_7_1.png)
    


## countplot
Dieses Diagramm ist prinzipiell das selbe wie das *barplot*. Außer insofern, dass *countplot* die Anzahl (count) an Erscheinungen zählt. Deshalb übergeben wir auch nur einen x Wert:


```python
sns.countplot(x="sex",data=tips)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11a6700f0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/02-Kategorische_Plots_9_1.png)
    


## boxplot
*boxplots* (genau wie die danach folgenden *violinplots*) zeigen die Verteilung von kategorischen Daten. Ein *box plot* (oder box-and-whisker plot) zeigt die Verteilung von quantitativen Daten auf eine Art, die den Vergleich zwischen Variablen bzw. zwischen Werten einer kategorischen Varaiblen begünstigt. Die *box* zeigt die Quantile des Datensatzes während die *whiskers* den Rest der Verteilung zeigen. Ausgenommen sind Daten, die durch ein Inter-Quanti-Verfahren als Outlier (Ausreißer) eingestuft wurden.


```python
sns.boxplot(x="day",y="total_bill",data=tips,palette="rainbow")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11a8af828>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/02-Kategorische_Plots_11_1.png)
    



```python
# Außerdem können wir die Ausrichtung zu "horizontal" ändern
sns.boxplot(data=tips,palette="rainbow",orient="h")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11a9da668>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/02-Kategorische_Plots_12_1.png)
    



```python
sns.boxplot(x="day", y="total_bill", hue="smoker", data=tips, palette="coolwarm")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11a893c50>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/02-Kategorische_Plots_13_1.png)
    


## violinplot

Ein *violin plot* spielt eine ähnliche Rolle wie das *boxplot*. Es zeigt die Verteilung von quantitativen Daten entlang mehrerer Werte einer kategorischen Variablen. Anders als das *box plot*, in dem das Diagramm tatsächliche Datenpunkte repräsentiert, zeigt das *violin plot* eine KDE (en. Kernal density estimation) der zugrundeliegenden Verteilung.


```python
sns.violinplot(x="day", y="total_bill", data=tips, palette="rainbow")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11adbff98>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/02-Kategorische_Plots_15_1.png)
    



```python
sns.violinplot(x="day", y="total_bill", data=tips,hue='sex',palette='Set1')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11ae8c748>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/02-Kategorische_Plots_16_1.png)
    



```python
sns.violinplot(x="day", y="total_bill", data=tips,hue='sex',split=True,palette='Set1')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11b1e2390>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/02-Kategorische_Plots_17_1.png)
    


## stripplot

Das *stripplot* zeichnet ein Scatterplot, indem eine Variable katagorisch ist. Ein *strip plot* kann alleinstehend gezeichnet werden. Es passt aber auch gut zu einem *box* oder *violin plot*, wenn man neben der Verteilung auch alle einzelnen Datenpunkte visualisieren möchte.


```python
sns.stripplot(x="day", y="total_bill", data=tips)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11b370d30>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/02-Kategorische_Plots_19_1.png)
    



```python
sns.stripplot(x="day", y="total_bill", data=tips,jitter=True)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11b4a8e48>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/02-Kategorische_Plots_20_1.png)
    



```python
sns.stripplot(x="day", y="total_bill", data=tips,jitter=True,hue='sex',palette='Set1')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11b6a8b00>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/02-Kategorische_Plots_21_1.png)
    



```python
sns.stripplot(x="day", y="total_bill", data=tips,jitter=True,hue='sex',palette='Set1',dodge=True)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11b94ec50>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/02-Kategorische_Plots_22_1.png)
    


## swarmplot
Das *swarmplot* ist dem eben behandelten *stripplot* ähnlich. Der Unterschied liegt in der Anpassung der Punkte, so dass sie sich nicht überschneiden. Das gibt einen besseren Eindruck über die Verteilung der Punkte. Allerdings lässt sich das aus zwei Gründen nicht gut auf wirkich große Datenmengen skalieren. Erstens wird es schwer alle Punkte einzuzweichnen und zweitens alle Positionen zu berechnen.


```python
sns.swarmplot(x="day", y="total_bill", data=tips)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11bab2b00>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/02-Kategorische_Plots_24_1.png)
    



```python
sns.swarmplot(x="day", y="total_bill",hue='sex',data=tips, palette="Set1", dodge=True)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11bc6a668>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/02-Kategorische_Plots_25_1.png)
    


## Kategorische Plots kombinieren


```python
sns.violinplot(x="tip", y="day", data=tips,palette='rainbow')
sns.swarmplot(x="tip", y="day", data=tips,color='black',size=3)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11bbe1048>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/02-Kategorische_Plots_27_1.png)
    


## factorplot
Das *factorplot* ist die allgemeinste Form eines kategorischen Diagramms. Es verarbeitet einen `kind` Parameter, um die Diagrammart anzupassen:


```python
sns.factorplot(x='sex',y='total_bill',data=tips,kind='bar')
```




    <seaborn.axisgrid.FacetGrid at 0x11b96c8d0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/02-Kategorische_Plots_29_1.png)
    


# Gut gemacht!

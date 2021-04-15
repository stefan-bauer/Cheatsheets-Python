# Distribution (Verteilung) Plots

Quelle: Datamics

Lasst uns einige Plots diskutieren, die es uns erlauben die Verteilung von Daten in einem Datensatz zu visualisieren. Diese Diagramme sind:

* distplot
* jointplot
* pairplot
* rugplot
* kdeplot

## Installation & Imports

Bevor wir damit beginnen können installieren und/oder importieren wir *Seaborn*:

Zum Installieren gebt in eurer Kommandozeile bzw. eurem Terminal folgenden Befehl ein:

    conda install seaborn
    
Nach der Installation können wir *Seaborn* importieren:


```python
import seaborn as sns
%matplotlib inline
```

## Daten

*Seaborn* verfügt über eingebaute Datensets, die wir uns zunutze machen können! Der Datensatz den wir jetzt nutzen werden liegt in englischer Sprache vor und beschreibt Daten zum Trinkgeld in einem Restaurant.


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



## Distribution Plots
### distplot

Das *distplot* zeigt uns die Verteilung (en. Distribution) eines univariaten Satzes von Beobachtungen an.


```python
sns.distplot(tips["total_bill"])
```




    <matplotlib.axes._subplots.AxesSubplot at 0x10ca97908>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/01-Distribution_Plots_6_1.png)
    


Um nur das Histogramm anzuzeigen nutzen wir KDE (Kernel Density Estimation):


```python
sns.distplot(tips["total_bill"],kde=False,bins=30)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x10cbc5b38>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/01-Distribution_Plots_8_1.png)
    


### jointplot

`jointplot()` ermöglicht es im Grunde genommen zwei *distplots* zu vereinen, um bivariate Daten zu visualisieren. Dabei können wir eine Wahl der Art (en.: kind) der Darstellung treffen:

* scatter
* reg
* resid
* kde
* hex


```python
sns.jointplot(x="total_bill",y="tip",data=tips,kind="scatter")
```




    <seaborn.axisgrid.JointGrid at 0x10d7987b8>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/01-Distribution_Plots_10_1.png)
    



```python
sns.jointplot(x="total_bill",y="tip",data=tips,kind="hex")
```




    <seaborn.axisgrid.JointGrid at 0x10dd22da0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/01-Distribution_Plots_11_1.png)
    



```python
sns.jointplot(x="total_bill",y="tip",data=tips,kind="reg")
```




    <seaborn.axisgrid.JointGrid at 0x10e0c3198>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/01-Distribution_Plots_12_1.png)
    


### pairplot

Das Diagramm *pairplot* zeigt paarweise Beziehungen in einem kompletten Dataframe. Für kategorische Variablen können wir über das `hue` Argument die Farbe einstellen.


```python
sns.pairplot(tips)
```




    <seaborn.axisgrid.PairGrid at 0x10db06048>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/01-Distribution_Plots_14_1.png)
    



```python
sns.pairplot(tips,hue='sex',palette='coolwarm')
```




    <seaborn.axisgrid.PairGrid at 0x10e83f2e8>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/01-Distribution_Plots_15_1.png)
    


## rugplot

*rugplots* folgen eigentlich einem sehr simplen Konzept: Sie zeichnen einfach einen Strich für jeden Piunkt einer univariaten Verteilung. Sie sind ein Bestandteil eines KDE-Plots (den wir anschließend kennenlernen werden).


```python
sns.rugplot(tips['total_bill'])
```




    <matplotlib.axes._subplots.AxesSubplot at 0x10f577240>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/01-Distribution_Plots_17_1.png)
    


### kdeplot

*kdeplots* sind [Kerndichteschätzer](https://de.wikipedia.org/wiki/Kerndichtesch%C3%A4tzer) (en.: Kernel density estimation). Diese KDE Plots ersetzen jede einzelne Beobachtung mit einer Gausschen (Normal-) Verteilung, die am beobachteten Wert zentriert ist. Zum Beispiel:


```python
# Keine Sorge, ihr müsst diesen Code nicht verstehen!
# Er soll nur das nachfolgende Diagramm erzeugen
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats

#Datensatz erstellen
dataset = np.random.randn(25)

# Ein weiteres rugplot erstellen
sns.rugplot(dataset);

# Die x-Achse des Plot einstellen
x_min = dataset.min() - 2
x_max = dataset.max() + 2

# 100 gleich verteilte Punkte von x_min bis x_max
x_axis = np.linspace(x_min,x_max,100)

# Die Bandbreite (en.: bandwidth) einstellen. Mehr Infos zur Bandbreite:
url = 'https://de.wikipedia.org/wiki/Kerndichtesch%C3%A4tzer#Satz_von_Nadaraya'

bandwidth = ((4*dataset.std()**5)/(3*len(dataset)))**.2


# Eine leere Liste erstellen
kernel_list = []

# Jede Funktion visualisieren
for data_point in dataset:
    
    # Für jeden Punkt wird ein Kernel erstellt und der Liste angefügt
    kernel = stats.norm(data_point,bandwidth).pdf(x_axis)
    kernel_list.append(kernel)
    
    # Skalieren für die Darstellung
    kernel = kernel / kernel.max()
    kernel = kernel * .4
    plt.plot(x_axis,kernel,color = 'grey',alpha=0.5)

plt.ylim(0,1)
```




    (0, 1)




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/01-Distribution_Plots_19_1.png)
    



```python
# Um das KDE-Plot zu erhalten können wir diese Funktionen summieren.

# Zeiche die Summe der Basisfunktionen
sum_of_kde = np.sum(kernel_list,axis=0)

# Diagramm zeigen
fig = plt.plot(x_axis,sum_of_kde,color='indianred')

# Das erste rugplot hinzufügen
sns.rugplot(dataset,c = 'indianred')

# Die y-tick-Markierungen entfernen
plt.yticks([])

# Titel definieren
plt.suptitle("Summe der Basisfunktionen")
```




    <matplotlib.text.Text at 0x10fe89128>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/01-Distribution_Plots_20_1.png)
    


Mit unserem Trinkgeld-Datensatz:


```python
sns.kdeplot(tips['total_bill'])
sns.rugplot(tips['total_bill'])
```




    <matplotlib.axes._subplots.AxesSubplot at 0x10fe890f0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/01-Distribution_Plots_22_1.png)
    



```python
sns.kdeplot(tips['tip'])
sns.rugplot(tips['tip'])
```




    <matplotlib.axes._subplots.AxesSubplot at 0x113937c50>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/01-Distribution_Plots_23_1.png)
    


# Gut gemacht!

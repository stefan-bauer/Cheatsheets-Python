# Pandas eingebaute Data Visualization

Quelle: Datamics

In dieser Lektion werden wir mehr über die vorhandenen Visualisierungsmöglichkeiten von *Pandas* erfahren. 
Es basiert auf *Matplotlib*, ist aber direkt in Pandas verfügbar, um eine leichtere Handhabung zu gewährleisten.

Fangen wir an!

### Imports


```python
import numpy as np
import pandas as pd
%matplotlib inline
```

### Die Daten
Wir haben einige CSV-Dateien mit Daten die wir als Dataframes nutzen können:


```python
df1 = pd.read_csv("df1",index_col=0)
df2 = pd.read_csv("df2")
```

## Stylesheets
Matplotlib bietet [*Stylesheets*](http://matplotlib.org/gallery.html#style_sheets), die wir nutzen können, damit unsere Diagramme etwas besser aussehen. Wie werden einige beispielhaft betrachten. 

Wir empfehlen die Nutzung der Stylesheets, da sie allen Diagrammen einen einheitlichen Look verleihen. Außerdem ist es möglich eigene Stylesheets zu erstellen, um z.B. eine Firma zu repräsentieren.

Schauen wir uns jetzt die Nutzung an:

*Vor der Nutzung von plt.style.use():*


```python
df1['A'].hist()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x10e7ec1d0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/01-Pandas_eingebaute_Data_Visualization_5_1.png)
    


Jetzt nutzen wir das Stylesheet.


```python
import matplotlib.pyplot as plt
plt.style.use('ggplot')
```


```python
df1['A'].hist()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x10e5d15f8>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/01-Pandas_eingebaute_Data_Visualization_8_1.png)
    



```python
plt.style.use('bmh')
df1['A'].hist()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x111b78358>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/01-Pandas_eingebaute_Data_Visualization_9_1.png)
    



```python
plt.style.use('dark_background')
df1['A'].hist()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x111ce0a90>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/01-Pandas_eingebaute_Data_Visualization_10_1.png)
    



```python
plt.style.use('fivethirtyeight')
df1['A'].hist()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x111da8470>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/01-Pandas_eingebaute_Data_Visualization_11_1.png)
    



```python
plt.style.use('ggplot')
```

Belassen wir es jetzt bei dem *ggplot* Stylesheet und betrachten die tatsächlichen Visualisierungsmöglichkeiten von *Pandas*.

## Diagrammarten
Es gibt verschiedene eingebaute Visualisierungen in *Pandas*. Die meisten davon sind statistische Diagramme. Hier eine Übersicht:

* df.plot.area     
* df.plot.barh     
* df.plot.density  
* df.plot.hist     
* df.plot.line     
* df.plot.scatter
* df.plot.bar      
* df.plot.box      
* df.plot.hexbin   
* df.plot.kde      
* df.plot.pie

Wir können alternativ auch df.plot(kind="area") aufrufen.

Schauen wir uns nun alle Diagramme an:

### Area


```python
df2.plot.area(alpha=0.4)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x111da4e48>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/01-Pandas_eingebaute_Data_Visualization_15_1.png)
    


### Barplots


```python
df2.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.039762</td>
      <td>0.218517</td>
      <td>0.103423</td>
      <td>0.957904</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.937288</td>
      <td>0.041567</td>
      <td>0.899125</td>
      <td>0.977680</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.780504</td>
      <td>0.008948</td>
      <td>0.557808</td>
      <td>0.797510</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.672717</td>
      <td>0.247870</td>
      <td>0.264071</td>
      <td>0.444358</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.053829</td>
      <td>0.520124</td>
      <td>0.552264</td>
      <td>0.190008</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2.plot.bar()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x111f8fda0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/01-Pandas_eingebaute_Data_Visualization_18_1.png)
    



```python
df2.plot.bar(stacked=True)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1122b39b0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/01-Pandas_eingebaute_Data_Visualization_19_1.png)
    


### Histogramm


```python
df1['A'].plot.hist(bins=50)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1125383c8>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/01-Pandas_eingebaute_Data_Visualization_21_1.png)
    


### Line Plot


```python
df1.plot.line(x=df1.index,y='B',figsize=(12,3),lw=1)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1127699e8>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/01-Pandas_eingebaute_Data_Visualization_23_1.png)
    


### Scatter Plots


```python
df1.plot.scatter(x='A',y='B')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x111e42828>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/01-Pandas_eingebaute_Data_Visualization_25_1.png)
    


Wir können außer *c* nutzen, um die Punkte anhand einer dritten Variablen einzufärben. Dazu definieren wir `cmap` mit einer der [Colormaps](http://matplotlib.org/users/colormaps.html).


```python
df1.plot.scatter(x='A',y='B',c='C',cmap='coolwarm')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11290f7b8>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/01-Pandas_eingebaute_Data_Visualization_27_1.png)
    


Oder wir nutzen `s`, um die Größe (en. scale) der Punkte zu ändern. Der `s` Parameter muss ein Array sein. Wir sehen hier wie es geht:


```python
df1.plot.scatter(x='A',y='B',s=df1['C']*100)
```

    /Users/renebrunner/anaconda/lib/python3.6/site-packages/matplotlib/collections.py:877: RuntimeWarning: invalid value encountered in sqrt
      scale = np.sqrt(self._sizes) * dpi / 72.0 * self._factor





    <matplotlib.axes._subplots.AxesSubplot at 0x114b793c8>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/01-Pandas_eingebaute_Data_Visualization_29_2.png)
    


### Box Plots


```python
df2.plot.box() # Wir können mit by= auch gruppieren nach (en. group by)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x112c67f60>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/01-Pandas_eingebaute_Data_Visualization_31_1.png)
    


### Hexagonal Bin Plot
Eine nützliche Alternative zum Scatterplot für bivariate Daten:


```python
df = pd.DataFrame(np.random.randn(1000, 2), columns=['a', 'b'])
df.plot.hexbin(x='a',y='b',gridsize=25,cmap='Oranges')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x112aa07f0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/01-Pandas_eingebaute_Data_Visualization_33_1.png)
    


### Kernel Density Estimation (KDE) Plot


```python
df2['a'].plot.kde()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x11311a198>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/01-Pandas_eingebaute_Data_Visualization_35_1.png)
    



```python
df2.plot.density()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x114888160>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/01-Pandas_eingebaute_Data_Visualization_36_1.png)
    


Und damit hätten wir sie alle. Hoffentlich sehr ihr, dass diese Variante der Visualisierung leichter ist als komplette Matplotlib-Herangehensweise. Sie bietet eine gute Balance aus Einfachheit und Kontrolle. Außerdem können wir bei vielen der Diagramme noch weitere Parameter übergeben (genau wie bei ihren Matplotlib-Eltern-Diagramme).

# Gut gemacht!

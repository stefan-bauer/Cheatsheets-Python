# Pandas Data Visualization Übung - Lösung

Quelle: Datamics

Das ist eine kleine Übung zur Anwendung der eingebauten Visualisierungsmöglichkeiten in *Pandas*. Dazu nutzen wir das **df3** CSV. Bitte stellt die folgenden Diagramme durch nutzung von Pandas dar. Die Imports seien gegeben:


```python
import pandas as pd
import matplotlib.pyplot as plt
df3 = pd.read_csv('df3')
%matplotlib inline
```


```python
df3.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 500 entries, 0 to 499
    Data columns (total 4 columns):
    a    500 non-null float64
    b    500 non-null float64
    c    500 non-null float64
    d    500 non-null float64
    dtypes: float64(4)
    memory usage: 15.7 KB



```python
df3.head()
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
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.336272</td>
      <td>0.325011</td>
      <td>0.001020</td>
      <td>0.401402</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.980265</td>
      <td>0.831835</td>
      <td>0.772288</td>
      <td>0.076485</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.480387</td>
      <td>0.686839</td>
      <td>0.000575</td>
      <td>0.746758</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.502106</td>
      <td>0.305142</td>
      <td>0.768608</td>
      <td>0.654685</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.856602</td>
      <td>0.171448</td>
      <td>0.157971</td>
      <td>0.321231</td>
    </tr>
  </tbody>
</table>
</div>



**Erstelle dieses Scatter Plot von b vs. a. Achte auf die Farbe und Größe der Punkte. Versuche außerdem es in die vorgegebene Form zu bringen. Dazu könnte eine Auffrischung der Matplotlib-Befehle helfen.**


```python
df3.plot.scatter(x='a',y='b',c='red',s=50,figsize=(12,3))
```




    <matplotlib.axes._subplots.AxesSubplot at 0x10e8d29e8>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/03-Loesung_Pandas_Data_Visualization_Uebung_5_1.png)
    


**Erstelle ein Histogramm der "a" Spalte.**


```python
df3['a'].plot.hist()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x10e90aa20>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/03-Loesung_Pandas_Data_Visualization_Uebung_7_1.png)
    


**Diese Plots sind soweit gut. Sie sehen aber noch nicht einheitlich aus. Nutze das `ggplot` Stylesheet, um das Erscheinungsbild der folgenden Diagramme zu beeinflussen. Erstelle dann das Histogramm von eben erneut und füge zusätzlich mehr Teilbalken hinzu.**


```python
plt.style.use('ggplot')
```


```python
df3['a'].plot.hist(alpha=0.5,bins=25)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x111e13f60>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/03-Loesung_Pandas_Data_Visualization_Uebung_10_1.png)
    


**Erstelle ein Box Plot, dass die Spalten a und b vergleicht.**


```python
df3[['a','b']].plot.box()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x111fbffd0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/03-Loesung_Pandas_Data_Visualization_Uebung_12_1.png)
    


**Erstelle ein KDE Plot der Spalte "d".**


```python
df3['d'].plot.kde()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x111fd8748>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/03-Loesung_Pandas_Data_Visualization_Uebung_14_1.png)
    


**Finde heraus, wie wir die Linienbreite erhöhen und die Linie stricheln können.**

*Hinweis: Normalerweise würden wir ein KDE Diagramm nicht stricheln.*


```python
df3['d'].plot.density(lw=5,ls='--')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x113d8e9b0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/03-Loesung_Pandas_Data_Visualization_Uebung_16_1.png)
    


**Erstelle ein Flächendiagramm (en. area plot) für alle Spalten. Nutze dabei aber nur die ersten 30 Zeilen.**

*Hinweis: Für die Zeilen kannst du .iloc nutzen.*


```python
df3.iloc[0:30].plot.area(alpha=0.4)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1141a1550>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/03-Loesung_Pandas_Data_Visualization_Uebung_18_1.png)
    


## Bonus Aufgabe!
Das könnte wirklich schwer sein, weshalb es okay ist, sich auf die Lösung zu beziehen, wenn man nicht weiter kommt.

**Sicher fällt euch auf, dass die Legende in der vorherigen Lösung das eigentliche Diagramm überdeckt. Findest du einen Weg, um die Legende neben dem eigentlichen Diagramm anzuzeigen?**

*Hinweis: Google Suche nach einem guten Stackoverflow-Link zu diesem Thema hilft.*


```python
f = plt.figure()
df3.ix[0:30].plot.area(alpha=0.4,ax=f.gca())
plt.legend(loc='center left', bbox_to_anchor=(1.0, 0.5))
plt.show()
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/03-Loesung_Pandas_Data_Visualization_Uebung_20_0.png)
    


# Gut gemacht!

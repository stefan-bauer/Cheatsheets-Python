# Pandas Data Visualization Übung - Aufgabe

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

```


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x10e8d29e8>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/02-Aufgabe_Pandas_Data_Visualization_Uebung_6_1.png)
    


**Erstelle ein Histogramm der "a" Spalte.**


```python

```


```python
df3['a'].plot.hist()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x111dfc8d0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/02-Aufgabe_Pandas_Data_Visualization_Uebung_9_1.png)
    


**Diese Plots sind soweit okay. Sie sehen aber nicht einheitlich aus. Nutze das `ggplot` Stylesheet, um das Erscheinungsbild der folgenden Diagramme zu beeinflussen. Erstelle dann das Histogramm von eben erneut und füge zusätzlich mehr Teilbalken hinzu.**


```python
# Style hier
```


```python
# Plot hier
```


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x111e13f60>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/02-Aufgabe_Pandas_Data_Visualization_Uebung_13_1.png)
    


**Erstelle ein Box Plot, dass die Spalten a und b vergleicht.**


```python
# Plot hier
```


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x111fbffd0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/02-Aufgabe_Pandas_Data_Visualization_Uebung_16_1.png)
    


**Erstelle ein KDE Plot der Spalte "d".**


```python
# Plot hier
```


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x111fd8748>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/02-Aufgabe_Pandas_Data_Visualization_Uebung_19_1.png)
    


**Finde heraus, wie wir die Linienbreite erhöhen und die Linie stricheln können.**

*Hinweis: Normalerweise würden wir ein KDE Diagramm nicht stricheln.*


```python
# Plot hier
```


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x113d8e9b0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/02-Aufgabe_Pandas_Data_Visualization_Uebung_22_1.png)
    


**Erstelle ein Flächendiagramm (en. area plot) für alle Spalten. Nutze dabei aber nur die ersten 30 Zeilen.**

*Hinweis: Für die Zeilen kannst du .iloc nutzen.*


```python
# Plot hier
```


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x1141a1550>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/02-Aufgabe_Pandas_Data_Visualization_Uebung_25_1.png)
    


## Bonus Aufgabe!
Das könnte wirklich schwer sein, weshalb es okay ist, sich auf die Lösung zu beziehen, wenn man nicht weiter kommt.

**Sicher fällt euch auf, dass die Legende in der vorherigen Lösung das eigentliche Diagramm überdeckt. Findest du einen Weg, um die Legende neben dem eigentlichen Diagramm anzuzeigen?**

*Hinweis: Google Suche nach einem guten Stackoverflow-Link zu diesem Thema hilft.*


```python
# Plot hier
```


```python

```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/06_PandasIntegrierteDataVisualization/Markdown/02-Aufgabe_Pandas_Data_Visualization_Uebung_28_0.png)
    


# Gut gemacht!

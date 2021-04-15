# Style und Farbgebung

Quelle: Datamics

Wir haben bereits einige Male die Anpassungsmöglichkeiten der Diagrammoptik in Seaborn genutzt. Lasst uns dies nun noch einmal formell betrachten:


```python
import seaborn as sns
import matplotlib.pyplot as plt
%matplotlib inline
tips = sns.load_dataset('tips')
```

## Styles
Wir können bestimmte Styles festlegen:


```python
sns.countplot(x='sex',data=tips)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x114a82780>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/06-Style_und_Farbgebung_3_1.png)
    



```python
sns.set_style('ticks')
sns.countplot(x='sex',data=tips,palette='deep')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x114de68d0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/06-Style_und_Farbgebung_4_1.png)
    


## Rahmen entfernen


```python
sns.countplot(x='sex',data=tips)
sns.despine()
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/06-Style_und_Farbgebung_6_0.png)
    



```python
sns.countplot(x='sex',data=tips)
sns.despine(left=True)
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/06-Style_und_Farbgebung_7_0.png)
    


## Größe und Perspektive

Wir können die aus *Matplotlib* bekannte `plt.figure(figsize=(width,heigth)` nutzen, um die Größe von Seaborn Diagrammen zu ändern.

Allerdings können wir die Größe und Perspektive der meisten Seaborn Diagramme auch über die Parameter `size` und `aspect` anpassen. Zum Beispiel:


```python
plt.figure(figsize=(12,3))
sns.countplot(x='sex',data=tips)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x115297860>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/06-Style_und_Farbgebung_9_1.png)
    



```python
sns.lmplot(x='total_bill',y='tip',size=2,aspect=4,data=tips)
```




    <seaborn.axisgrid.FacetGrid at 0x1153d5128>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/06-Style_und_Farbgebung_10_1.png)
    


## Skalierung und Kontext
Die `set_context()` Funktion erlaubt es uns Standardeigenschaften zu überschreiben:


```python
sns.set_context('poster',font_scale=4)
sns.countplot(x='sex',data=tips,palette='coolwarm')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1153f22b0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/05_Seaborn/Markdown/06-Style_und_Farbgebung_12_1.png)
    


Check out the documentation page for more info on these topics:

https://stanford.edu/~mwaskom/software/seaborn/tutorial/aesthetics.html

http://matplotlib.org/examples/color/colormaps_reference.html

# Gut gemacht!

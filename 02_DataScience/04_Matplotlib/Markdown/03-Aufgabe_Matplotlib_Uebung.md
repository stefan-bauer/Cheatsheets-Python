<a href="https://www.datamics.com/courses/online-courses/">![title](bg_datamics_top.png)</a>

<center><em>© Datamics</em></center><br><center><em>Besuche uns für mehr Informationen auf <a href='https://www.datamics.com/courses/online-courses/'>www.datamics.com</a></em>
# Matplotlib Übung - Aufgabe

Willkommen zur Übung zur Python Lib *Matplotlib*. Nehmt Euch dafür ausreichend Zeit, denn Matplotlib kann anfangs knifflig sein. Die Diagramme sind relativ simpel, allerdings kann es schwierig sein, wenn man sich das erste Mal selbstständig mit Matplotlib beschäftigt. Wenn es Probleme gibt dann stehen euch immer die vorherigen Lektionen oder die Lösungen zur Übung zur Verfügung.

Falls euch die Matplotlib Syntax frustriert macht euch keine großen Sorgen, da sie nicht so häufig im Kurs verwendet werden wird. Das liegt daran, dass wir zu *Seaborn* und den *eingebauten Pandas* Visualisierungen wechseln werden. Da diese aber auf Matplotlib aufbauen ist es wichtig sich einmal damit auseinanderzusetzen.

***Hinweis: Alle Befehle sollten in einer Zelle geschrieben werden. Teilt man den Code auf mehrere Zellen auf kann es passieren, dass kein Diagramm angezeigt wird.***

## Übung

Die folgenden Anweisungen sollten durch Nutzung der folgenden Daten umgesetzt werden:

### Daten


```python
import numpy as np
x = np.arange(0,100)
y = x*2
z = x**2
```

**Importiere matplotlib.pyplot als plt und führe %matplotlib inline aus, wenn du die Jupyter Notebooks nutzt. Welchen Befehl sollte man nutzen, wenn man die Notebooks nicht verwendet?**


```python

```

## Übung 1

**Führe folgende Schritte aus:**

* **Erstelle ein Diagramm Objekt *fig* durch plt.figure()**
* **Nutze add_axes um eine Achse zum Diagramm auf der Arbeitsfläche bei der Position [0,0,1,1] hinzuzufügen. Nenne diese Achse *ax*.**
* **Zeige (x,y) auf den Achsen und bennene Labels und Titel wie im angezeigten Beispiel.**


```python

```




    <matplotlib.text.Text at 0x117efccc0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/03-Aufgabe_Matplotlib_Uebung_5_1.png)
    


## Übung 2

**Erstelle ein Diagramm Objekt und füge die beiden Achsen *ax1* und *ax2* hinzu. Platziere sie bei [0,0,1,1] bzw. [0.2,0.5,0.2,0.2].**


```python

```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/03-Aufgabe_Matplotlib_Uebung_7_0.png)
    


**Jetzt stelle (x,y) auf beiden Achsen dar. Rufe außerdem dein Diagramm auf, um es anzuzeigen.**


```python

```




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/03-Aufgabe_Matplotlib_Uebung_9_0.png)
    



## Übung 3
**Erstelle das zu sehende Diagramm durch Hinzufügen von zwei Achsen. Platziere sie bei [0,0,1,1] und [0.2,0.5,0.4,0.4].**


```python

```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/03-Aufgabe_Matplotlib_Uebung_11_0.png)
    


**Nutze jetzt x,y, und z Arrays um das folgende Diagramm darzustellen. Achte bei eingefügten Diagramm auf `xlimits` und `ylimits`.**


```python

```




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/03-Aufgabe_Matplotlib_Uebung_13_0.png)
    



## Übung 4

**Nutze plt.subplots(nrows=1, ncols=2) um das untenstehende Diagramm zu erstellen.**


```python

```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/03-Aufgabe_Matplotlib_Uebung_15_0.png)
    


**Füge jetzt (x,y) und (x,z) auf den beiden Achsen ein. Spiele mit Linienstärke und -stil.**


```python

```




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/03-Aufgabe_Matplotlib_Uebung_17_0.png)
    



**Ändere jetzt die Größe der Diagramme durch Hinzufügen des figsize() Arguments in plt.subplots(). Du kannst deinen vorherigen Code kopieren.**


```python

```




    <matplotlib.text.Text at 0x11bbf8cc0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/03-Aufgabe_Matplotlib_Uebung_19_1.png)
    


# Gut gemacht!

# Matplotlib Übung - Lösung

Quelle: Datamics

Willkommen zur Übung zur Python Lib *Matplotlib*. Nehme dir dafür ausreichend Zeit, denn Matplotlib kann anfangs knifflig sein. Die Diagramme sind relativ simpel, allerdings kann es schwierig sein, wenn man sich das erste Mal selbstständig mit Matplotlib beschäftigt. Wenn es Probleme gibt dann stehen euch immer die vorherigen Lektionen oder die Lösungen zur Übung zur Verfügung.

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
import matplotlib.pyplot as plt
%matplotlib inline
# plt.show() für Nicht-Notebook-Nutzer
```

## Übung 1

**Führe folgende Schritte aus:**

* **Erstelle ein Diagramm Objekt *fig* durch plt.figure()**
* **Nutze add_axes um eine Achse zum Diagramm auf der Arbeitsfläche bei der Position [0,0,1,1] hinzuzufügen. Nenne diese Achse *ax*.**
* **Zeige (x,y) auf den Achsen und bennene Labels und Titel wie im angezeigten Beispiel.**


```python
fig = plt.figure()
ax = fig.add_axes([0,0,1,1])
ax.plot(x,y)
ax.set_xlabel('x')
ax.set_ylabel('y')
ax.set_title('Titel')
```




    <matplotlib.text.Text at 0x117efccc0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/04-Loesung_Matplotlib_Uebung_5_1.png)
    


## Übung 2

**Erstelle ein Diagramm Objekt und füge die beiden Achsen *ax1* und *ax2* hinzu. Platziere sie bei [0,0,1,1] bzw. [0.2,0.5,0.2,0.2].**


```python
fig = plt.figure()

ax1 = fig.add_axes([0,0,1,1])
ax2 = fig.add_axes([0.2,0.5,.2,.2])
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/04-Loesung_Matplotlib_Uebung_7_0.png)
    


**Jetzt stelle (x,y) auf beiden Achsen dar. Rufe außerdem dein Diagramm auf, um es anzuzeigen.**


```python
ax1.plot(x,y)
ax1.set_xlabel('x')
ax1.set_ylabel('y')


ax2.plot(x,y)
ax2.set_xlabel('x')
ax2.set_ylabel('y')

fig # Show figure object
```




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/04-Loesung_Matplotlib_Uebung_9_0.png)
    



## Übung 3
**Erstelle das zu sehende Diagramm durch Hinzufügen von zwei Achsen. Platziere sie bei [0,0,1,1] und [0.2,0.5,0.4,0.4].**


```python
fig = plt.figure()

ax1 = fig.add_axes([0,0,1,1])
ax2 = fig.add_axes([0.2,0.5,.4,.4])
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/04-Loesung_Matplotlib_Uebung_11_0.png)
    


**Nutze jetzt x,y, und z Arrays um das folgende Diagramm darzustellen. Achte bei eingefügten Diagramm auf `xlimits` und `ylimits`.**


```python
ax1.plot(x,z)
ax1.set_xlabel('X')
ax1.set_ylabel('Z')


ax2.plot(x,y)
ax2.set_xlabel('X')
ax2.set_ylabel('Y')
ax2.set_title('zoom')
ax2.set_xlim(20,22)
ax2.set_ylim(30,50)

fig
```




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/04-Loesung_Matplotlib_Uebung_13_0.png)
    



## Übung 4

**Nutze plt.subplots(nrows=1, ncols=2) um das untenstehende Diagramm zu erstellen.**


```python
# Leere Arbeitsfläche mit 1 x 2 Diagrammen
fig, axes = plt.subplots(nrows=1, ncols=2)
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/04-Loesung_Matplotlib_Uebung_15_0.png)
    


**Füge jetzt (x,y) und (x,z) auf den beiden Achsen ein. Spiele mit Linienstärke und -stil.**


```python
axes[0].plot(x,y,color="blue", lw=3, ls='--')
axes[1].plot(x,z,color="red", lw=3, ls='-')
fig
```




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/04-Loesung_Matplotlib_Uebung_17_0.png)
    



**Ändere jetzt die Größe der Diagramme durch Hinzufügen des figsize() Arguments in plt.subplots(). Du kannst deinen vorherigen Code kopieren.**


```python
fig, axes = plt.subplots(nrows=1, ncols=2,figsize=(12,2))

axes[0].plot(x,y,color="blue", lw=5)
axes[0].set_xlabel('x')
axes[0].set_ylabel('y')

axes[1].plot(x,z,color="red", lw=3, ls='--')
axes[1].set_xlabel('x')
axes[1].set_ylabel('z')
```




    <matplotlib.text.Text at 0x11bbf8cc0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/04-Loesung_Matplotlib_Uebung_19_1.png)
    


# Gut gemacht!

# Matplotlib

Quelle: Datamics

## Einführung

Matplotlib ist quasi der Großvater der Daten Visualisierung mit Python. Es wurde von John Hunter geschaffen und sollte dazu dienen, die Möglichkeiten, die MatLab (eine weitere Programmiersprache) zur Visualisierung bietet, in Python nachzubilden. Wenn du MatLab kennst, dann wird dir Matplotlib vertraut vorkommen.

Es ist eine exzellente 2D und 3D Grafik Library um wissenschaftliche Diagramme zu erzeugen.

Einige der größten Vorteile von Matplotlib sind:

* Generell ist es einfach mit simplen Plots loszulegen
* Es werden eigene Labels und Texte unterstützt
* Gute Kontrolle über jedes einzelne Element in einem Diagram
* Output in hoher Qualität in viele Formate
* Insgesamt sehr anpassbar

Matplotlib erlaubt es uns wiederherstellbare Graphen durch Programmieren zu erstellen. Jetzt werden wir lernen, wie das geht! Zuvor empfiehlt es sich jedoch, die offizielle Homepage anzuschauen: [http://matplotlib.org/](http://matplotlib.org/).

## Installation

Falls noch nicht vorhaben könnt ihr Matplotlib mit folgendem Code im Terminal bzw. der Kommandozeile installieren:

    conda install matplotlib

## Importieren

Wir importieren das `matplotlib.pyplot` Modul unter dem Namen plt (Kurzform):


```python
import matplotlib.pyplot as plt
```

Außerdem müssen wir einmal die folgende Zeile ausführen, um die Plots im Notebook zu sehen:


```python
%matplotlib inline
```

Sofern du nicht die Notebooks verwendest, sondern einen anderen Editor, kannst du `plt.show()` am Ende aller Plottingbefehle eingeben. Dadurch öffnet sich der Graph in einem neuen Fenster.

## Grundlegendes Beispiel

Lass uns ein einfaches Beispiel anschauen bei dem wir zwei NumPy Arrays verwenden:

### Beispiel

Lass uns ein einfaches Beispiel anschauen bei dem wir zwei NumPy Arrays verwenden. Du könntest auch Listen verwenden, aber im Data Science Kontext würden wir vermutlich eher mit NumPy Arrays oder Pandas Spalten (die sich wie Arrays verhalten) arbeiten.

#### Die Daten die wir darstellen wollen:


```python
import numpy as np
x = np.linspace(0, 5, 11)
y = x ** 2
```


```python
x
```




    array([ 0. ,  0.5,  1. ,  1.5,  2. ,  2.5,  3. ,  3.5,  4. ,  4.5,  5. ])




```python
y
```




    array([  0.  ,   0.25,   1.  ,   2.25,   4.  ,   6.25,   9.  ,  12.25,
            16.  ,  20.25,  25.  ])



## Matplotlib Kommandos

Wir können ein einfaches Liniendiagramm durch die folgenden Kommandos erstellen. Dabei rate ich jedem kurz zu pausieren und sich mit Shift + Tab die Dokumentation zu den Funktionen anzuschauen, um sie besser zu verstehen.


```python
plt.plot(x, y, 'r') # 'r' bezeichnet die Farbe "Rot"
plt.xlabel('X Achsen Bezeichnung')
plt.ylabel('Y Achsen Bezeichnung')
plt.title('Diagramm Titel')
plt.show()
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_10_0.png)
    


## Mehrere Diagramme auf derselben Arbeitsfläche


```python
# plt.subplot(AnzahlDerZeilen, AnzahlDerSpalten, PlotNummer)
plt.subplot(1,2,1)
plt.plot(x, y, 'r--') # Mehr zur Farbgestalltung später
plt.subplot(1,2,2)
plt.plot(y, x, 'g*-'); 
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_12_0.png)
    


# Matplotlib Objektorientierte Methode

Jetzt wo wir die Grundlagen kennengelernt haben können wir uns die etwas formalere Einführung zu Matplotlib's Objektorientierter API (dt. Schnittstelle) anschauen. Das bedeutet, dass wir Diagramm-Objekte instanziieren und darauf Methoden oder Attribute anwenden.

## Einführung zur objektorientierten Methode

Die Grundidee davon die objektorientierte Methode zu verwenden ist es Diagramm Objekte zu erstellen auf die man Methoden oder Attribute anwenden kann. Dieser Ansatz ist angenehmer wenn wir mit Arbeitsflächen arbeiten, auf denen mehrere Diagramme sind.

Um loszulegen erstellen wir eine Diagramm Instanz. Dann fügen wir dem Diagramm Achsen hinzu:


```python
# Diagramm erstellen (leere Arbeitsfläche)
af = plt.figure()

# Dem Diagramm Achsen hinzufügen
axes = af.add_axes([0.1, 0.1, 0.8, 0.8]) # links, unten, breite, höhe (zwischen 0 und 1)

# Anhand dieser Achsen darstellen
axes.plot(x, y, 'b')
axes.set_xlabel('X Label definieren') # Nutzt set_ um die Methode zu beginnen
axes.set_ylabel('Y Label definieren')
axes.set_title('Titer definieren')
```




    <matplotlib.text.Text at 0x10e971dd8>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_14_1.png)
    


Zunächst ist der Code jetzt etwas umständlicher. Der große Vorteil ist allerdings, dass wir die volle Kontrolle über unsere Arbeitsfläche haben. So können wir bspw. mehr als nur eine Achse zur Arbeitsfläche hinzufügen:


```python
# Leere Arbeitsfläche erstellen
af = plt.figure()

axes1 = af.add_axes([0.1, 0.1, 0.8, 0.8]) # Hauptachse
axes2 = af.add_axes([0.2, 0.5, 0.4, 0.3]) # Eingesetzte Achse

# Größeres Diagramm mit Achse 1
axes1.plot(x, y, 'b')
axes1.set_xlabel('x Beschriftung Achse 1')
axes1.set_ylabel('y Beschriftung Achse 1')
axes1.set_title('Titel größeres Diagramm')

# Eingesetztes Diagramm mit Achse 2
axes2.plot(y, x, 'r')
axes2.set_xlabel('x Beschriftung Achse 2')
axes2.set_ylabel('y Beschriftung Achse 2')
axes2.set_title('Titel eingesetztes Diagramm');
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_16_0.png)
    


## subplots()

Das plt.subplot() Objekt funktioniert eher wie eine automatische Achsenverwaltung. 

Einfacher Anwendungsfall:


```python
# Wir nutzen wie bei plt.figure() 
diag, axes = plt.subplots()

# Jezt fügen wir über das axes Objekt weitere Informationen hinzu
axes.plot(x, y, 'r')
axes.set_xlabel('x')
axes.set_ylabel('y')
axes.set_title('titel');
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_18_0.png)
    


Dann können wir durch das subplots() Objekt die Anzahl von Zeilen und Spalten definieren:


```python
# Leere Arbeitsfläche von 1 x 2 Subplots
diag, axes = plt.subplots(nrows = 1, ncols = 2)
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_20_0.png)
    



```python
# Axes ist ein Array der Achsen
axes
```




    array([<matplotlib.axes._subplots.AxesSubplot object at 0x10ed3fdd8>,
           <matplotlib.axes._subplots.AxesSubplot object at 0x10ee6a0b8>], dtype=object)



Wir können durch dieses Array iterieren:


```python
for ax in axes:
    ax.plot(x, y, 'b')
    ax.set_xlabel('x')
    ax.set_ylabel('y')
    ax.set_title('titel')

# Anzeigen
diag
```




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_23_0.png)
    



Ein häufiges "Problem" mit Matplotlib ist, dass es überlappende Inhalte in den Subplots gibt. Wir können diag.tight_layout() oder die plt.tight_layout() Methode nutzen. Dadurch wird die Position der Achsen automatisch angepasst, damit es keine überlappenden Inhalte mehr gibt:


```python
diag, axes = plt.subplots(nrows=1, ncols=2)

for ax in axes:
    ax.plot(x, y, 'g')
    ax.set_xlabel('x')
    ax.set_ylabel('y')
    ax.set_title('titel')

diag    
plt.tight_layout()
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_25_0.png)
    


## Diagrammgröße, Abbildungsverhältnis und DPI

Matplotlib erlaubt es uns das Abbildungsverhältnis, DPI und Diagrammgröße zu spezifizieren. Dazu nutzen wir die `figsize` und `dpi` Argumente.

* `figsize` ist ein Tupel von Breite und Höhe in Zoll
* `dpi` bezeichnet dots-per-inch (Pixel pro Zoll)

Zum Beispiel:


```python
diag = plt.figure(figsize=(8,4), dpi= 100)

ax = diag.add_axes([0,0,1,1])
ax.plot(x,y)
```




    [<matplotlib.lines.Line2D at 0x110224320>]




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_27_1.png)
    


Dieselben Argumente können auch an die Layoutverwaltung (wie z.B. `subplots` übergeben werden:


```python
diag, axes = plt.subplots(figsize=(12,3))

axes.plot(x, y, 'r')
axes.set_xlabel('x')
axes.set_ylabel('y')
axes.set_title('titel');
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_29_0.png)
    


## Diagramme speichern

Matplotlib kann hochauflösenden Output in verschiedenen Formaten generieren: PNG, JPG, EPS, SVG, PGF und PDF.

Um Diagramme als Datei zu speichern verwenden wir die `savefig` Methode in der `figure` Klasse:


```python
diag.savefig("dateiname.png")
```

Hier können wir außerdem die DPI festlegen:


```python
diag.savefig("dateiname.png", dpi=200)
```

## Legenden, Beschriftungen und Titel

Wir haben bisher die Grundlagen kennengelernt, um Diagramme auf der Arbeitsfläche zu erzeugen und Achsen hinzuzufügen. Nun können wir uns anschauen, wie man Diagramme mit weiteren Elementen ausstattet. Dazu zählen Legenden, Beschriftungen und Titel.

### Diagramm Titel

Ein Titel kann der Achsen Instanz eines Diagramms hinzugefügt werden. Um den Titel zu definieren nutzen wir die `set_title` Methode:


```python
ax.set_title("title")
```

### Achsenbeschriftung

Genauso, mit den Methoden `set_xlabel` und `set_ylabel`, können wir Beschriftungen zu den Achsen X und Y hinzufügen:


```python
ax.set_xlabel("x")
ax.set_ylabel("y")
```

## Legenden

Über **label="Beschriftung"** als Argument für Diagramme in Kombination mit der `legend` Methode (ohne weitere Argumente) können wir unserem Diagramm eine Legende hinzufügen:


```python
diag = plt.figure()

ax = diag.add_axes([0,0,1,1])

ax.plot(x, x**2, label="x**2")
ax.plot(x, x**3, label="x**3")
ax.legend()
```




    <matplotlib.legend.Legend at 0x10ea45438>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_39_1.png)
    


Manchmal kann es passieren, dass die Legende den Graphen überdeckt!

Um dem entgegenzuwirken können wir die Position der Legende aus vielen Möglichkeiten mit dem **loc** Argument festlegen. Die erlaubten Werte für das loc Argument sind numerische Werte, die bspw. vier Ecken des Diagramms repräsentieren. Für alle Positionen siehe die [Dokumentation](http://matplotlib.org/api/pyplot_api.html#matplotlib.pyplot.legend). Die meistverwendeten Werte sind folgende:


```python
# Viele Optionen...

ax.legend(loc=1) # Ecke oben rechts
ax.legend(loc=2) # Ecke oben links
ax.legend(loc=3) # Ecke unten links 
ax.legend(loc=4) # Ecke unten rechts

# es gibt jedoch viele weitere Möglichkeiten

# Häufigste Verwendung
ax.legend(loc=0) # Matplotlib sucht sich die optimale Position selbst aus
```




    <matplotlib.legend.Legend at 0x10eaa84e0>



## Farben festlegen, Linienstärke und Linientyp

Matplotlib gibt uns viele Optionen um Farbe, Stärke und Typ einer Linie (bzw. eines Diagramms) festzulegen.

Es gibt dazu die MatLab ähnliche Syntax, aber auch andere Varianten.

### Farben mit der MatLab ähnlichen Syntax

Mit Matplotlib können wir die Farbe und andere graphische Elemente in einer Vielzahl an Wegen definieren. Der erste Weg wäre die Definition in einer MatLab ähnlichen Syntax. In dieser bedeutet "b" blue (dt. blau), "g" bedeutet green (en. grün), etc. Die MatLab API erlaubt es uns auch den Linientyp auszuwählen. Z.B. bedeutet "b.-" im Diagramm letztliche blaue Linie mit Punkten:


```python
# MatLab Style
diag, ax = plt.subplots()
ax.plot(x, x**2, 'b.-') # blaue Linie mit Punkten
ax.plot(x, x**3, 'g--') # grüne gestrichelte Linie
```




    [<matplotlib.lines.Line2D at 0x10f2c6cc0>]




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_43_1.png)
    


### Farben mit dem "color =" Parameter

Wir können zweitens Farben über den "color =" Parameter festlegen. Dazu nutzen wir deren Namen oder RGB Code und optional einen Alpha-Wert, um die Transparenz festzulegen.


```python
diag, ax = plt.subplots()

ax.plot(x, x+1, color="blue", alpha=0.5) # Transparenz 50%
ax.plot(x, x+2, color="#8B008B")        # RGB Hex Code
ax.plot(x, x+3, color="#FF8C00")        # RGB Hex Code 
```




    [<matplotlib.lines.Line2D at 0x10f203748>]




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_45_1.png)
    


### Linien- und Markierungsstil

Um die Linienstärke zu ändern können wir `linewidth` oder `lw` nutzen. Den Stil können wir mit `linestyle` oder `ls` festlegen.


```python
diag, ax = plt.subplots(figsize=(12,6))

ax.plot(x, x+1, color="red", linewidth=0.25)
ax.plot(x, x+2, color="red", linewidth=0.50)
ax.plot(x, x+3, color="red", linewidth=1.00)
ax.plot(x, x+4, color="red", linewidth=2.00)

# Mögliche Linienstile ‘-‘, ‘–’, ‘-.’, ‘:’, ‘steps’
ax.plot(x, x+5, color="green", lw=3, linestyle='-')
ax.plot(x, x+6, color="green", lw=3, ls='-.')
ax.plot(x, x+7, color="green", lw=3, ls=':')

# Benutzerdefinierte Querstrich
line, = ax.plot(x, x+8, color="black", lw=1.50)
line.set_dashes([5, 10, 15, 10]) # Format: Linienlänge, Abstandslänge, ...

# Mögliche Markierungen: marker = '+', 'o', '*', 's', ',', '.', '1', '2', '3', '4', ...
ax.plot(x, x+ 9, color="blue", lw=3, ls='-', marker='+')
ax.plot(x, x+10, color="blue", lw=3, ls='--', marker='o')
ax.plot(x, x+11, color="blue", lw=3, ls='-', marker='s')
ax.plot(x, x+12, color="blue", lw=3, ls='--', marker='1')

# Markierungsgröße und Farbe
ax.plot(x, x+13, color="purple", lw=1, ls='-', marker='o', markersize=2)
ax.plot(x, x+14, color="purple", lw=1, ls='-', marker='o', markersize=4)
ax.plot(x, x+15, color="purple", lw=1, ls='-', marker='o', markersize=8, markerfacecolor="red")
ax.plot(x, x+16, color="purple", lw=1, ls='-', marker='s', markersize=8, 
        markerfacecolor="yellow", markeredgewidth=3, markeredgecolor="green");
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_47_0.png)
    


### Diagrammbereich

Wir können den Diagrammbereich der Achsen mit `set_ylim` und `set_xlim` als Methoden des Achsenobjekts definieren. Alternativ kann man per `axis("tight")` automatisch einen "eng angelegten" Bereich wählen:


```python
diag, axes = plt.subplots(1, 3, figsize=(12, 4))

axes[0].plot(x, x**2, x, x**3)
axes[0].set_title("Standard Achsen Bereich")

axes[1].plot(x, x**2, x, x**3)
axes[1].axis('tight')
axes[1].set_title("Enge Achsen")

axes[2].plot(x, x**2, x, x**3)
axes[2].set_ylim([0, 60])
axes[2].set_xlim([2, 5])
axes[2].set_title("Benutzerdefinierter Bereich");
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_49_0.png)
    


# Spezielle Diagramme

Es gibt viele weitere spezielle Diagramme wie bspw. Balkendiagramme, Histogramme oder Scatter Plots, die wir mit Matplotlib erstellen können. Die meisten davon werden wir in späteren Lektionen automatisch durch *Seaborn* erstellen. Das ist eine statistische Diagramm Library für Python. Nichtsdestotrotz können wir uns schon Beispiele dieser Diagramme anschauen:


```python
plt.scatter(x,y)
```




    <matplotlib.collections.PathCollection at 0x1100cbc18>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_51_1.png)
    



```python
from random import sample
data = sample(range(1, 1000), 100)
plt.hist(data)
```




    (array([ 10.,   9.,  14.,   8.,   8.,  11.,  12.,  12.,   8.,   8.]),
     array([   9. ,  106.8,  204.6,  302.4,  400.2,  498. ,  595.8,  693.6,
             791.4,  889.2,  987. ]),
     <a list of 10 Patch objects>)




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_52_1.png)
    



```python
data = [np.random.normal(0, std, 100) for std in range(1, 4)]

# Rechteckiges Box Plot
plt.boxplot(data,vert=True,patch_artist=True);   
```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/04_Matplotlib/Markdown/01-Matplotlib_Konzepte_53_0.png)
    


## Weitere Ressourcen

* http://www.matplotlib.org - Die Webseite von Matplotlib.
* https://github.com/matplotlib/matplotlib - Der Sourcecode zu Matplotlib.
* http://matplotlib.org/gallery.html - Eine große Galerie, die viele Arten von Diagrammen zeigt, die mit Matplotlib erstellbar sind.

# Gut gemacht!

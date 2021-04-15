# Interact nutzen

Quelle: Datamics

In dieser Lektion werden wir damit beginnen zu lernen, wie man Dashboard-artige GUIs mit iPython Widgets erstellt!

Die `interact` Funktion (ipywidgets.interact) erstellt automatisch Nutzeroberflächen (UI = user interface), Regler zur Codeerkundung und Daten Interaktivität. Es ist der einfachste Weg um mit iPython Widgets loszulegen.


```python
# Wir starten mit einigen Imports!

from ipywidgets import interact, interactive, fixed
import ipywidgets as widgets
```

<div class="alert alert-success">
Bitte beachten! Die Widgets in diesem Notebook werden in NbViewer oder Github nicht angezeigt werden. Um die Widgets zu sehen und mit ihnen interagieren zu können, werdet ihr dieses Notebook herunterladen und mit Jupyter ausführen müssen.
</div>

## Grundsätzliches `interact`

Auf dem grundsätzlichsten Level erzeugt `interact` selbstständig UI-Steuerelemente für Parameter. Schließlich wird die Funktion mit diesen Parametern aufgerufen, sobald die Steuerelemente manipuliert werden. Um `interact` zu nutzen, müssen wir eine Funktion definieren. Hier ist eine Funktion die den Parameter x ausgibt


```python
# Sehr einfache Funktion
def f(x):
    return x
```

Wenn wir diese Funktion als den ersten Parameter zusammen mit einer Zahl (x=10) an `interact` übergeben, dann wird ein Slider erzeugt, der den Parameter der Funktion repräsentiert.

Der Strichpunkt am Ende sorgt hier dafür, dass wir keine "Out"-Zelle erzeugen.


```python
# Einen interaktiven Slider erstellen
interact(f, x=10);
```



Wenn wir den Slider bewegen, wird die Funktion ausgeführt, die den aktuellen Wert von x ausgibt. 

Wenn wir `True` oder `Flase` an `interact` übergeben generiert es eine Check-Box:


```python
# Booleans erzeugen ein Check-Boxen
interact(f, x=True);
```



Wenn wir einen String übergeben, dann erstellt `interact` ein Textfeld.


```python
# Strings generieren Textfelder
interact(f, x="Hallo zusammen!");
```



`interact` kann auch als Dekorator genutzt werden. Das erlaubt es uns, auf einen Streich eine Funktion zu definieren und die Interaktion auszuführen. Wie das folgende Beispiel zeigt funktioniert `interact` auch mit mehreren Parametern.


```python
# Einen Dekorator nutzen
@interact(x=True, y=1.0)
def g(x,y):
    return (x,y)
```



## Parameter mit `fixed` fixieren

Es kann vorkommen, dass ihr mit einer Funktion interagieren wollt, dabei aber einen oder mehrere Werte konstant halten wollt. Das kann dadurch erreicht werden, dass wir den Wert in die fixed() Funktion packen.


```python
# Eine weitere einfache Funktion
def h(p, q):
    return (p, q)
```


```python
# Den Wert für q auf 20 fixieren
interact(h, p=5, q=fixed(20));
```



Wie ihr sehen könnt wird dadurch nur für p ein Slider erstellt.

## Widget Abkürzungen

Wenn wir einen Zahlen-Wert Stichwort von 10 (x=10) als Parameter an `interact` übergeben, dann erstellt es einen Zahlen bezogenen Slider mit der Skala [-10, +3x10]. In diesem Fall ist 10 eine *Abkürzung* für ein tatsächliches Slider Widget:

    IntSlider(min=-10,max=30,step=1,value=10)
    
Und tatsächlich können wir auch auf diese Weise das selbe Ergebnis erzielen:


```python
# Wir können IntSlider nuten, um genauere Parameter zu übergeben
interact(f, x=widgets.IntSlider(min=-10,max=30,step=1,value=10));
```



Dieses Beispiel verdeutlich, wie `interact` seine Parameter verarbeitet:

1. Wenn das Stichwort eine Widget Instanz mit einem `value` Parameter ist, wird das entsprechende Widget verwendet. Jedes Widget kann verwendet werden, sogar selbsterstellte.
2. Andernfalls wird der Wert als Widget Abkürzung behandelt und in ein Widget konvertiert.

Die folgende Tabelle gibt eine Übersicht zu verschiedenen Widget Abkürzungen:

<table class="table table-condensed table-bordered">
  <tr><td><strong>Keyword Parameter</strong></td><td><strong>Widget</strong></td></tr>  
  <tr><td>`True` oder `False`</td><td>Checkbox</td></tr>  
  <tr><td>`'Hallo zusammen'`</td><td>Text</td></tr>
  <tr><td>`value` oder `(min,max)` oder `(min,max,step)` wenn Zahlen übergeben werden</td><td>IntSlider</td></tr>
  <tr><td>`value` oder `(min,max)` oder `(min,max,step)` wenn Kommazahlen übergeben werden</td><td>FloatSlider</td></tr>
  <tr><td>`('Orange','Apfel')` oder `{'Eins':1,'Zwei':2}`</td><td>Dropdown</td></tr>
</table>

Ihr habt gesehen, wie Check-Box und Textfeld Widgets funktionieren. Hier geben wir weitere Details zu den Widget Abkürzungen für Slider und Dropdown Menüs.

Wenn ein 2-Tupel von Zahlen (min,max) übergeben wird, wird ein Zahlen Slider erzeugt, der diese Werte als Minimum und Maximum hat. In dem Fall wird die Standard Schrittgröße von 1 verwendet.


```python
# Min,Max Slider mit einem Tupel
interact(f, x=(0,4));
```



Wird ein 3-Tupel (min,max,schritt) übergeben, können wir die Schrittgröße definieren.


```python
# (Min, Max, Schritt)
interact(f, x=(0,8,2));
```



Ein Kommazahlen Slider wird erzeugt, sobald die Werte im Tupel Kommazahlen sind. Hier ist das Minimum 0,0, das Maximum 10,0 und die Schrittgröße (per Standard) ist 0,1.


```python
interact(f, x=(0.0,10.0));
```



Die Schrittgröße könne wir durch Übergabe eines dritten Elements im Tupel erreichen.


```python
interact(f, x=(0.0,10.0,0.01));
```



Für sowohl Zahlen als auch Kommazahlen Slider können wir den Startwert des Widgets wählen, indem wir ihn als Parameter an die Python Funktion übergeben. Hier haben wir einen Startwert von 5,5 gewählt.


```python
@interact(x=(0.0,20.0,0.5))
def h(x=5.5):
    return x
```



Dropdown Menüs werden dadurch erstellt, dass man eine Liste von Strings übergibt. In diesem Fall dienen die Strings sowohl als Punkte im GUI Dropdown Menü, als auch als Werte für die Python Funktion.


```python
interact(f, x=['Apfel','Orange']);
```



Wenn ihr ein Dropdown Menü wollt, dass nicht-String Werte an die Python Funktion übergibt, dann könnt ihr ein Dictionary verwenden. Die Keys fungieren als Namen im GUI Dropdown. Die Werte des Dictionaries werden als Parameter an die zugrundeliegende Python Funktion übergeben.


```python
interact(f, x={"Eins":1,"Zwei":2});
```



## Funkionsanmerkungen mit `interact` nutzen

Wenn ihr Python 3 nutzt, dann könnt ihr Widget Abkürzungen auch durch Funktionsanmerkungen spezifizieren.

### PYTHON 3

Definition einer Funktion mit der Widget Abkürzung für eine Checkbox:


```python
def f(x:True): # Nur in Python 3
    return x
```

Und weil die Widget Abkürzung bereits definiert würde können wir `interact` mit einem einzigen Parameter aufrufen.


```python
interact(f);
```



### PYTHON 2

Wenn ihr Python 2 nutzt, dann können Funktionsanmerkungen durch die @annotate Funktion definiert werden.


```python
from IPython.utils.py3compat import annotate
```


```python
@annotate(x=True)
def f(x):
    return x
```


```python
interact(f);
```



## interactive

Zusätzlich zu `interact` bietet iPython eine weitere Funktion, `interactive`, die nützlich ist, um Widgets wiederzuverwenden oder auf die Daten zuzugreifen, die die UI Regler beinhalten.

Hier ist eine Funktion, die die Summe zweier Parameter berechnet:


```python
def f(a, b):
    return a+b
```

Anders als `interact` gibt `interactive` eine Widget Instanz zurück, anstatt das Widget direkt anzuzeigen.


```python
w = interactive(f, a=10, b=20)
```

Das Widget ist eine Box, die ein Behälter für andere Widgets ist.


```python
type(w)
```




    ipywidgets.widgets.interaction.interactive



Die Kinder (children) dieser Box sind zwei Zahlen Slider und ein Output, die durch die Widget Abkürzung erstellt wurden.


```python
w.children
```




    (<ipywidgets.widgets.widget_int.IntSlider at 0x1036e7b70>,
     <ipywidgets.widgets.widget_int.IntSlider at 0x103694278>,
     <ipywidgets.widgets.widget_output.Output at 0x1036e7c50>)



Um das tatsächliche Widget anzuzeigen können wir iPython's `display` Funktion nutzen.


```python
from IPython.display import display
display(w)
```



An diesem Punkt funktionieren die UI Regler genau so, als ob sie durch `interact` erzeugt worden wären. Wir können sie interaktiv manipulieren und die Funktion so aufrufen. 

Darüberhinaus gibt uns `interactive` aber auch Zugang auf die beiden Stichwort Parameter und das aktuelle Ergebnis der Python Funktion. So können wir darauf zugreifen:


```python
w.kwargs
```




    {'a': 16, 'b': 13}



Und hier das aktuelle Ergebnis der Funktion:


```python
w.result
```




    29



## Abschließende Bemerkung

Ihr solltet jetzt ein grundsätzliches Verständnis davon haben, wie wir Interact in Jupyter Notebooks verwenden können! Viel Spaß bei den nächsten Lektionen zu GUIs!

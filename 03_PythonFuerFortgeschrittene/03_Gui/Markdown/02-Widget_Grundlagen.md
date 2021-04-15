# Widget Grundlagen

Quelle: Datamics

In dieser Lektion werden wir unser Verständnis von interact und interactive weiter ausbauen, um vollständige Widgets verwenden zu können.

## Was sind Widgets?

Widgets sind bewegte Python Objekte, die im Browser repräsentiert werden. Beispiele sind Slider, Textboxen und ähnliches.

## Wofür können sie verwendet werden?

Ihr könnt Widgets nutzen, um interaktive GUIs für eure Notbeooks zu erstellen. Außerdem könnt ihr sie nutzen, um zustandsorientierte und zustandslose Information zwischen Python und Java zu synchronisieren.

## Widgets nutzen

Um das Widget Framework zu nutzen, müssen wir *ipywidgets* importieren.


```python
from ipywidgets import *
```

### repr

Widgets haben ihr eigenes `repr`, was ihnen gestattet durch iPython's display Framework angezeigt zu werden. Durch das erstellen und ausgeben eines `IntSlider` wird das Widget automatisch ausgegeben (wie ihr unten sehen könnt). Widgets werden innerhalb des Widget Bereichs angezeigt, welcher zwischen dem Zellen Code und dem Output liegt. Wir können alle Widgets des Widget Bereichs ausblenden, indem wir das graue *x* am Rand klicken.


```python
IntSlider()
```



### display

Wir können Widgets außerdem explizit anzeigen, indem wir `display` verwenden.


```python
from IPython.display import display
w = IntSlider()
display(w)
```



### Mehrere display() Aufrufe

Wenn wir das selbe Widget mehrmals anzeigen lassen, werden sie im Frontend synchronisiert. Verstellt den folgenden Slider und achtet auf den obigen.


```python
display(w)
```



### Widgets schließen

Widgets können durch die close() Methode geschlossen werden.


```python
display(w)
```




```python
w.close()
```

### Widget Eigenschaften

Alle iPython Widgets teilen die gleiche Nomenklatur. Um den Wert eines Widgets auszulesen können wir die `value` Eigenschaft aufrufen.


```python
w = IntSlider()
display(w)
```




```python
w.value
```




    6



Genau so können wir auch den Wert eines Widgets festlegen.


```python
w.value = 100
```

### Keys

Zusätzlich zu `value` teilen die meisten Widgets `keys`, `description`, `disabled` und `visible`. Um die gesamte Liste der synchronisierten Eigenschaften eines spezifischen Widgets anzuzeigen, können wir die `keys` Eigenschaft aufrufen.


```python
w.keys
```




    ['_dom_classes',
     '_model_module',
     '_model_module_version',
     '_model_name',
     '_range',
     '_view_module',
     '_view_module_version',
     '_view_name',
     'continuous_update',
     'description',
     'disabled',
     'layout',
     'max',
     'min',
     'msg_throttle',
     'orientation',
     'readout',
     'readout_format',
     'step',
     'style',
     'value']



### Kurzschrift um den Startwert einer Widget Eigenschaft festzulegen

Während wir ein Widget erstellen, können wir gleichzeitig einige oder alle der Eigenschaften eines Widgets festlegen, indem wir diese als Stichwort Parameter festlegen. Seht hier ein Beispiel:


```python
Text(value="Hallo Welt", disabled=True)
```



## Zwei gleiche Widgets verknüpfen

Wenn ihr denselben Wert auf zwei unterschiedliche Arten anzeigen wollt, dann braucht ihr zwei unterschiedliche Widgets. Anstatt diese aber manuell synchronisieren zu wollen können wir einfach die `traitlet link` Funktion verwenden, um die beiden Eigenschaften zu verknüpfen. Unten sind die Werte zweier Widgets verknüpft:


```python
from traitlets import link
a = FloatText()
b = FloatSlider()
display(a,b)

mylink = link((a, 'value'), (b, 'value'))
```





### Verknüpfung von Widgets aufheben

Die Verknüpfung von Widgets aufzuheben ist leicht. Alles was wir tun müssen ist .`unlink` auf das link Objekt anzuwenden. Versucht eines der Widgets oberhalb zu verändern, nachdem wir die Verknüpfung aufgehoben haben.


```python
mylink.unlink()
```

## Schlussfolgerung

So langsam solltet ihr ein Gefühl dafür bekommen, wie Widgets miteinander interagieren können und wie wir Details von Widgets festlegen können.

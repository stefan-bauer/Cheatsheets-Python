# Widget Listen

Quelle: Datamics

Diese Lektion dient als Referenz für Widgets, indem sie eine Liste der GUI Widgets zur Verfügung stellt!

## Komplette Liste

Für eine vollständige Liste aller GUI Widgets die euch zur Verfügung stehen, könnt ihr die registrierten Widget Typen auflisten. `Widget` und `DOMWidget`, die untern nicht aufgeführt sind, sind Basisklassen.


```python
import ipywidgets as widgets

# Zeige alle verfügbaren Widgets!
widgets.Widget.widget_types.values()
```




    dict_values([<class 'ipywidgets.widgets.widget_bool.Checkbox'>, <class 'ipywidgets.widgets.widget_bool.ToggleButton'>, <class 'ipywidgets.widgets.widget_bool.Valid'>, <class 'ipywidgets.widgets.widget_button.ButtonStyle'>, <class 'ipywidgets.widgets.widget_button.Button'>, <class 'ipywidgets.widgets.widget_box.Box'>, <class 'ipywidgets.widgets.widget_box.VBox'>, <class 'ipywidgets.widgets.widget_box.HBox'>, <class 'ipywidgets.widgets.widget_float.FloatText'>, <class 'ipywidgets.widgets.widget_float.BoundedFloatText'>, <class 'ipywidgets.widgets.widget_float.FloatSlider'>, <class 'ipywidgets.widgets.widget_float.FloatProgress'>, <class 'ipywidgets.widgets.widget_float.FloatRangeSlider'>, <class 'ipywidgets.widgets.widget_image.Image'>, <class 'ipywidgets.widgets.widget_int.IntText'>, <class 'ipywidgets.widgets.widget_int.BoundedIntText'>, <class 'ipywidgets.widgets.widget_int.SliderStyle'>, <class 'ipywidgets.widgets.widget_int.IntSlider'>, <class 'ipywidgets.widgets.widget_int.ProgressStyle'>, <class 'ipywidgets.widgets.widget_int.IntProgress'>, <class 'ipywidgets.widgets.widget_int.IntRangeSlider'>, <class 'ipywidgets.widgets.widget_int.Play'>, <class 'ipywidgets.widgets.widget_color.ColorPicker'>, <class 'ipywidgets.widgets.widget_date.DatePicker'>, <class 'ipywidgets.widgets.widget_selection.ToggleButtons'>, <class 'ipywidgets.widgets.widget_selection.Dropdown'>, <class 'ipywidgets.widgets.widget_selection.RadioButtons'>, <class 'ipywidgets.widgets.widget_selection.Select'>, <class 'ipywidgets.widgets.widget_selection.SelectionSlider'>, <class 'ipywidgets.widgets.widget_selection.SelectMultiple'>, <class 'ipywidgets.widgets.widget_selectioncontainer.Accordion'>, <class 'ipywidgets.widgets.widget_selectioncontainer.Tab'>, <class 'ipywidgets.widgets.widget_string.HTML'>, <class 'ipywidgets.widgets.widget_string.HTMLMath'>, <class 'ipywidgets.widgets.widget_string.Label'>, <class 'ipywidgets.widgets.widget_string.Textarea'>, <class 'ipywidgets.widgets.widget_string.Text'>, <class 'ipywidgets.widgets.widget_controller.Button'>, <class 'ipywidgets.widgets.widget_controller.Axis'>, <class 'ipywidgets.widgets.widget_controller.Controller'>, <class 'ipywidgets.widgets.widget_link.Link'>, <class 'ipywidgets.widgets.widget_link.DirectionalLink'>])



## Numerische Widgets

Es gibt 8 Widgets, die über iPython vertrieben werden, die dazu gedacht sind, numerische Werte anzuzeigen. Widgets existieren sowohl für Ganzzahlen (Integers), als auch für Kommazahlen (Floats), jeweils ohne Grenzen und mit. Die Ganzzahlen Widgets teilen eine gemeinsame Nomenklatur mit ihren Kommazahlen Gegenstücken. Durch das Ersetzen von `Float` durch `Int` im Widgetnamen, erhält man das Äquivalent.

### FloatSlider


```python
widgets.FloatSlider(
    value=7.5,
    min=5.0,
    max=10.0,
    step=0.1,
    description='Test:',
)
```



Slider können auch vertikal angezeigt werden.


```python
widgets.FloatSlider(
    value=7.5,
    min=5.0,
    max=10.0,
    step=0.1,
    description='Test',
    orientation='vertical',
)
```



### FloatProgress


```python
widgets.FloatProgress(
    value=7.5,
    min=5.0,
    max=10.0,
    step=0.1,
    description='Laden:',
)
```



### BoundedFloatText


```python
widgets.BoundedFloatText(
    value=7.5,
    min=5.0,
    max=10.0,
    description='Text:',
)
```



### FloatText


```python
widgets.FloatText(
    value=7.5,
    description='Any:',
)
```



## Boolean Widgets

Es gibt drei Widgets die dafür ausgelegt sind Boolean Werte anzuzeigen.

### ToogleButton


```python
widgets.ToggleButton(
    description='Klick mich',
    value=False,
)
```



### Checkbox


```python
widgets.Checkbox(
    description='Checke mich',
    value=True,
)
```



### Valid

Das valid Widget bietet einen "nur lesen" Indikator.


```python
widgets.Valid(
    value=True,
)
```



## Auswahl Widgets

Es gibt insgesamt vier Widgets, die dafür genutzt werden können, eine Einzelauswahl (selection) Liste anzuzeigen, und eines dafür, eine Mehrfahrauswahl anzuzeigen. Alle gehen von derselben Basisklasse aus. Wir können die Aufzählung der auswählbaren Optionen bestimmen, indem wir eine Liste übergeben. Außerdem können wir die Optionen als Dictionary übergeben, wodurch der Key als angezeigte Option und der Value als verarbeitbarer Wert behandelt werden.

### Dropdown


```python
from IPython.display import display
w = widgets.Dropdown(
    options=['1', '2', '3'],
    value='2',
    description='Nummer:',
)
display(w)
```




```python
# Wert anzeigen
w.value
```




    '3'



Das folgende ist ebenfalls gültig:


```python
w = widgets.Dropdown(
    options={'Eins': 1, 'Zwei': 2, 'Drei': 3},
    value=2,
    description='Nummer:')

display(w)
```




```python
# Wert anzeigen
w.value
```




    2



### RadioButtons


```python
widgets.RadioButtons(
    description='Pizzabelag:',
    options=['Pepperoni', 'Ananas', 'Pilze'],
)
```



### Select


```python
widgets.Select(
    description='OS:',
    options=['Linux', 'Windows', 'OSX'],
)
```



### ToggleButtons


```python
widgets.ToggleButtons(
    description='Geschwindigkeit:',
    options=['Schnell', 'Normal', 'Schnell'],
)
```



### SelectMultiple


```python
w = widgets.SelectMultiple(
    description="Früchte",
    options=['Apfel', 'Orange', 'Traube'])

display(w)
```




```python
w.value
```




    ('Orange', 'Traube')



## String Widgets

Insgesamt drei Widgets können dazu verwendet werden String Werte anzuzeigen. Von diesen sind es das `Text` und `Textarea` Widget, die eine Eingabe akzeptieren. Das `HTML` Widget zeigt den String als HTML an, lässt aber keine Eingabe zu.

### Text


```python
widgets.Text(
    description='String:',
    value='Hallo Welt',
)
```



### Textarea


```python
widgets.Textarea(
    description='String:',
    value='Hallo Welt',
)
```



### HTML


```python
widgets.HTML(
    value="Hello <b>World</b>"
)
```



### Button


```python
widgets.Button(description='Klick mich!')
```



## Schlussfolgerung

Diese Liste der Widgets könnt ihr als Referenz für zukünftige Projekte nutzen!

# Widget Styling

Quelle: Datamics

In dieser Lektion werden wir mehr darüber lernen, wie wir die vielen Möglichkeiten anwenden können, um Widgets zu stylen!


```python
%%html
<style>
.example-container { background: #999999; padding: 2px; min-height: 100px; }
.example-container.sm { min-height: 50px; }
.example-box { background: #9999FF; width: 50px; height: 50px; text-align: center; vertical-align: middle; color: white; font-weight: bold; margin: 2px;}
.example-box.med { width: 65px; height: 65px; }   
.example-box.lrg { width: 80px; height: 80px; }   
</style>
```


<style>
.example-container { background: #999999; padding: 2px; min-height: 100px; }
.example-container.sm { min-height: 50px; }
.example-box { background: #9999FF; width: 50px; height: 50px; text-align: center; vertical-align: middle; color: white; font-weight: bold; margin: 2px;}
.example-box.med { width: 65px; height: 65px; }   
.example-box.lrg { width: 80px; height: 80px; }   
</style>




```python
import ipywidgets as widgets
from IPython.display import display
```

## Grundlegendes Styling

Die Buttons, die wir durch iPython erzeugen, können durch folgende Eigenschaften angepasst werden:

* 'primary'
* 'success'
* 'info'
* 'warning'
* 'danger'

Das folgende Beispiel zeigt, wie ein Button Widget gestylt werden kann:


```python
button = widgets.Button(
    description='Hallo Welt!',
    button_style='info')
display(button)
```


    Button(button_style='info', description='Hallo Welt!', style=ButtonStyle())


## Eltern/Kind Beziehungen
Für die Darstellung mehrerer Widgets kann zuerst ein Layout angelegt werden:


```python
box_layout = widgets.Layout(display='flex', flex_flow='column', align_items='stretch', border='3px dotted red', width='40%')
```

Um ein Widget A innerhalb eines Widgets B anzuzeigen, muss Widget A ein Kind (child) von Widget B (parent) sein. Widgets, die andere Widgets beinhalten können, besitzen das `children` Attribut. Dieses Attribut kann durch einen Stichwort Parameter bei der Erstellung eines Widgets angegeben werden. Alternativ nach der Erstellung. Wenn wir display() auf ein Widget anwenden, dass ein Kind hat, wird dieses Kind automatisch auch angezeigt.


```python
float_range = widgets.FloatSlider()
string = widgets.Text(value='Hi')
container = widgets.Box(children=[float_range, string], layout=box_layout)

display(container) # Zeigt den Behälter an und alle seine "Kinder"
```


    Box(children=(FloatSlider(value=0.0), Text(value='Hi')), layout=Layout(align_items='stretch', border='3px dott…


### Nachdem das Eltern Widget angezeigt wurde

Kinder können auch definiert werden, nachdem das Eltern Widget angezeigt wurde. Das Eltern Element ist dafür verantwortlich, seine Kinder anzuzeigen.


```python
int_range = widgets.IntSlider()
container.children=[int_range]
display(container)
```


    Box(children=(IntSlider(value=0),), layout=Layout(align_items='stretch', border='3px dotted red', display='fle…


## Besondere Boxen

Wenn wir eine etwas kompliziertere Kombination von Widgets anzeigen möchten, können wir spezielle Behälter dafür benutzen. Um mehrere Widgets anzuzeigen, können wir `Accordion` oder `Tab` in Kombination mit einer Box benutzen (wie ihr unten sehen könnt). Die "Seiten" dieser Widgets sind ihre Kinder. Um den Titel der Seiten festzulegen nutzen wir `set_title`.

### Accordion


```python
name1 = widgets.Text(description='Position:')
zip1 = widgets.BoundedIntText(description='Zip:', min=0, max=99999)
seite1 = widgets.Box(children=[name1, zip1])

name2 = widgets.Text(description='Position:')
zip2 = widgets.BoundedIntText(description='Zip:', min=0, max=99999)
seite2 = widgets.Box(children=[name2, zip2])

accord = widgets.Accordion(children=[seite1, seite2], width=400)
display(accord)

accord.set_title(0, 'Von')
accord.set_title(1, 'Nach')
```


    Accordion(children=(Box(children=(Text(value='', description='Position:'), BoundedIntText(value=0, description…


### TabWidget


```python
name = widgets.Text(description='Name:', padding=4)
farbe = widgets.Dropdown(description='Farbe:', padding=4, options=['rot', 'orange', 'gelb', 'grün', 'blau', 'indigo', 'violet'])
seite1 = widgets.Box(children=[name, farbe], padding=4)

alter = widgets.IntSlider(description='Alter:', padding=4, min=0, max=120, value=50)
geschlecht = widgets.RadioButtons(description='Geschlecht:', padding=4, options=['männlich', 'weiblich'])
seite2 = widgets.Box(children=[alter, geschlecht], padding=4)

tabs = widgets.Tab(children=[seite1, seite2])
display(tabs)

tabs.set_title(0, 'Name')
tabs.set_title(1, 'Details')
```


    Tab(children=(Box(children=(Text(value='', description='Name:'), Dropdown(description='Farbe:', options=('rot'…


## Ausrichtung

Die meisten Widgets haben ein `description` (dt.: Beschreibung) Attribut. Dieses erlaubt uns, einen Namen zu vergeben. Der Name des Widgets hat eine fixierte Mindestbreite. Der Text des Namens ist immer rechts ausgerichtet und das Widget links.


```python
display(widgets.Text(description="a:"))
display(widgets.Text(description="aa:"))
display(widgets.Text(description="aaa:"))
```


    Text(value='', description='a:')



    Text(value='', description='aa:')



    Text(value='', description='aaa:')


Sollte der Name des Widgets länger als die Mindestbreite sein, wird das Widget nach rechts verschoben:


```python
display(widgets.Text(description="a:"))
display(widgets.Text(description="aa:"))
display(widgets.Text(description="aaa:"))
display(widgets.Text(description="aaaaaaaaaaaaa:"))
```


    Text(value='', description='a:')



    Text(value='', description='aa:')



    Text(value='', description='aaa:')



    Text(value='', description='aaaaaaaaaaaaa:')


Sofern kein Name vergeben ist wird auch keiner angezeigt.


```python
display(widgets.Text(description="a:"))
display(widgets.Text(description="aa:"))
display(widgets.Text(description="aaa:"))
display(widgets.Text())
```


    Text(value='', description='a:')



    Text(value='', description='aa:')



    Text(value='', description='aaa:')



    Text(value='')


## Flex Boxen

Widgets können ausgerichtet werden indem wir `FlexBox`, `HBox` und `VBox` Widgets verwenden.

### Anwendung auf Widgets

Widgets werden per Standard vertikal ausgegeben:


```python
buttons = [widgets.Button(description=str(i)) for i in range(3)]
display(*buttons)
```


    Button(description='0', style=ButtonStyle())



    Button(description='1', style=ButtonStyle())



    Button(description='2', style=ButtonStyle())


### HBox anwenden

Um Widgets horizontal auszugeben, können sie als Kinder von einem HBox Widget angelegt werden.


```python
container = widgets.HBox(children=buttons)
display(container)
```


    HBox(children=(Button(description='0', style=ButtonStyle()), Button(description='1', style=ButtonStyle()), But…


## Sichtbarkeit

Die `visibile` Eigenschaft eines Widgets kann genutzt werden, um Widgets auszublenden oder anzuzeigen, die bereits erzeugt wurden. Die `visible` Eigenschaft kann folgende Werte annehmen:

* True - das Widget wird angezeigt
* False - das Widget wird ausgeblendet und ebenso der leere Platz, an dem es stehen würde
* None - das Widget wird ausgeblendet, der leere Platz jedoch nicht


```python
w1 = widgets.Text(value="Erste Zeile")
w2 = widgets.Text(value="Zweite Zeile")
w3 = widgets.Text(value="Dritte Zeile")
display(w1, w2, w3)
```


    Text(value='Erste Zeile')



    Text(value='Zweite Zeile')



    Text(value='Dritte Zeile')



```python
w2.layout.visibility = None
```


```python
w2.layout.visibility = 'hidden'
```


```python
w2.layout.visibility = 'visible'
```

### Weiteres Beispiel

Im untenstehenden Beispiel wird ein Formular erzeugt, das bestimmte Widgets in Abhängigkeit von anderen Widgets anzeigt. Versucht die "Student" Check-Box umzuschalten.


```python
form = widgets.VBox()
vorname = widgets.Text(description="Vorname:")
nachname = widgets.Text(description="Nachname:")

student = widgets.Checkbox(description="Student:", value=False)
school_info = widgets.VBox(visible=False, children=[
    widgets.Text(description="Schule:"),
    widgets.IntText(description="Note:", min=0, max=12)
    ])

haustier = widgets.Text(description="Haustier:")
form.children = [vorname, nachname, student, schul_info, haustier]
display(form)

def on_student_toggle(value):
    if value:
        school_info.visible = True
    else:
        school_info.visible = False
student.observe(on_student_toggle, 'value')
```


    VBox(children=(Text(value='', description='Vorname:'), Text(value='', description='Nachname:'), Checkbox(value…


## Abschließende Bemerkung

Jetzt solltet ihr verstanden haben, wie wir Widgets stylen können!

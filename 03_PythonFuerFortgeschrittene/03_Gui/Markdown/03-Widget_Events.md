# Widget Events

Quelle: Datamics

In dieser Lektion besprechen wir Events, die Widgets passieren können, wie bspw. der Klick auf einen Button!

## Spezielle Events

Der `Button` wird nicht genutzt, um einen Datentyp zu repräsentieren. Stattdessen wird das Button Widget verwendet, um Klicks mit der Maus zu handhaben. Die `on_click` Mehode des `Button` kann verwendet werden, um Funktionen aufzurufen, sobald der Button geklickt wird. Die Dokumentation von `on_click` seht ihr unterhalb.


```python
import ipywidgets as widgets
print(widgets.Button.on_click.__doc__)
```

    Register a callback to execute when the button is clicked.
    
            The callback will be called with one argument, the clicked button
            widget instance.
    
            Parameters
            ----------
            remove: bool (optional)
                Set to true to remove the callback from the list of callbacks.
            


### Beispiel

Da Button Klicks zustandslos sind, werden sie vom Frontend an das Backend durch eine benutzerdefinierte Nachricht übergeben. Durch Verwendung der `on_click` Methode wird der Button unterhalb eine Nachricht anzeigen, sobald er geklickt wird.


```python
from IPython.display import display
button = widgets.Button(description="Klick mich!")
display(button)

def button_geklickt(b):
    print("Button geklickt.")

button.on_click(button_geklickt)
```



## on_submit

Das `Text` Widget hat ein spezielles `on_submit` Event. Das `on_submit` Event wird ausgelöst, wenn der Nutzer Enter drückt.


```python
text = widgets.Text()
display(text)

def enter_druck(sender):
    print(text.value)

text.on_submit(enter_druck)
```



## Traitlet Events

Widget Eigenschaften sind iPython Traitlets und Traitlets sind ereignisreich. Um Veränderungen zu managen kann die `on_trait_change` Methode der Widgets verwendet werden, die einen Rückruf (en.: callback) registriert. Die Dokumentation für `on_trait_change` kann unterhalb eingesehen werden.


```python
print(widgets.Widget.on_trait_change.__doc__)
```

    DEPRECATED: Setup a handler to be called when a trait changes.
    
            This is used to setup dynamic notifications of trait changes.
    
            Static handlers can be created by creating methods on a HasTraits
            subclass with the naming convention '_[traitname]_changed'.  Thus,
            to create static handler for the trait 'a', create the method
            _a_changed(self, name, old, new) (fewer arguments can be used, see
            below).
    
            If `remove` is True and `handler` is not specified, all change
            handlers for the specified name are uninstalled.
    
            Parameters
            ----------
            handler : callable, None
                A callable that is called when a trait changes.  Its
                signature can be handler(), handler(name), handler(name, new),
                handler(name, old, new), or handler(name, old, new, self).
            name : list, str, None
                If None, the handler will apply to all traits.  If a list
                of str, handler will apply to all names in the list.  If a
                str, the handler will apply just to that name.
            remove : bool
                If False (the default), then install the handler.  If True
                then unintall it.
            


### Signaturen

Wie wir der Dokumentation entnehmen können kann der Rückruf 4 mögliche Signaturen haben:

* callback()
* callback(trait_name)
* callback(trait_name, new_value)
* callback(trait_name, old_value, new_value)

Unter Verwendung dieser Methode folgt jetzt ein Beispiel wie der Wert eines IntSliders ausgegeben werden kann, während er sich ändert:


```python
int_range = widgets.IntSlider()
display(int_range)

def anderer_wert(value):
    print(value)
 
int_range.observe(anderer_wert, 'value')
```



## Widgets verknüpfen

Oftmals könntet ihr einfach Widget Attribute verknüpfen wollen. Die Synchronisation von Attributen kann einfacher erfolgen, als durch Nutzung von Traitlets Events.

### Traitlets Attribute serverseitig verknüpfen

Die erste Methode ist die Verwendung der `link` und `dlink` Funktionen aus dem `traitlets` Modul.


```python
import traitlets
```


```python
# Überschrift erstellen
ueberschrift = widgets.Label(value = 'Die Werte von Slider1 und Slider2 sind synchronisiert.')

# IntSlider erstellen
slider1 = widgets.IntSlider(description='Slider 1')
slider2 =  widgets.IntSlider(description='Slider 2')

# Trailets zum Verknüpfen verwenden
l = traitlets.link((slider1, 'value'), (slider2, 'value'))

# Anzeigen!
display(ueberschrift, slider1, slider2)
```








```python
# Überschrift erstellen
ueberschrift = widgets.Label(value = 'Änderungen der Quelle werden im Ziel angezeigt.')

# IntSlider erstellen
quelle = widgets.IntSlider(description='Quelle')
ziel1 =  widgets.IntSlider(description='Ziel 1')

# Trailets zum Verknüpfen verwenden
dl = traitlets.dlink((quelle, 'value'), (ziel1, 'value'))

# Anzeigen!
display(ueberschrift, quelle, ziel1)
```







Die Funktionen `traitlets.link` und `traitlets.dlink` geben ein `Link` bzw. `DLink` Objekt zurück. Diese Verknüpfung kann durch die `unlink` Methode aufgehoben werden.


```python
# Je nach Ausführung könnte ein Error auftauchen
l.unlink()
dl.unlink()
```

### Traitlets Attribute klientseitig verknüpfen

Wenn wir Traitlets Attribute synchronisieren könnte es zu Verzögerungen aufgrund der "Rundreise" zum Server kommen. Wir können Widget Attribute auch direkt im Browser verknüpfen, indem wir Link Widgets verwenden. Dies geht einseitig oder beidseitig.


```python
# Version ohne Verzögerung
ueberschrift = widgets.Label(value = 'Die Werte von Slider1 und Slider2 sind synchronisiert.')

# IntSlider erstellen
slider1 = widgets.IntSlider(description='Slider 1')
slider2 =  widgets.IntSlider(description='Slider 2')

# Trailets zum Verknüpfen verwenden
l = widgets.jslink((slider1, 'value'), (slider2, 'value'))

# Anzeigen!
display(ueberschrift, slider1, slider2)
```








```python
# Version ohne Verzögerung
ueberschrift = widgets.Label(value = 'Änderungen der Quelle werden im Ziel angezeigt.')

# IntSlider erstellen
quelle = widgets.IntSlider(description='Quelle')
ziel1 =  widgets.IntSlider(description='Ziel 1')

# Trailets zum Verknüpfen verwenden
dl = widgets.jsdlink((quelle, 'value'), (ziel1, 'value'))

# Anzeigen!
display(ueberschrift, quelle, ziel1)
```







Die Funktionen `widgets.jslink` und `widgets.jsdlink` geben ein Link Widget zurück. Diese Verknüpfung kann durch die `unlink()` Methode aufgehoben werden.


```python
l.unlink()
dl.unlink()
```

## Abschluss

Ihr solltet nun gut mit der Verknüpfung von Widgets umgehen können!

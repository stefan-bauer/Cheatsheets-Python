# Module, Pakete und Importe

Quelle: Datamics

## Was sind Module?

Die Verwendung von Modulen in der Programmierung basiert auf dem Konzept des modularen Designs. Dies ist ein Konzept, dass aus dem Ingeniuerwesen stammt. Es hat sich lange vor Computern entwickelt. 

Mit modularem Design bezeichnet man die Zerlegung eines komplexen Gesamtsystems in einzelne Einheiten, die für sich genommen selbstständig funktionieren können. Und genau diese Einheiten nennt man häufig "*Module*". 

## Warum sind Module wichtig?

Module finden sich in sehr vielen Produkten wieder. Prominente Beispiele sind Autos, Smartphones und Computer. Insbesondere letztere sind so weit modularisiert, wie es nur geht. Das gilt für die Hardware ebenso, wie für die Software, die auf den Rechnern läuft.

Sie sind deshalb so extrem wichtig, weil sie es ermöglichen, lesbare, zuverlässige und insbesondere gut wartbare Programme zu schreiben. Gerade bei großen Software-Projekten ermöglichen sie eine einfacherer Entwicklungsarbeit. Dabei geht man so vor, dass Programme in logische Teilblöcke (die Module) zerlegt werden. Diese können von unterschiedlichen Teams bearbeitet und später kombiniert werden.

## Module in Python

Es gibt in dieser Lektion nicht wirklich viel Code, da es für die Inhalte nur an wenigen Stellen Sinn ergibt. Schaut euch die Video Lektion und die zusätzlichen Ressourcen an, um mehr Infos zu erhalten.

Hierfür ist die [offizielle Dokumentation](https://docs.python.org/3/tutorial/modules.html) die beste Quelle.

Noch etwas extra Info, um zu helfen:

Module und Pakete in Python sind einfach Python Dateien mit der .py Endung. Sie implementieren eine Reihe von Funktionen. Module werden durch das `import` Kommando importiert.

Um ein Modul zu importieren nutzen wir das `import` Kommando. Schaut euch dazu auch die vollständige Liste der vorinstallierten (built-in) Module an.

Wenn ein Modul das erste Mal in ein Python Skript geladen wird, erfolgt die Initialisierung durch einmaliges Ausführen des Modul Codes. Wenn ein anderes Modul nun ein bereits geladenes Modul enthält, wird dieses nicht ein zweites mal geladen

Wenn wir beispielsweise das `math` Modul importieren wollen, tippen wir einfach:


```python
# Die Library importieren
import math
```


```python
# Anwendung (Aufrunden)
math.ceil(2.4)
```




    3



## Beinhaltete Module erkunden

Zwei sehr wichtige Funktionen, um Module zu erkunden, sind die `dir` und die `help` Funktion.

Wir können schauen, welche Funktionen in einem Modul beinhaltet sind, indem wir `dir` nutzen:


```python
print(dir(math))
```

    ['__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'acos', 'acosh', 'asin', 'asinh', 'atan', 'atan2', 'atanh', 'ceil', 'copysign', 'cos', 'cosh', 'degrees', 'e', 'erf', 'erfc', 'exp', 'expm1', 'fabs', 'factorial', 'floor', 'fmod', 'frexp', 'fsum', 'gamma', 'gcd', 'hypot', 'inf', 'isclose', 'isfinite', 'isinf', 'isnan', 'ldexp', 'lgamma', 'log', 'log10', 'log1p', 'log2', 'modf', 'nan', 'pi', 'pow', 'radians', 'sin', 'sinh', 'sqrt', 'tan', 'tanh', 'tau', 'trunc']


Sobald wir die Funktion gefunden haben, die wir aus einem bestimmten Modul benutzen wollen, können wir mehr darüber erfahren, indem wir `help` nutzen.


```python
help(math.ceil)
```

    Help on built-in function ceil in module math:
    
    ceil(...)
        ceil(x)
        
        Return the ceiling of x as an Integral.
        This is the smallest integer >= x.
    


## Module schreiben

Python Module zu schreiben ist sehr einfach. Was müssen wir also tun, um ein Modul zu erstellen? Dazu erstellt man einfach eine .py Datei mit dem Namen des Moduls. Diese kann dann mit dem Python Dateinamen (ohne .py Endung) und `import` importiert werden.

## Pakete schreiben

Wenn ein Programm oder Projekt immer umfangreicher wird kann es passieren, dass selbst die Anzahl unserer Module sehr groß wird. Das erschwert es, die Gesamtheit des Codes nachzuvollziehen und zu warten. Was können wir also tun, um zu verhindern, dass wir den Überblick über unsere Module verlieren? Pakete "schnüren".

Pakete sind Namensräume die selbst mehrere Pakete und Module beinhalten. Sie sind einfach Verzeichnisse, allerdings mit einem Twist.

Jedes Paket in Python ist ein Verzeichnis (Ordner), welches eine spezielle Datei namens **\__init\__.py** beinhalten muss. Diese Datei kann leer sein; sie zeigt lediglich an, dass das entsprechende Verzeichnis ein Python Paket ist, das wie ein Modul importiert werden kann.

Wenn wir ein Verzeichnis erstellen, dass `foo` heißt, können wir darin ein Modul erstellen, das `bar` heißt. Außerdem müssen wir an die **\__init\__.py** Datei denken.

Um das Modul `bar` zu nutzen, können wir es auf zwei Arten importieren:


```python
# Nur ein Beispiel, funktioniert hier nicht
import foo.bar
```


```python
# oder auf diese Weise
from foo import bar
```

Bei der ersten Variante müssen wir immer das foo Präfix benutzen, wenn wir das Modul bar adressieren wollen. Bei der zweiten Variante müssen wir das nicht, da wir das Modul zu unserem Module  Namensraum hinzugefügt haben.

Die **\__init\__.py** Datei kann darüber entscheiden, welche Module das Paket als API exportiert, während andere Module intern gehalten werden, indem wir die **\__all\__** Variable überschreiben:


```python
__init__.py:

__all__ = ["bar"]
```

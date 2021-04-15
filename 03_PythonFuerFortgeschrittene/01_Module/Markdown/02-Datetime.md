# Datetime

Quelle: Datamics

Python hat das `datetime` Modul integriert, um dabei zu helfen, mit Zeitstempeln in eurem Code zu arbeiten. Zeitwerte werden durch die Zeit Klasse repräsentiert. Zeiten haben Attribute für Stunden, Minuten, Sekunden und Mikrosekunden. Sie können außerdem Zeitzoneninformation beinhalten. Die Parameter, um eine Zeit aufzusetzen, sind optional und per Standard auf 0 gesetzt. Das wird aber kaum die Zeit sein, die ihr angeben wollt.

## time

Lasst uns betrachten, wie wir Zeitinformationen aus dem `datetime` Modul auslesen. Wir können einen Zeitstempel erstellen, indem wir datetime.time(hour,minute,second,microsecond) definieren.


```python
import datetime

t = datetime.time(4,20,1)

# Lasst uns die Bestandteile betrachten

print(t)
print('Stunde:',t.hour)
print('Minute:',t.minute)
print('Sekunde:',t.second)
print('Mikrosekunde:',t.microsecond)
print('Zeitzone:',t.tzinfo)
```

    04:20:01
    Stunde: 4
    Minute: 20
    Sekunde: 1
    Mikrosekunde: 0
    Zeitzone: None


Achtet darauf, dass eine time Einheit nur Werte für Zeit, nicht jedoch für das Datum, beinhaltet. 

Wir können uns auch die Mindest- und Höchstwerte für Zeitwerte anschauen:


```python
print('Mindestwert:',datetime.time.min)
print('Höchstwert:',datetime.time.max)
print('Schrittgröße:',datetime.time.resolution)
```

    Mindestwert: 00:00:00
    Höchstwert: 23:59:59.999999
    Schrittgröße: 0:00:00.000001


## Date

datetime (wie ihr euch bestimmt denken könnt) erlaubt es uns auch, mit Datumsstempeln zu arbeiten. Kalenderdaten werden durch die `date` Klasse repräsentiert. Sie besitzen Parameter für das Jahr, den Monat und den Tag. Es ist allerdings einfacher ein Datum zu erstellen, dass den heutigen Tag wiederspiegelt, indem wir today() verwenden.

Hier einige Beispiele:


```python
today = datetime.date.today()
print(today)
print('Weltzeit',today.ctime())
print('Tupel:',today.timetuple())
print('Ordinal:',today.toordinal())
print('Jahr:',today.year)
print('Monat :',today.month)
print('Tag :',today.day)
```

    2017-05-02
    Weltzeit Tue May  2 00:00:00 2017
    Tupel: time.struct_time(tm_year=2017, tm_mon=5, tm_mday=2, tm_hour=0, tm_min=0, tm_sec=0, tm_wday=1, tm_yday=122, tm_isdst=-1)
    Ordinal: 736451
    Jahr: 2017
    Monat : 5
    Tag : 2


Genau wie bei time, können wir uns Mindest- und Höchstwerte ausgeben lassen, indem wir min und max verwenden.


```python
print('Mindestwert:',datetime.date.min)
print('Höchstwert:',datetime.date.max)
print('Schrittgröße:',datetime.date.resolution)
```

    Mindestwert: 0001-01-01
    Höchstwert: 9999-12-31
    Schrittgröße: 1 day, 0:00:00


Ein anderer Weg um neue Datumseinheiten zu erzeugen ist die Verwendung der replace() Methode mit einem bestehenden Datum. Zum Beispiel können wir das Jahr ändern und Tag und Monat unberührt lassen.


```python
d1 = datetime.date(2017,5,2)
print('d1:',d1)

d2 = d1.replace(year=1990)
print('d2:',d2)
```

    d1: 2017-05-02
    d2: 1990-05-02


## Arithmetik

Wir können mit auch Arithmetik auf date Einheiten anwenden:


```python
d1
```




    datetime.date(2017, 5, 2)




```python
d2
```




    datetime.date(1990, 5, 2)




```python
d1-d2
```




    datetime.timedelta(9862)



Wir erhalten die Differenz zwischen den beiden Daten in Tagen. Wir können die `timedelta` Methode verwenden, um verschiedenste Einheiten von Zeit zu spezifizieren (Tage, Minuten, Stunden,...).

Toll! Durch diese Lektion solltest du ein gutes Grundverständnis für `time` und `date` Einheiten bekommen haben und Zeitstempel in deinem Code verwenden können!

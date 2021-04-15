# Web Scraping in Python

Quelle: Datamics

In dieser Lektion schauen wir uns in einem Beispiel an, wie man mit Python Informationen aus dem Web zieht.


##### Wir werden jetzt die folgenden Schritte ausführen

1.) Wir gehen auf eine Webseite

2.) suchen uns Informationen die wir haben möchten 

3.) schauen uns an wo diese gespeichert wird 

4.) Danach extrahieren wir diese

5.) und speichern die Information als ein Pandas DataFrame!

#### Allerdings solltest Du diese Dinge in Betracht ziehen, bevor Du mit dem scrapen einer Webseite beginnst:

1.) Auf jeden fall solltest Du die *"Terms and Conditions"* der Web Seite anschauen

2.) Sparsam mit den Anfragen umgehen damit der Zielserver nicht überlastet wird. Ansonsten kannst du blockiert werden.

3.) "Scrapers" werden im Laufe der Zeit fehlerhaft, da Webseiten ihr Layout ständig ändern. Du wirst wahrscheinlich häufig Deinen Code Anpassen müssen. 

4.) Webseiten sind gewöhnlich inkonsistent, daher wirst du wahrscheinlich die Daten nach dem einlesen aufbereiten müssen.

5.) Jede Webseite und jede Situation ist unterschiedlich, daher wirst du viel Zeit für die Konfiguration Deines Scrapers aufbringen.


#### Um mehr über HTML zu lernen, empfehle ich die folgenden Seiten: 

[SELFHTML](https://wiki.selfhtml.org/wiki/HTML/Tutorials)

[W3School](http://www.w3schools.com/html/)




#### Wir müssen die folgenden 3 Python Pakete installieren (falls noch nicht installiert):

1.) **BeautifulSoup: **
    *pip install beautifulsoup4* or *conda install beautifulsoup4* 

2.) **lxml:** 
    *pip install lxml* oder *conda install lxml* 

3.) **requests:** 
    *pip install requests* oder *conda install requests*



Beginnen wir mit den Importen:


```python
from bs4 import BeautifulSoup
import requests
```


```python
import pandas as pd
from pandas import Series,DataFrame
```

Für unser kurzes Web Scraping Tutorial schauen wir uns Berichte von der Webseite der University of California an. Ihr könnt natürlich gerne weitere Webseiten selbst ausprobieren. Seid dabei allerdings bitte respektvoll und vorsichtig mit dem was und mit der Menge die ihr "scrapt". Überprüft vorher auch auf jeden Fall noch die rechtliche Grundlage für ein automatisches Auslesen des Inhalts der Webseite.


OK, fangen wir an und legen die URL fest.


```python
url = 'http://www.ucop.edu/operating-budget/budgets-and-reports/legislative-reports/2013-14-legislative-session.html'
```

Als nächstes verwenden wir requests um den Inhalt der Webseite zu laden und definieren dieses als ein Beautiful Soup Object.


```python
# Request Inhalt der Webseite
result = requests.get(url)
c = result.content

# Beautiful Soup Object
soup = BeautifulSoup(c, "html5lib")
```

Jetzt verwenden wir Beautiful Soup um die Tabelle zu finden, die wir nehmen möchten! 



```python
# Gehe zur Sektion mit den Informationen
summary = soup.find("div",{'class':'list-land','id':'content'})

# Finde die Tabellen in dem HTML
tables = summary.find_all('table')

```

Jetzt benötigen wir Beautiful Soup um die Tabelleneinträge zu finden. Ein 'td' Tag definiert eine Standardzelle in einer HTML Tabelle. Der 'tr' Tag definiert eine Zeile in einer HTML Tabelle.

Wir parsen durch unser Tabellenobjekt und versuchen jede Zelle mit der findALL('td') Methode zu finden.

Es gibt viele Möglichkeiten um findALL mit Beautiful Soup zu verwenden. Du kannst diese gerne  [hier](http://www.crummy.com/software/BeautifulSoup/bs4/doc/#find-all) nachlesen.

 


```python
# Definiere eine leere Liste data
data = []

# Setzte rows (Zeilen) als erstes indexierte Objekt in der Tabelle mit einer Zeile
rows = tables[0].findAll('tr')

# Jetzt lesen wir jede HTML-Zelle aus jeder Zeile aus
for tr in rows:
    cols = tr.findAll('td')
    # Überprüfe, ob die Zelle einen Text enthält
    for td in cols:
        text = td.find(text=True) 
        print (text)
        data.append(text)
    
```

    1
    08/01/13
    2013-14 (EDU 92495) Proposed Capital Outlay Projects (2013-14 only) (pdf)
    2
    09/01/13
    2014-15  (EDU 92495) Proposed Capital Outlay Projects (pdf)
    3
    11/01/13
    Utilization of Classroom and Teaching Laboratories (pdf)
    4
    11/01/13
    Instruction and Research Space Summary & Analysis (pdf)
    5
    11/15/13
    Statewide Energy Partnership Program (pdf)
    6
    11/30/13
    2013-23 Capital Financial Plan (pdf)
    7
    11/30/13
    Projects Savings Funded from Capital Outlay Bond Funds (pdf)
    8
    12/01/13
    Streamlined Capital Projects Funded from Capital (pdf)
    9
    01/01/14
    Annual General Obligation Bonds Accountability (pdf)
    10
    01/01/14
    Small Business Utilization (pdf)
    11
    01/01/14
    Institutional Financial Aid Programs - Preliminary report (pdf)
    12
    01/10/14
    Summer Enrollment (pdf)
    13
    01/15/14
    Contracting Out for Services at Newly Developed Facilities (pdf)
    14
    03/01/14
    Performance Measures (pdf)
    15
    03/01/14
    Entry Level Writing Requirement (pdf)
    16
    03/31/14
    Annual Report on Student Financial Support (pdf)
    17
    04/01/14
    Unique Statewide Pupil Identifier (pdf)
    18
    04/01/14
    Riverside School of Medicine (pdf)
    19
    04/01/14
    SAPEP Funds and Outcomes - N/A
    20
    05/15/14
    Receipt and Use of Lottery Funds (pdf)
    21
    07/01/14
    Cogeneration and Energy Consv Major Capital Projects (pdf)
    
    
    
    
    
    
     
    Future Reports
    
    
    24
    12-
    Breast Cancer Research Fund
    25
    12-31-15
    Cigarette and Tobacco Products Surtax Research Program
    26
    01-01-16
    Best Value Program
    27
    01-01-16
    California Subject Matter Programs
    28
    04-01-16
    COSMOS Program Outcomes


Schauen wir unsere Liste "data" nochmal genauer an.


```python
data
```




    ['1',
     '08/01/13',
     '2013-14 (EDU 92495) Proposed Capital Outlay Projects (2013-14 only) (pdf)',
     '2',
     '09/01/13',
     '2014-15\xa0 (EDU 92495) Proposed Capital Outlay Projects (pdf)',
     '3',
     '11/01/13',
     'Utilization of Classroom and Teaching Laboratories (pdf)',
     '4',
     '11/01/13',
     'Instruction and Research Space Summary & Analysis (pdf)',
     '5',
     '11/15/13',
     'Statewide Energy Partnership Program (pdf)',
     '6',
     '11/30/13',
     '2013-23 Capital Financial Plan (pdf)',
     '7',
     '11/30/13',
     'Projects Savings Funded from Capital Outlay Bond Funds (pdf)',
     '8',
     '12/01/13',
     'Streamlined Capital Projects Funded from Capital (pdf)',
     '9',
     '01/01/14',
     'Annual General Obligation Bonds Accountability (pdf)',
     '10',
     '01/01/14',
     'Small Business Utilization (pdf)',
     '11',
     '01/01/14',
     'Institutional Financial Aid Programs - Preliminary report (pdf)',
     '12',
     '01/10/14',
     'Summer Enrollment (pdf)',
     '13',
     '01/15/14',
     'Contracting Out for Services at Newly Developed Facilities (pdf)',
     '14',
     '03/01/14',
     'Performance Measures (pdf)',
     '15',
     '03/01/14',
     'Entry Level Writing Requirement (pdf)',
     '16',
     '03/31/14',
     'Annual Report on Student\xa0Financial Support (pdf)',
     '17',
     '04/01/14',
     'Unique Statewide Pupil Identifier (pdf)',
     '18',
     '04/01/14',
     'Riverside School of Medicine (pdf)',
     '19',
     '04/01/14',
     'SAPEP Funds and Outcomes - N/A',
     '20',
     '05/15/14',
     'Receipt and Use of Lottery Funds (pdf)',
     '21',
     '07/01/14',
     'Cogeneration and Energy Consv Major Capital Projects (pdf)',
     '\n',
     '\n',
     '\n',
     '\xa0',
     'Future Reports',
     '\n',
     '24',
     '12-',
     'Breast Cancer Research Fund',
     '25',
     '12-31-15',
     'Cigarette and Tobacco Products Surtax Research Program',
     '26',
     '01-01-16',
     'Best Value Program',
     '27',
     '01-01-16',
     'California Subject Matter Programs',
     '28',
     '04-01-16',
     'COSMOS Program Outcomes']



Jetzt könenn wir eine For-Schleife einsetzten um durch die Liste zu iterieren. Dabei nehmen wir nur die Zellen die ein  PDF Dokument beinhalten. Außerdem müssen wir den Index mit dem Datum des Berichts auslesen.




```python
# Definiere die leeren Listen
reports = []
date = []

# Definiere den Indexzähler
index = 0

# Suche die PDF Zellen
for item in data:
    if 'pdf' in item:
        # Füge das Datum des Berichts hinzu
        date.append(data[index-1])
        
        # Entferne \xa0
        reports.append(item.replace(u'\xa0', u' '))
                    
    index += 1
```

Jetzt müssen wir nur noch unsere Daten in einem Pandas DataFrame speichern!


```python
# Dazu wandeln wir date und reports in Series um
date = Series(date)
reports = Series(reports)
```


```python
# Fügen diese zu einem DataFrame zusammen
legislative_df = pd.concat([date,reports],axis=1)
```


```python
# Definieren die Spalten
legislative_df.columns = ['Datum','Bericht']
```


```python
# und schauen uns das DataFrame an
legislative_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Reports</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>08/01/13</td>
      <td>2013-14 (EDU 92495) Proposed Capital Outlay Pr...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>09/01/13</td>
      <td>2014-15  (EDU 92495) Proposed Capital Outlay P...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>11/01/13</td>
      <td>Utilization of Classroom and Teaching Laborato...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>11/01/13</td>
      <td>Instruction and Research Space Summary &amp; Analy...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>11/15/13</td>
      <td>Statewide Energy Partnership Program (pdf)</td>
    </tr>
    <tr>
      <th>5</th>
      <td>11/30/13</td>
      <td>2013-23 Capital Financial Plan (pdf)</td>
    </tr>
    <tr>
      <th>6</th>
      <td>11/30/13</td>
      <td>Projects Savings Funded from Capital Outlay Bo...</td>
    </tr>
    <tr>
      <th>7</th>
      <td>12/01/13</td>
      <td>Streamlined Capital Projects Funded from Capit...</td>
    </tr>
    <tr>
      <th>8</th>
      <td>01/01/14</td>
      <td>Annual General Obligation Bonds Accountability...</td>
    </tr>
    <tr>
      <th>9</th>
      <td>01/01/14</td>
      <td>Small Business Utilization (pdf)</td>
    </tr>
    <tr>
      <th>10</th>
      <td>01/01/14</td>
      <td>Institutional Financial Aid Programs - Prelimi...</td>
    </tr>
    <tr>
      <th>11</th>
      <td>01/10/14</td>
      <td>Summer Enrollment (pdf)</td>
    </tr>
    <tr>
      <th>12</th>
      <td>01/15/14</td>
      <td>Contracting Out for Services at Newly Develope...</td>
    </tr>
    <tr>
      <th>13</th>
      <td>03/01/14</td>
      <td>Performance Measures (pdf)</td>
    </tr>
    <tr>
      <th>14</th>
      <td>03/01/14</td>
      <td>Entry Level Writing Requirement (pdf)</td>
    </tr>
    <tr>
      <th>15</th>
      <td>03/31/14</td>
      <td>Annual Report on Student Financial Support (pdf)</td>
    </tr>
    <tr>
      <th>16</th>
      <td>04/01/14</td>
      <td>Unique Statewide Pupil Identifier (pdf)</td>
    </tr>
    <tr>
      <th>17</th>
      <td>04/01/14</td>
      <td>Riverside School of Medicine (pdf)</td>
    </tr>
    <tr>
      <th>18</th>
      <td>05/15/14</td>
      <td>Receipt and Use of Lottery Funds (pdf)</td>
    </tr>
    <tr>
      <th>19</th>
      <td>07/01/14</td>
      <td>Cogeneration and Energy Consv Major Capital Pr...</td>
    </tr>
  </tbody>
</table>
</div>



Du kannst natürlich gerne weitere Webseiten selbst ausprobieren. Sei dabei allerdings bitte respektvoll und vorsichtig mit dem was und mit der Menge die ihr "scrapt". Überprüfe vorher auch auf jeden Fall noch die rechtliche Grundlage für ein automatisches Auslesen des Inhalts der Webseite.


## Gute Arbeit!

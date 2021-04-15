<a href="https://www.datamics.com/courses/online-courses/">![title](bg_datamics_top.png)</a>

<center><em>© Datamics</em></center><br><center><em>Besuche uns für mehr Informationen auf <a href='https://www.datamics.com/courses/online-courses/'>www.datamics.com</a></em>
    
# Wahlanalyse Projekt - Aufgabe

In diesem Datenprojekt werden wir uns Daten der US Wahl von 2012 anschauen.

Wir werden dazu zwei Datensätze analysieren. Der erste wird die Ergebnisse einer Umfrage zur Wahl von Obama vs. Romney an. Es gibt einige Fragen, denen wir uns annehmen möchten:

1. Wer wurde befragt und zu welcher Partei fühlten sie sich zugehörig?
2. Haben die Umfrageergebnisse Romney oder Obama favorisiert?
3. Wie beinflussen unentschiedene Wähler die Umfrage?
4. Können wir auf die unentschiedenen Wähler Rücksicht nehmen?
5. Wie hat sich die Wählerschaft über die Zeit verändert?
6. Können wir einen Einfluss der TV-Debatten auf die Umfrageergebnisse feststellen?

Den zweiten Datensatz besprechen wir später. 
    
# Datensatz herunterladen
Lade den Datensatz von der Adresse herunter https://datamics.com/download/election_donor_data/ und speichere ihn im Verzeichnis dieses Notebooks.

**Importiere zuerst `Pandas`, aus Pandas im Speziellen `Series` und `DataFrame` und zusätzlich `Numpy`.**


```python

```

**Importiere `Matplotlib`, `Seaborn`, setze den Seaborn Style auf "whitegrid" fest und matplotlib "inline".**


```python

```

**Lies die Daten aus `poll.csv` (dt. Umfrage) in einen DataFrame namens "poll_df" ein.**


```python

```

**Schaue dir die `info()`, `describe()` und `head()` zum DataFrame an.**


```python

```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 586 entries, 0 to 585
    Data columns (total 17 columns):
    Pollster                  586 non-null object
    Start Date                586 non-null object
    End Date                  586 non-null object
    Entry Date/Time (ET)      586 non-null object
    Number of Observations    564 non-null float64
    Population                586 non-null object
    Mode                      586 non-null object
    Obama                     586 non-null float64
    Romney                    586 non-null float64
    Undecided                 423 non-null float64
    Other                     202 non-null float64
    Pollster URL              586 non-null object
    Source URL                584 non-null object
    Partisan                  586 non-null object
    Affiliation               586 non-null object
    Question Text             0 non-null float64
    Question Iteration        586 non-null int64
    dtypes: float64(6), int64(1), object(10)
    memory usage: 77.9+ KB



```python

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
      <th>Number of Observations</th>
      <th>Obama</th>
      <th>Romney</th>
      <th>Undecided</th>
      <th>Other</th>
      <th>Question Text</th>
      <th>Question Iteration</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>564.000000</td>
      <td>586.000000</td>
      <td>586.000000</td>
      <td>423.000000</td>
      <td>202.000000</td>
      <td>0.0</td>
      <td>586.0</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>1296.679078</td>
      <td>46.805461</td>
      <td>44.614334</td>
      <td>6.550827</td>
      <td>3.376238</td>
      <td>NaN</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>std</th>
      <td>1621.268369</td>
      <td>2.422058</td>
      <td>2.906180</td>
      <td>3.701754</td>
      <td>2.692726</td>
      <td>NaN</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>min</th>
      <td>328.000000</td>
      <td>37.000000</td>
      <td>32.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>855.000000</td>
      <td>45.000000</td>
      <td>43.000000</td>
      <td>4.000000</td>
      <td>2.000000</td>
      <td>NaN</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1000.000000</td>
      <td>47.000000</td>
      <td>45.000000</td>
      <td>6.000000</td>
      <td>3.000000</td>
      <td>NaN</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>1500.000000</td>
      <td>48.000000</td>
      <td>46.750000</td>
      <td>8.000000</td>
      <td>4.000000</td>
      <td>NaN</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>max</th>
      <td>36472.000000</td>
      <td>54.000000</td>
      <td>53.000000</td>
      <td>28.000000</td>
      <td>19.000000</td>
      <td>NaN</td>
      <td>1.0</td>
    </tr>
  </tbody>
</table>
</div>




```python

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
      <th>Pollster</th>
      <th>Start Date</th>
      <th>End Date</th>
      <th>Entry Date/Time (ET)</th>
      <th>Number of Observations</th>
      <th>Population</th>
      <th>Mode</th>
      <th>Obama</th>
      <th>Romney</th>
      <th>Undecided</th>
      <th>Other</th>
      <th>Pollster URL</th>
      <th>Source URL</th>
      <th>Partisan</th>
      <th>Affiliation</th>
      <th>Question Text</th>
      <th>Question Iteration</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Politico/GWU/Battleground</td>
      <td>2012-11-04</td>
      <td>2012-11-05</td>
      <td>2012-11-06T08:40:26Z</td>
      <td>1000.0</td>
      <td>Likely Voters</td>
      <td>Live Phone</td>
      <td>47.0</td>
      <td>47.0</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://www.politico.com/news/stories/1112/8338...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>YouGov/Economist</td>
      <td>2012-11-03</td>
      <td>2012-11-05</td>
      <td>2012-11-26T15:31:23Z</td>
      <td>740.0</td>
      <td>Likely Voters</td>
      <td>Internet</td>
      <td>49.0</td>
      <td>47.0</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://cdn.yougov.com/cumulus_uploads/document...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Gravis Marketing</td>
      <td>2012-11-03</td>
      <td>2012-11-05</td>
      <td>2012-11-06T09:22:02Z</td>
      <td>872.0</td>
      <td>Likely Voters</td>
      <td>Automated Phone</td>
      <td>48.0</td>
      <td>48.0</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://www.gravispolls.com/2012/11/gravis-mark...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>IBD/TIPP</td>
      <td>2012-11-03</td>
      <td>2012-11-05</td>
      <td>2012-11-06T08:51:48Z</td>
      <td>712.0</td>
      <td>Likely Voters</td>
      <td>Live Phone</td>
      <td>50.0</td>
      <td>49.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://news.investors.com/special-report/50841...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rasmussen</td>
      <td>2012-11-03</td>
      <td>2012-11-05</td>
      <td>2012-11-06T08:47:50Z</td>
      <td>1500.0</td>
      <td>Likely Voters</td>
      <td>Automated Phone</td>
      <td>48.0</td>
      <td>49.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://www.rasmussenreports.com/public_content...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



Jetzt wo wir unseren DataFrame etwas besser kennen können wir eine erste Visualisierung erzeugen.

**Erstelle mit Seaborn ein `Countplot`, das die Zugehörigkeit (en. Affiliation) der Befrageten darstellt.**


```python
# Dein Code hier
```


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x107d44a58>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/02-Wahlanalyse_Projekt/Markdown/01-Aufgabe_Wahlanalyse_Projekt_12_1.png)
    


Sieht aus, als wären sie relativ neutral eingestellt, mit einer leichten Tendenz zu den Demokraten. Das im Hinterkopf zu behalten wird uns bei den weiteren Analysen helfen. Schauen wir, ob uns die Bevölkerung (en. Population) mehr Einblicke verschafft.

**Erzeuge das gleiche Diagramm erneut. Verwende dieses Mal die "Population" als `hue`.**


```python
# Dein Code hier
```


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x107f69278>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/02-Wahlanalyse_Projekt/Markdown/01-Aufgabe_Wahlanalyse_Projekt_15_1.png)
    


Sieht aus als wären viele wahrscheinliche Wähler (en. likely voters) und registrierte Wähler (en. registered voters) inbegriffen. Das bedeutet hoffentlich, dass unsere Umfragedaten eine gute Repräsentation der befragten Bevölerung darstellt. Schauen wir uns noch einmal kurz den DataFrame an.

**Gib den Head des DataFrames aus.**


```python

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
      <th>Pollster</th>
      <th>Start Date</th>
      <th>End Date</th>
      <th>Entry Date/Time (ET)</th>
      <th>Number of Observations</th>
      <th>Population</th>
      <th>Mode</th>
      <th>Obama</th>
      <th>Romney</th>
      <th>Undecided</th>
      <th>Other</th>
      <th>Pollster URL</th>
      <th>Source URL</th>
      <th>Partisan</th>
      <th>Affiliation</th>
      <th>Question Text</th>
      <th>Question Iteration</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Politico/GWU/Battleground</td>
      <td>2012-11-04</td>
      <td>2012-11-05</td>
      <td>2012-11-06T08:40:26Z</td>
      <td>1000.0</td>
      <td>Likely Voters</td>
      <td>Live Phone</td>
      <td>47.0</td>
      <td>47.0</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://www.politico.com/news/stories/1112/8338...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>YouGov/Economist</td>
      <td>2012-11-03</td>
      <td>2012-11-05</td>
      <td>2012-11-26T15:31:23Z</td>
      <td>740.0</td>
      <td>Likely Voters</td>
      <td>Internet</td>
      <td>49.0</td>
      <td>47.0</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://cdn.yougov.com/cumulus_uploads/document...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Gravis Marketing</td>
      <td>2012-11-03</td>
      <td>2012-11-05</td>
      <td>2012-11-06T09:22:02Z</td>
      <td>872.0</td>
      <td>Likely Voters</td>
      <td>Automated Phone</td>
      <td>48.0</td>
      <td>48.0</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://www.gravispolls.com/2012/11/gravis-mark...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>IBD/TIPP</td>
      <td>2012-11-03</td>
      <td>2012-11-05</td>
      <td>2012-11-06T08:51:48Z</td>
      <td>712.0</td>
      <td>Likely Voters</td>
      <td>Live Phone</td>
      <td>50.0</td>
      <td>49.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://news.investors.com/special-report/50841...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rasmussen</td>
      <td>2012-11-03</td>
      <td>2012-11-05</td>
      <td>2012-11-06T08:47:50Z</td>
      <td>1500.0</td>
      <td>Likely Voters</td>
      <td>Automated Phone</td>
      <td>48.0</td>
      <td>49.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://www.rasmussenreports.com/public_content...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



Fahren wir damit fort, uns die Durchschnitte für Obama und Romeny anzuschauen. Außerdem schließen wir die Befragten mit ein, die unentschlossen sind. 

**Erstelle einen DataFrame namens "avg" (dt. Durchschnitt), der für die Daten aus "poll_df" den Durchschnitt beinhaltet. Schließe danach "Number of Observations" (*Hinweis:* `axis=0`) aus.**


```python

```

**Erstelle einen DataFrame namens "std" (dt. Standardabweichung), der für die Daten aus "poll_df" die Standardabweichung beinhaltet. Schließe danach "Number of Observations" (*Hinweis:* `axis=0`) aus.**


```python

```

**Nutze Pandas, um das folgende Balkendiagramm darzusellen.**


```python
# Dein Code hier
```


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x10d0e88d0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/02-Wahlanalyse_Projekt/Markdown/01-Aufgabe_Wahlanalyse_Projekt_24_1.png)
    


Interessant wie eng die Umfrage zu sein scheint. Insbesondere unter Berücksichtigung des "Unentschlossenheit"-Faktors (en. undecided). Schauen wir uns die Zahlen an.

**Erstelle einen DataFrame namens "poll_avg". Dieser soll sowohl "avg" als auch "std" beinhalten.**


```python

```

**Benennen die Spalten dieses neuen DataFrames in "Average" und "STD" um.**


```python

```

**Zeige den neuen DataFrame an.**


```python

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
      <th>Average</th>
      <th>STD</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Obama</th>
      <td>46.805461</td>
      <td>2.422058</td>
    </tr>
    <tr>
      <th>Romney</th>
      <td>44.614334</td>
      <td>2.906180</td>
    </tr>
    <tr>
      <th>Undecided</th>
      <td>6.550827</td>
      <td>3.701754</td>
    </tr>
    <tr>
      <th>Other</th>
      <td>3.376238</td>
      <td>2.692726</td>
    </tr>
    <tr>
      <th>Question Text</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Question Iteration</th>
      <td>1.000000</td>
      <td>0.000000</td>
    </tr>
  </tbody>
</table>
</div>



Sieht aus als ob die verschiedenen Umfragen es als ziemlich knappes Rennen einstufen. Was ist mit den unentschlossenen Wählern? Die meisten davon werden sich entscheiden, sobald die Wahl stattfindet. Wenn wir annehmen, dass wir die unentschlossenen Wähler gleich auf Romeny und Obama verteilen können, dann sollte das ein nahezu unverfälschtes Ergebniss der finalen Differenz ergeben.

**Schau dir erneut den DataFrame `poll_df` mit `head()` an.**


```python

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
      <th>Pollster</th>
      <th>Start Date</th>
      <th>End Date</th>
      <th>Entry Date/Time (ET)</th>
      <th>Number of Observations</th>
      <th>Population</th>
      <th>Mode</th>
      <th>Obama</th>
      <th>Romney</th>
      <th>Undecided</th>
      <th>Other</th>
      <th>Pollster URL</th>
      <th>Source URL</th>
      <th>Partisan</th>
      <th>Affiliation</th>
      <th>Question Text</th>
      <th>Question Iteration</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Politico/GWU/Battleground</td>
      <td>2012-11-04</td>
      <td>2012-11-05</td>
      <td>2012-11-06T08:40:26Z</td>
      <td>1000.0</td>
      <td>Likely Voters</td>
      <td>Live Phone</td>
      <td>47.0</td>
      <td>47.0</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://www.politico.com/news/stories/1112/8338...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>YouGov/Economist</td>
      <td>2012-11-03</td>
      <td>2012-11-05</td>
      <td>2012-11-26T15:31:23Z</td>
      <td>740.0</td>
      <td>Likely Voters</td>
      <td>Internet</td>
      <td>49.0</td>
      <td>47.0</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://cdn.yougov.com/cumulus_uploads/document...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Gravis Marketing</td>
      <td>2012-11-03</td>
      <td>2012-11-05</td>
      <td>2012-11-06T09:22:02Z</td>
      <td>872.0</td>
      <td>Likely Voters</td>
      <td>Automated Phone</td>
      <td>48.0</td>
      <td>48.0</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://www.gravispolls.com/2012/11/gravis-mark...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>IBD/TIPP</td>
      <td>2012-11-03</td>
      <td>2012-11-05</td>
      <td>2012-11-06T08:51:48Z</td>
      <td>712.0</td>
      <td>Likely Voters</td>
      <td>Live Phone</td>
      <td>50.0</td>
      <td>49.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://news.investors.com/special-report/50841...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rasmussen</td>
      <td>2012-11-03</td>
      <td>2012-11-05</td>
      <td>2012-11-06T08:47:50Z</td>
      <td>1500.0</td>
      <td>Likely Voters</td>
      <td>Automated Phone</td>
      <td>48.0</td>
      <td>49.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://www.rasmussenreports.com/public_content...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



Wenn wir wollten könnten wir auch eine kurze Zeitreihen Analyse machen. Diese wird recht einfach und schnell sein! Das Ziel ist es, die Verteilung im Zeitverlauf zu betrachten. 

**Erzeuge mit Matplotlib ein Diagramm mit "End Date" auf der x- und `['Obama','Romney','Undecided']` auf der y-Achse.**

*Hinweis: Die Enddaten werden in umgekehrter chronologischer Reihenfolge angezeigt werden.*


```python
# Dein Code hier
```


```python

```

    /Users/davidmika/anaconda3/lib/python3.5/site-packages/pandas/plotting/_core.py:1714: UserWarning: Pandas doesn't allow columns to be created via a new attribute name - see https://pandas.pydata.org/pandas-docs/stable/indexing.html#attribute-access
      series.name = label





    <matplotlib.axes._subplots.AxesSubplot at 0x10d1acfd0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/02-Wahlanalyse_Projekt/Markdown/01-Aufgabe_Wahlanalyse_Projekt_35_2.png)
    


Das gibt uns einen sehr groben Überblick, allerdings ist es auch schwer zu lesen.

Um die Daten etwas besser zu verstehen erzeugen wir eine weitere Visualisierung. Dafür werden wir zunächst einige weitere Fragen beantworten. Als Ziel wollen wir die Differenz zwischen Obama und Romney im Zetverlauf darstellen. `Datetime` wird uns dabei eine hilfe sein.

**Importiere `datetime` aus `datetime`.**


```python

```

Jetzt werden wir in unserem "poll_df" DataFrame eine neue Spalte hinzufügen, die die Differenz zwischen Romney und Obama in den Umfragen festhält.

**Erzeuge die die Differenz zwischen Obama's und Romney's Ergebnissen und teile diese durch 100. Das Ergebnis soll in einer neuen Spalte namens "Differenz" (dt. Differenz) stehen.**


```python

```

**Schau dir das Ergebnis des letzten Schritts mit `head()` an.**


```python

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
      <th>Pollster</th>
      <th>Start Date</th>
      <th>End Date</th>
      <th>Entry Date/Time (ET)</th>
      <th>Number of Observations</th>
      <th>Population</th>
      <th>Mode</th>
      <th>Obama</th>
      <th>Romney</th>
      <th>Undecided</th>
      <th>Other</th>
      <th>Pollster URL</th>
      <th>Source URL</th>
      <th>Partisan</th>
      <th>Affiliation</th>
      <th>Question Text</th>
      <th>Question Iteration</th>
      <th>Difference</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Politico/GWU/Battleground</td>
      <td>2012-11-04</td>
      <td>2012-11-05</td>
      <td>2012-11-06T08:40:26Z</td>
      <td>1000.0</td>
      <td>Likely Voters</td>
      <td>Live Phone</td>
      <td>47.0</td>
      <td>47.0</td>
      <td>6.0</td>
      <td>NaN</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://www.politico.com/news/stories/1112/8338...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>1</th>
      <td>YouGov/Economist</td>
      <td>2012-11-03</td>
      <td>2012-11-05</td>
      <td>2012-11-26T15:31:23Z</td>
      <td>740.0</td>
      <td>Likely Voters</td>
      <td>Internet</td>
      <td>49.0</td>
      <td>47.0</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://cdn.yougov.com/cumulus_uploads/document...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
      <td>0.02</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Gravis Marketing</td>
      <td>2012-11-03</td>
      <td>2012-11-05</td>
      <td>2012-11-06T09:22:02Z</td>
      <td>872.0</td>
      <td>Likely Voters</td>
      <td>Automated Phone</td>
      <td>48.0</td>
      <td>48.0</td>
      <td>4.0</td>
      <td>NaN</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://www.gravispolls.com/2012/11/gravis-mark...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>IBD/TIPP</td>
      <td>2012-11-03</td>
      <td>2012-11-05</td>
      <td>2012-11-06T08:51:48Z</td>
      <td>712.0</td>
      <td>Likely Voters</td>
      <td>Live Phone</td>
      <td>50.0</td>
      <td>49.0</td>
      <td>NaN</td>
      <td>1.0</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://news.investors.com/special-report/50841...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
      <td>0.01</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rasmussen</td>
      <td>2012-11-03</td>
      <td>2012-11-05</td>
      <td>2012-11-06T08:47:50Z</td>
      <td>1500.0</td>
      <td>Likely Voters</td>
      <td>Automated Phone</td>
      <td>48.0</td>
      <td>49.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>http://elections.huffingtonpost.com/pollster/p...</td>
      <td>http://www.rasmussenreports.com/public_content...</td>
      <td>Nonpartisan</td>
      <td>None</td>
      <td>NaN</td>
      <td>1</td>
      <td>-0.01</td>
    </tr>
  </tbody>
</table>
</div>



Toll! Behalte im Kopf, dass die "Difference" Spalte Obama minus Romney betrachtet. Also bedeutet eine positive Differenz, dass Obama in der Umfrage vorne liegt. Und umgekehrt.

Fahren wir damit fort, diese Differenz im Zeitverlauf zu betrachten. Wir werden zuerst alle Umfragen mit dem gleichen Startdatum (Spalte: Start Date) gruppieren.

**Verwende `groupby()`, um die Umfragen nach ihrem "Start Date" zu gruppieren.**

*Hinweis: Du musst dafür einen Durchschnitt berechnen.*


```python

```

**Schau dir das Ergebnis des letzten Schritts mit `head()` an.**


```python

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
      <th>Start Date</th>
      <th>Number of Observations</th>
      <th>Obama</th>
      <th>Romney</th>
      <th>Undecided</th>
      <th>Other</th>
      <th>Question Text</th>
      <th>Question Iteration</th>
      <th>Difference</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2009-03-13</td>
      <td>1403.0</td>
      <td>44.0</td>
      <td>44.0</td>
      <td>12.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1</td>
      <td>0.00</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2009-04-17</td>
      <td>686.0</td>
      <td>50.0</td>
      <td>39.0</td>
      <td>11.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1</td>
      <td>0.11</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2009-05-14</td>
      <td>1000.0</td>
      <td>53.0</td>
      <td>35.0</td>
      <td>12.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1</td>
      <td>0.18</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2009-06-12</td>
      <td>638.0</td>
      <td>48.0</td>
      <td>40.0</td>
      <td>12.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1</td>
      <td>0.08</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2009-07-15</td>
      <td>577.0</td>
      <td>49.0</td>
      <td>40.0</td>
      <td>11.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1</td>
      <td>0.09</td>
    </tr>
  </tbody>
</table>
</div>



Toll! Jetzt können wir daraus ein Diagramm erstellen.

**Erzeuge ein Objekt namens "fig", das ein Diagramm für "Start Date" und "Difference" beinhaltet. Achte dabei außerdem auf den Stil.**


```python

```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/02-Wahlanalyse_Projekt/Markdown/01-Aufgabe_Wahlanalyse_Projekt_47_0.png)
    


Es wäre sehr interessant zu sehen, wann die TV-Debatten waren. Dann könnten wir Vermutungen über deren Einfluss anstellen. 

Die Debatten fanden statt am 3. Oktober, 11. Oktober und 22. Oktober 2012. Lass uns diese Daten als LInien in das Diagramm zeichnen und auf den Monat Oktober zoomen.

Um herauszufinden, wo wir das Limit der x-Achse setzen müssen brauchen wir den Index des Monats Oktober in 2012. Hier siehst du eine einfache for-Schleife, die dir den Index liefert.

*Hinweis: Da dies durch das Datumsformat etwas kompliziert ist haben wir die for-Schleife bereits gegeben. Eine Erklärung dazu findest du in der Video-Lektion.*


```python
row_in = 0
xlimit = []

for date in poll_df['Start Date']:
    if date[0:7] == '2012-10':
        xlimit.append(row_in)
        row_in +=1
    else:
        row_in += 1
        
print(min(xlimit))
print(max(xlimit))
```

    325
    352


Toll! Jetzt wissen wir, wo wir unsere oberen und unteren Limits für die x-Achse setzen müssen. 

**Lege `xlim` für das `fig` Objekt fest.**


```python
# Dein Code hier
```


```python

```


    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/02-Wahlanalyse_Projekt/Markdown/01-Aufgabe_Wahlanalyse_Projekt_52_0.png)
    


**Trage jetzt Linien für die TV-Debatten in das Diagramm ein.**


```python
# Dein Code hier
```


```python

```




    <matplotlib.lines.Line2D at 0x1a1170c668>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/02-Wahlanalyse_Projekt/Markdown/01-Aufgabe_Wahlanalyse_Projekt_55_1.png)
    


Ersteunlicherweise spiegeln die Umfragen einen Einbruch für Obama nach der 2. Debatte wieder. Und das, obwohl er meiner Erinnerung zu folge bei der 1. Debatte wesentlich schlechter abschnitt.

Für all diese Umfragedaten ist es sehr wichtig, dass Geographie eine große Rolle für die Ergebnisse der Umfrage spielt. Man denke nur an die typische verteilung des US-amerikanischen Bundesstaaten zu verschiedenen Parteien.

## Spendendaten

Im zweiten Teil dieses Projekts werden wir uns einen Datensatz zu Spenden im Wahlkampf von 2012 anschauen. Das wird einer der größten Datensätze sein, mit denen wir im Kurs arbeiten. Ihr könnt sie [hier](https://www.dropbox.com/s/l29oppon2veaq4n/Election_Donor_Data.csv?dl=0) downloaden und dann im Verzeichnis der Notebooks speichern. 

Die Fragen, die wir beantworten möchten sind die folgenden:

1. Wie viel wurde gespendet und wie hoch war die durchschnittiche Spende?
2. Wie unterschieden sich die Spenden zwischen den Kandidaten?
3. Wie unterschieden sich die Spenden zwischen Demokraten und Republikanern?
4. Wie ist die Demographie der Spender?
5. Gibt es ein Muster der Spendenbeträge?

**Lade `Election_Donor_Data.csv` mit Pandas in einen DataFrame namens "donor_df".**


```python

```

    /Users/davidmika/anaconda3/lib/python3.5/site-packages/IPython/core/interactiveshell.py:2728: DtypeWarning: Columns (6) have mixed types. Specify dtype option on import or set low_memory=False.
      interactivity=interactivity, compiler=compiler, result=result)


**Schaue dir die `info()`, `describe()` und `head()` zum DataFrame an.**


```python

```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1001731 entries, 0 to 1001730
    Data columns (total 16 columns):
    cmte_id              1001731 non-null object
    cand_id              1001731 non-null object
    cand_nm              1001731 non-null object
    contbr_nm            1001731 non-null object
    contbr_city          1001712 non-null object
    contbr_st            1001727 non-null object
    contbr_zip           1001620 non-null object
    contbr_employer      988002 non-null object
    contbr_occupation    993301 non-null object
    contb_receipt_amt    1001731 non-null float64
    contb_receipt_dt     1001731 non-null object
    receipt_desc         14166 non-null object
    memo_cd              92482 non-null object
    memo_text            97770 non-null object
    form_tp              1001731 non-null object
    file_num             1001731 non-null int64
    dtypes: float64(1), int64(1), object(14)
    memory usage: 122.3+ MB



```python

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
      <th>contb_receipt_amt</th>
      <th>file_num</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1.001731e+06</td>
      <td>1.001731e+06</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2.982352e+02</td>
      <td>7.744948e+05</td>
    </tr>
    <tr>
      <th>std</th>
      <td>3.749667e+03</td>
      <td>1.059822e+04</td>
    </tr>
    <tr>
      <th>min</th>
      <td>-3.080000e+04</td>
      <td>7.235110e+05</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>3.500000e+01</td>
      <td>7.719270e+05</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1.000000e+02</td>
      <td>7.792250e+05</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>2.500000e+02</td>
      <td>7.802340e+05</td>
    </tr>
    <tr>
      <th>max</th>
      <td>2.014491e+06</td>
      <td>7.878030e+05</td>
    </tr>
  </tbody>
</table>
</div>




```python

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
      <th>cmte_id</th>
      <th>cand_id</th>
      <th>cand_nm</th>
      <th>contbr_nm</th>
      <th>contbr_city</th>
      <th>contbr_st</th>
      <th>contbr_zip</th>
      <th>contbr_employer</th>
      <th>contbr_occupation</th>
      <th>contb_receipt_amt</th>
      <th>contb_receipt_dt</th>
      <th>receipt_desc</th>
      <th>memo_cd</th>
      <th>memo_text</th>
      <th>form_tp</th>
      <th>file_num</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>C00410118</td>
      <td>P20002978</td>
      <td>Bachmann, Michelle</td>
      <td>HARVEY, WILLIAM</td>
      <td>MOBILE</td>
      <td>AL</td>
      <td>3.6601e+08</td>
      <td>RETIRED</td>
      <td>RETIRED</td>
      <td>250.0</td>
      <td>20-JUN-11</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>SA17A</td>
      <td>736166</td>
    </tr>
    <tr>
      <th>1</th>
      <td>C00410118</td>
      <td>P20002978</td>
      <td>Bachmann, Michelle</td>
      <td>HARVEY, WILLIAM</td>
      <td>MOBILE</td>
      <td>AL</td>
      <td>3.6601e+08</td>
      <td>RETIRED</td>
      <td>RETIRED</td>
      <td>50.0</td>
      <td>23-JUN-11</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>SA17A</td>
      <td>736166</td>
    </tr>
    <tr>
      <th>2</th>
      <td>C00410118</td>
      <td>P20002978</td>
      <td>Bachmann, Michelle</td>
      <td>SMITH, LANIER</td>
      <td>LANETT</td>
      <td>AL</td>
      <td>3.68633e+08</td>
      <td>INFORMATION REQUESTED</td>
      <td>INFORMATION REQUESTED</td>
      <td>250.0</td>
      <td>05-JUL-11</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>SA17A</td>
      <td>749073</td>
    </tr>
    <tr>
      <th>3</th>
      <td>C00410118</td>
      <td>P20002978</td>
      <td>Bachmann, Michelle</td>
      <td>BLEVINS, DARONDA</td>
      <td>PIGGOTT</td>
      <td>AR</td>
      <td>7.24548e+08</td>
      <td>NONE</td>
      <td>RETIRED</td>
      <td>250.0</td>
      <td>01-AUG-11</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>SA17A</td>
      <td>749073</td>
    </tr>
    <tr>
      <th>4</th>
      <td>C00410118</td>
      <td>P20002978</td>
      <td>Bachmann, Michelle</td>
      <td>WARDENBURG, HAROLD</td>
      <td>HOT SPRINGS NATION</td>
      <td>AR</td>
      <td>7.19016e+08</td>
      <td>NONE</td>
      <td>RETIRED</td>
      <td>300.0</td>
      <td>20-JUN-11</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>SA17A</td>
      <td>736166</td>
    </tr>
  </tbody>
</table>
</div>



Was interessant sein dürfte sind die Spendenbeträge. Verschaffen wir uns einen Überblick:

**Zähle die Erscheinungen der Werte in der Spalte "contb_receipt_amt".**


```python

```




     100.00     178188
     50.00      137584
     25.00      110345
     250.00      91182
     500.00      57984
     2500.00     49005
     35.00       37237
     1000.00     36494
     10.00       33986
     200.00      27813
     20.00       17565
     15.00       16163
     150.00      14600
     75.00       13647
     201.20      11718
     30.00       11381
     300.00      11204
     20.12        9897
     5.00         9024
     40.00        5007
     2000.00      4128
     55.00        3760
     1500.00      3705
     3.00         3383
     60.00        3084
     400.00       3066
    -2500.00      2727
     110.00       2554
     125.00       2520
     19.00        2474
                 ...  
     174.80          1
     7.27            1
     1219.00         1
     1884.88         1
     162.25          1
     218.31          1
     78.62           1
     203.16          1
     53.11           1
     499.66          1
     19.53           1
     188.60          1
     47.10           1
     19.85           1
     28.83           1
     202.59          1
    -5500.00         1
     9.25            1
     202.66          1
     1205.00         1
     80.73           1
     115.07          1
     213.69          1
     70.76           1
     144.13          1
     97.15           1
     122.32          1
     188.65          1
     122.40          1
     132.12          1
    Name: contb_receipt_amt, Length: 8079, dtype: int64



8079 verschiedene Beträge. Eine ziemliche Variation. Untersuchen wir dies genauer:

**Berechne den Durchschnitt der Spenden und speichere ihn in der Variablen "don_mean".**


```python

```

**Berechne die Standardabweichung der Spenden und speichere sie in der Variablen "don_std".**


```python

```

**Gib den unten stehenden Satz aus, indem du die beiden zuletzt erzeugten Variablen in einen String einfügst.**


```python

```

    Die durchschnittliche Spende war 298.24 mit einer Standardabweichung von 3749.67


Wow! Das ist eine riesige Standardabweichung. Wir sollten untersuchen, ob es irgendwelche sehr großen Spenden gab oder welche sonstigen Faktoren da eine Rolle gespielt haben könnten.

**Kopiere die Spalte "contb_receipt_amt" in eine Series namens "top_donor".**


```python

```

**Sortiere die neue Series.**


```python

```

**Zeige die sortierte Series an.**


```python

```




    114604     -30800.00
    226986     -25800.00
    101356      -7500.00
    398429      -5500.00
    250737      -5455.00
    33821       -5414.31
    908565      -5115.00
    456649      -5000.00
    574657      -5000.00
    30513       -5000.00
    562267      -5000.00
    30584       -5000.00
    86268       -5000.00
    708920      -5000.00
    665887      -5000.00
    708899      -5000.00
    708929      -5000.00
    21172       -5000.00
    21168       -5000.00
    21167       -5000.00
    262328      -5000.00
    946875      -5000.00
    7361        -5000.00
    416403      -5000.00
    21164       -5000.00
    707945      -5000.00
    615101      -5000.00
    7973        -5000.00
    54430       -5000.00
    54434       -5000.00
                 ...    
    708022      10000.00
    708898      10000.00
    710177      10000.00
    876244      10000.00
    709608      10000.00
    708919      10000.00
    709739      10000.00
    91145       10000.00
    708138      10000.00
    993178      10000.00
    709813      10000.00
    710730      10000.00
    708928      10000.00
    709268      10000.00
    99829       10000.00
    90076       10000.00
    709859      10000.00
    41888       10000.00
    65131       12700.00
    834301      25000.00
    823345      25000.00
    217891      25800.00
    114754      33300.00
    257270     451726.00
    335187     512710.91
    319478     526246.17
    344419    1511192.17
    344539    1679114.65
    326651    1944042.43
    325136    2014490.51
    Name: contb_receipt_amt, Length: 1001731, dtype: float64



Sieht aus als hätten wir einige negative Beträge als auch riesige Spenden! Die negativen Einträge kommen daher, dass die FEC (zuständige Behörde) auch die Erstattungen notiert. Fahren wir fort und betrachten nur die positiven Beträge.

**Aktuallisiere die "top_donor" Series und behalte nur die positiven Werte.**


```python

```

**Sortiere die neue Series.**


```python

```




    334504          0.01
    321779          0.01
    323547          0.01
    325614          0.01
    326100          0.01
    325982          0.01
    318560          0.01
    325986          0.01
    325429          0.01
    323822          0.01
    348154          0.01
    329984          0.01
    320749          0.01
    320784          0.01
    326053          0.01
    325758          0.01
    317753          0.01
    325344          0.01
    323661          0.01
    319373          0.01
    321025          0.01
    326172          0.01
    336020          0.01
    335424          0.01
    345103          0.01
    323823          0.01
    320309          0.01
    325975          0.01
    325973          0.01
    321676          0.01
                 ...    
    99829       10000.00
    709268      10000.00
    708928      10000.00
    710730      10000.00
    709813      10000.00
    41888       10000.00
    708138      10000.00
    923476      10000.00
    709739      10000.00
    708919      10000.00
    709608      10000.00
    876244      10000.00
    710177      10000.00
    708898      10000.00
    708022      10000.00
    711167      10000.00
    710198      10000.00
    91145       10000.00
    65131       12700.00
    834301      25000.00
    823345      25000.00
    217891      25800.00
    114754      33300.00
    257270     451726.00
    335187     512710.91
    319478     526246.17
    344419    1511192.17
    344539    1679114.65
    326651    1944042.43
    325136    2014490.51
    Name: contb_receipt_amt, Length: 991475, dtype: float64



**Schaue dir die 10 häufigsten Spendenbeträge an.**


```python

```




    100.0     178188
    50.0      137584
    25.0      110345
    250.0      91182
    500.0      57984
    2500.0     49005
    35.0       37237
    1000.0     36494
    10.0       33986
    200.0      27813
    Name: contb_receipt_amt, dtype: int64



Wir sehen, dass die 10 häufigsten Spendenbeträge zwischen 10 und 2500 Dollar liegen. 

Wir können relativ schnell überprüfen, ob üblicherweise Spenden von runder Summe (10, 20, 50, usw.) gemacht werden. Dazu können wir ein Histogramm erstellen und nach Ausschlägen bei diesen Werten schauen.

**Erstelle eine neuee Series "com_don", die die Spenden unter 2500 Dollar beinhaltet.**


```python

```

**Erstelle ein Histogramm der neuen Series und setze `bins=100`.**


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x1a11940d68>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/02-Wahlanalyse_Projekt/Markdown/01-Aufgabe_Wahlanalyse_Projekt_85_1.png)
    


Sieht aus, als ob unsere Intuition korrekt war: Die Ausschläge sind insbesondere bei den runden Summen. 

Tauchen wir etwas tiefer ein und teilen Spenden nach den Parteien auf. Um dies zu tun müssen wir einen Weg finden, um eine neue "Party" (dt. Partei) Spalte zu erzeugen. Wir könenn dazu die Kandidaten nutzen und dann ihre Parteizugehörigkeit verwenden.

**Zeige die uniquen Kandidaten an und speichere sie in der "candidates" Variablen.**


```python

```




    array(['Bachmann, Michelle', 'Romney, Mitt', 'Obama, Barack',
           "Roemer, Charles E. 'Buddy' III", 'Pawlenty, Timothy',
           'Johnson, Gary Earl', 'Paul, Ron', 'Santorum, Rick', 'Cain, Herman',
           'Gingrich, Newt', 'McCotter, Thaddeus G', 'Huntsman, Jon',
           'Perry, Rick'], dtype=object)



Die Zugehörigkeit der Kandidaten zu den Parteien sei gegeben:


```python
party_map = {'Bachmann, Michelle': 'Republican',
           'Cain, Herman': 'Republican',
           'Gingrich, Newt': 'Republican',
           'Huntsman, Jon': 'Republican',
           'Johnson, Gary Earl': 'Republican',
           'McCotter, Thaddeus G': 'Republican',
           'Obama, Barack': 'Democrat',
           'Paul, Ron': 'Republican',
           'Pawlenty, Timothy': 'Republican',
           'Perry, Rick': 'Republican',
           "Roemer, Charles E. 'Buddy' III": 'Republican',
           'Romney, Mitt': 'Republican',
           'Santorum, Rick': 'Republican'}
```

**Verwende `map`, um eine neue Spalte "Party" im "donor_df" DataFrame zu erzeugen, die dem Kandidaten die passende Partei zuweiset.**


```python

```

Lasst uns sicher gehen, dass die negativen Beträge aus dem DataFrame ausgeschlossen werden.

**Bereinige den DataFrame um die negativen Spenden.**


```python

```

**Schaue dir den aktuallisierten DataFrame an.**


```python

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
      <th>cmte_id</th>
      <th>cand_id</th>
      <th>cand_nm</th>
      <th>contbr_nm</th>
      <th>contbr_city</th>
      <th>contbr_st</th>
      <th>contbr_zip</th>
      <th>contbr_employer</th>
      <th>contbr_occupation</th>
      <th>contb_receipt_amt</th>
      <th>contb_receipt_dt</th>
      <th>receipt_desc</th>
      <th>memo_cd</th>
      <th>memo_text</th>
      <th>form_tp</th>
      <th>file_num</th>
      <th>Party</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>C00410118</td>
      <td>P20002978</td>
      <td>Bachmann, Michelle</td>
      <td>HARVEY, WILLIAM</td>
      <td>MOBILE</td>
      <td>AL</td>
      <td>3.6601e+08</td>
      <td>RETIRED</td>
      <td>RETIRED</td>
      <td>250.0</td>
      <td>20-JUN-11</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>SA17A</td>
      <td>736166</td>
      <td>Republican</td>
    </tr>
    <tr>
      <th>1</th>
      <td>C00410118</td>
      <td>P20002978</td>
      <td>Bachmann, Michelle</td>
      <td>HARVEY, WILLIAM</td>
      <td>MOBILE</td>
      <td>AL</td>
      <td>3.6601e+08</td>
      <td>RETIRED</td>
      <td>RETIRED</td>
      <td>50.0</td>
      <td>23-JUN-11</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>SA17A</td>
      <td>736166</td>
      <td>Republican</td>
    </tr>
    <tr>
      <th>2</th>
      <td>C00410118</td>
      <td>P20002978</td>
      <td>Bachmann, Michelle</td>
      <td>SMITH, LANIER</td>
      <td>LANETT</td>
      <td>AL</td>
      <td>3.68633e+08</td>
      <td>INFORMATION REQUESTED</td>
      <td>INFORMATION REQUESTED</td>
      <td>250.0</td>
      <td>05-JUL-11</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>SA17A</td>
      <td>749073</td>
      <td>Republican</td>
    </tr>
    <tr>
      <th>3</th>
      <td>C00410118</td>
      <td>P20002978</td>
      <td>Bachmann, Michelle</td>
      <td>BLEVINS, DARONDA</td>
      <td>PIGGOTT</td>
      <td>AR</td>
      <td>7.24548e+08</td>
      <td>NONE</td>
      <td>RETIRED</td>
      <td>250.0</td>
      <td>01-AUG-11</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>SA17A</td>
      <td>749073</td>
      <td>Republican</td>
    </tr>
    <tr>
      <th>4</th>
      <td>C00410118</td>
      <td>P20002978</td>
      <td>Bachmann, Michelle</td>
      <td>WARDENBURG, HAROLD</td>
      <td>HOT SPRINGS NATION</td>
      <td>AR</td>
      <td>7.19016e+08</td>
      <td>NONE</td>
      <td>RETIRED</td>
      <td>300.0</td>
      <td>20-JUN-11</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>SA17A</td>
      <td>736166</td>
      <td>Republican</td>
    </tr>
  </tbody>
</table>
</div>



Fahren wir damit fort, die Daten nach Kandidaten aggregieren. Wir schauen uns schnell an, wie viel jeder Kandidat erhalten hat.

**Zeige die Anzahl der Spenden an, die jeder Kandidat erhalten hat.**


```python

```




    cand_nm
    Bachmann, Michelle                 13082
    Cain, Herman                       20052
    Gingrich, Newt                     46883
    Huntsman, Jon                       4066
    Johnson, Gary Earl                  1234
    McCotter, Thaddeus G                  73
    Obama, Barack                     589127
    Paul, Ron                         143161
    Pawlenty, Timothy                   3844
    Perry, Rick                        12709
    Roemer, Charles E. 'Buddy' III      5844
    Romney, Mitt                      105155
    Santorum, Rick                     46245
    Name: contb_receipt_amt, dtype: int64



Ok, offensichtich hat Obama die meisten Spenden erhalten. Das ergibt Sinn, da er nicht mit anderen demokratischen Kandidaten um die Spenden konkuriert. Schauen wir uns nun die Summe der Spenden an:

**Zeige die Summe der Spenden an, die jeder Kandidat erhalten hat.**


```python

```




    cand_nm
    Bachmann, Michelle                2.711439e+06
    Cain, Herman                      7.101082e+06
    Gingrich, Newt                    1.283277e+07
    Huntsman, Jon                     3.330373e+06
    Johnson, Gary Earl                5.669616e+05
    McCotter, Thaddeus G              3.903000e+04
    Obama, Barack                     1.358774e+08
    Paul, Ron                         2.100962e+07
    Pawlenty, Timothy                 6.004819e+06
    Perry, Rick                       2.030575e+07
    Roemer, Charles E. 'Buddy' III    3.730099e+05
    Romney, Mitt                      8.833591e+07
    Santorum, Rick                    1.104316e+07
    Name: contb_receipt_amt, dtype: float64



Das ist nicht gut lesbar, wir sollten es bearbeiten. Zu den wichtigen Aspekten von Data Science gehört es auch, Informationen verständlich zu präsentieren. Deshalb sollten wir diese Werte mit einem for-Loop und vollständigen Setzen ausgeben.

**Erstelle eine for-Schleife, um für jeden Kandidaten die untenstehenden Sätze zu erzeugen.**


```python

```

     Der/Die Kandidat(in) Bachmann, Michelle sammelte 2711439 dollar ein.
    
    
     Der/Die Kandidat(in) Cain, Herman sammelte 7101082 dollar ein.
    
    
     Der/Die Kandidat(in) Gingrich, Newt sammelte 12832770 dollar ein.
    
    
     Der/Die Kandidat(in) Huntsman, Jon sammelte 3330373 dollar ein.
    
    
     Der/Die Kandidat(in) Johnson, Gary Earl sammelte 566962 dollar ein.
    
    
     Der/Die Kandidat(in) McCotter, Thaddeus G sammelte 39030 dollar ein.
    
    
     Der/Die Kandidat(in) Obama, Barack sammelte 135877427 dollar ein.
    
    
     Der/Die Kandidat(in) Paul, Ron sammelte 21009620 dollar ein.
    
    
     Der/Die Kandidat(in) Pawlenty, Timothy sammelte 6004819 dollar ein.
    
    
     Der/Die Kandidat(in) Perry, Rick sammelte 20305754 dollar ein.
    
    
     Der/Die Kandidat(in) Roemer, Charles E. 'Buddy' III sammelte 373010 dollar ein.
    
    
     Der/Die Kandidat(in) Romney, Mitt sammelte 88335908 dollar ein.
    
    
     Der/Die Kandidat(in) Santorum, Rick sammelte 11043159 dollar ein.
    
    


Das ist zwar verständlich, aber noch immer nicht gut vergleichbar.

**Erstelle ein Balkendiagramm der summierten Spenden pro Kandidaten.**


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x1a11f6b898>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/02-Wahlanalyse_Projekt/Markdown/01-Aufgabe_Wahlanalyse_Projekt_103_1.png)
    


Jetzt ist der Vergleich relativ leicht zu ziehen. Wie wir vorher gesehen haben ist Obama der größte Spendenempfänger. Die ergibt Sinn, da es keine anderen demokratischen Kandidaten gibt. Wie wäre es, wenn wir nur Demokraten und Republikaner vergleichen?

**Erstelle ein Balkendiagramm der Spenden pro Partei.**


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x1a1426fd30>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/02-Wahlanalyse_Projekt/Markdown/01-Aufgabe_Wahlanalyse_Projekt_105_1.png)
    


Sieht aus als könnte Obama mit der Gesamtheit der Republikaner nicht mithalten. Aber er hat ganz klar den Vorteil, dass ihre Spenden sich auf viele Kandidaten aufteilen.

Zu guter Letzt, um das Projekt zum Ende zu bringen, möchten wir uns noch die Spenden anschauen und insbesondere, von wem sie kamen. Wir werden die "contr_occupation" (dt. Spender Beruf) Information aus dem donor_df DataFrame nutzen. 

**Verwende `pivot_table`, um für jeden Beruf die summierte Spende pro Partei anzuzeigen. Speichere dein Ergebnis in einen neuen "occupation_df" DataFrame.**


```python

```

**Zeige den neuen DataFrame an.**


```python

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
      <th>Party</th>
      <th>Democrat</th>
      <th>Republican</th>
    </tr>
    <tr>
      <th>contbr_occupation</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>MIXED-MEDIA ARTIST / STORYTELLER</th>
      <td>100.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>AREA VICE PRESIDENT</th>
      <td>250.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>RESEARCH ASSOCIATE</th>
      <td>100.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>TEACHER</th>
      <td>500.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>THERAPIST</th>
      <td>3900.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



Toll! Jetzt sollten wir überprüfen, wie groß dieser DataFrame ist.

**Finde heraus, wie groß der DataFrame ist.**


```python

```




    (45067, 2)



Wow! Das sind sehr viele. Leider zu viele, um sie in einem statischen Diagramm effektiv darzustellen. Wir sollten eine Grenze ziehen, und Einzelbeträge unter dieser ausschließen. Viele kleine 20 Dollar Spenden einer Berufsgruppe sind für uns nicht so interessant, wie die großen Geldgeber. Wir wählen als Grenzwert für die summierten Spenden eines Berufs $1.000.000.

**Aktuallisiere den "occupation_df" DataFrame und behalte nur summierte Spenden von mehr als 1 Mio. Dollar.**


```python

```

**Finde heraus, wie groß der aktuallisierte DataFrame ist.**


```python

```




    (31, 2)



Gut! Das sieht wesentlich "umgänglicher" aus. Wir können es jetzt visualisieren.

**Erstelle ein Balkendiagramm für die summierten Spenden pro Berufsgruppe für den aktuallisierten DataFrame.**


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x1a11522278>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/02-Wahlanalyse_Projekt/Markdown/01-Aufgabe_Wahlanalyse_Projekt_117_1.png)
    


Immer noch etwas schwer zu lesen. Lasst uns `barh` verwenden, um das ganze horizontal auszurichten.

**Erzeuge das gleiche Diagramm. Wähle diesesmal eine horizontale Darstellung.**


```python
# Dein Code hier
```


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x1a11e85c50>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/02-Wahlanalyse_Projekt/Markdown/01-Aufgabe_Wahlanalyse_Projekt_120_1.png)
    


Sieht aus, als wären manche Berufe falsch beschriftet. Außerdem können wir CEO und C.E.O. kombinieren.

**Schließe "INFORMATION REQUESTED PER BEST EFFORTS" aus dem DataFrame aus.**


```python

```

**Aktuallisiere die Einträge für CEO durch die Summe aus CEO und C.E.O. Anschließend entferne den Eintrag für C.E.O. aus dem DataFrame.**


```python

```

**Erzeuge nun erneut das horizontale Balkendiagramm.**


```python
# Dein Code hier
```


```python

```




    <matplotlib.axes._subplots.AxesSubplot at 0x1a1228fcc0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/02-Wahlanalyse_Projekt/Markdown/01-Aufgabe_Wahlanalyse_Projekt_127_1.png)
    


Toll! Sieht aus gut aus.

Es gibt noch so viel in diesem Datensatz zu analysieren. Werde kreativ, denke über die politischen Faktoren nach und stelle eigene Fragen auf. Diese kannst du versuchen mit Python zu beantworten. Natürlich komplett freiwillig und optional.

# Gut gemacht!

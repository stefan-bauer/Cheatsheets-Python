<a href="https://www.datamics.com/courses/online-courses/">![title](bg_datamics_top.png)</a>

<center><em>© Datamics</em></center><br><center><em>Besuche uns für mehr Informationen auf <a href='https://www.datamics.com/courses/online-courses/'>www.datamics.com</a></em>
# Titanic Projekt - Lösung

Wilkommen zum Titanic Projekt. Wir werden Daten von [Kaggle](Titanic Projekt - Lösungen) analysieren. Du findest sie als "`titanic.csv` Datei im selben Verzeichnis wie dieses Notebook. 

Wir werden

# noch ausformulieren

Legen wir gleich los!

**Importiere Pandas. Und zusätzlich aus Pandas speziell "Series" und "DataFrame".**


```python
import pandas as pd
from pandas import Series, DataFrame
```

**Lade die `titanic.csv` mit `read_csv` in einen DataFrame namens "titanic_df".**


```python
titanic_df = pd.read_csv("titanic.csv")
```

**Schaue dir den `head` des DataFrame an.**


```python
titanic_df.head()
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
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1</td>
      <td>1</td>
      <td>Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>113803</td>
      <td>53.1000</td>
      <td>C123</td>
      <td>S</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>0</td>
      <td>3</td>
      <td>Allen, Mr. William Henry</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>373450</td>
      <td>8.0500</td>
      <td>NaN</td>
      <td>S</td>
    </tr>
  </tbody>
</table>
</div>



**Verwende `info()` auf den DataFrame.**


```python
titanic_df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 891 entries, 0 to 890
    Data columns (total 12 columns):
    PassengerId    891 non-null int64
    Survived       891 non-null int64
    Pclass         891 non-null int64
    Name           891 non-null object
    Sex            891 non-null object
    Age            714 non-null float64
    SibSp          891 non-null int64
    Parch          891 non-null int64
    Ticket         891 non-null object
    Fare           891 non-null float64
    Cabin          204 non-null object
    Embarked       889 non-null object
    dtypes: float64(2), int64(5), object(5)
    memory usage: 83.6+ KB


**Verwende `describe()` auf den DataFrame.**


```python
titanic_df.describe()
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
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Fare</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>891.000000</td>
      <td>891.000000</td>
      <td>891.000000</td>
      <td>714.000000</td>
      <td>891.000000</td>
      <td>891.000000</td>
      <td>891.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>446.000000</td>
      <td>0.383838</td>
      <td>2.308642</td>
      <td>29.699118</td>
      <td>0.523008</td>
      <td>0.381594</td>
      <td>32.204208</td>
    </tr>
    <tr>
      <th>std</th>
      <td>257.353842</td>
      <td>0.486592</td>
      <td>0.836071</td>
      <td>14.526497</td>
      <td>1.102743</td>
      <td>0.806057</td>
      <td>49.693429</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>0.420000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>223.500000</td>
      <td>0.000000</td>
      <td>2.000000</td>
      <td>20.125000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>7.910400</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>446.000000</td>
      <td>0.000000</td>
      <td>3.000000</td>
      <td>28.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>14.454200</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>668.500000</td>
      <td>1.000000</td>
      <td>3.000000</td>
      <td>38.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>31.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>891.000000</td>
      <td>1.000000</td>
      <td>3.000000</td>
      <td>80.000000</td>
      <td>8.000000</td>
      <td>6.000000</td>
      <td>512.329200</td>
    </tr>
  </tbody>
</table>
</div>



Alle guten Analyse Prohekte beginnen mit einer Fragestellung. Jetzt wo wir wissen, wie unser DataFrame strukturell aussieht, können wir uns einige solcher Fragen überlegen. Was ist es, das wir erfahren möchten? Hier ist eine Liste an Fragen, die wir versuchen werden zu beantworten. Dazu nutzen wir natürlich unsere neu gelernten Analyse Fähigkeiten!

Einige grundlegende Fragen:

1. Wer waren die Passagiere auf der Titanic (Alter, Geschlecht, Klasse, etc.)?
2. Auf welchem Deck befanden sie sich und wie hängt das mit ihrere Klasse zusammen?
3. Woher kamen die Passagiere?
4. Wer war alleine an Board und wer mit seiner Familie?

Dann können wir noch versuchen herauszufinden, welche Faktoren beim Überleben geholfen haben:

5. Welche Faktoren halfen Passagieren dabei zu überleben?

Also beginnen wir mit unserer ersten Frage: Wer waren die Passagiere auf der Titanic?

**Importiere numpy, matplotlib, seaborn und setzte matplotlib inline.**


```python
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline
```

**Nutze Seaborn, um das Geschlecht (en. Sex) in einem countplot darzustellen.**


```python
# Dein Code hier
```


```python
sns.countplot('Sex',data=titanic_df)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1a19671cc0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_14_1.png)
    


**Untersuche jetzt die Klassen (Spalte: Pclass) und trenne dabei nach Geschlecht (en. Sex).**


```python
# Dein Code hier
```


```python
sns.countplot('Pclass',data=titanic_df,hue='Sex')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1a1969db70>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_17_1.png)
    


Wow, da sind deutlich mehr Männder als Frauen in der 3. Klasse. Eine interessante Erkenntnis. Nichtsdestotrotz könnte es nützlich sein darüberhinaus auch Kinder von Männern und Frauen zu Unterscheiden.

Wie können wir dafür vorgehen? Wir können jeden unter 16 Jahren als "child" (dt. Kind) einteilen. 

**Erstelle eine Funktion die folgendes tut: 1. Lese einen Passagier ein. 2. Rufe sein Alter und Geschlecht ab. 3. Wenn das Alter niedriger als 16 ist dann gebe "child" (dt. Kind) zurück. 4. Ansonsten gebe das Geschlecht (Spalte: sex) zurück.**

*Hinweis: Diese Funktion soll anschließend mit `apply()` angewendet werden.*


```python
def male_female_child(passenger):
    age, sex = passenger
    if age < 16:
        return "child"
    else:
        return sex
```

**Wende deine Funktion von ebene mit `apply` an, um eine neue Spalte namens "person" zum DataFrame hinzuzufügen.**


```python
titanic_df['person'] = titanic_df[['Age','Sex']].apply(male_female_child,axis=1)
```

**Überprüfe deinen letzten Arbeitsschnitt mit `head()` für die ersten 10 Einträge.**


```python
titanic_df.head(10)
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
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
      <th>person</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
      <td>male</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
      <td>female</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
      <td>female</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1</td>
      <td>1</td>
      <td>Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>113803</td>
      <td>53.1000</td>
      <td>C123</td>
      <td>S</td>
      <td>female</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>0</td>
      <td>3</td>
      <td>Allen, Mr. William Henry</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>373450</td>
      <td>8.0500</td>
      <td>NaN</td>
      <td>S</td>
      <td>male</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>0</td>
      <td>3</td>
      <td>Moran, Mr. James</td>
      <td>male</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>330877</td>
      <td>8.4583</td>
      <td>NaN</td>
      <td>Q</td>
      <td>male</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>0</td>
      <td>1</td>
      <td>McCarthy, Mr. Timothy J</td>
      <td>male</td>
      <td>54.0</td>
      <td>0</td>
      <td>0</td>
      <td>17463</td>
      <td>51.8625</td>
      <td>E46</td>
      <td>S</td>
      <td>male</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8</td>
      <td>0</td>
      <td>3</td>
      <td>Palsson, Master. Gosta Leonard</td>
      <td>male</td>
      <td>2.0</td>
      <td>3</td>
      <td>1</td>
      <td>349909</td>
      <td>21.0750</td>
      <td>NaN</td>
      <td>S</td>
      <td>child</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9</td>
      <td>1</td>
      <td>3</td>
      <td>Johnson, Mrs. Oscar W (Elisabeth Vilhelmina Berg)</td>
      <td>female</td>
      <td>27.0</td>
      <td>0</td>
      <td>2</td>
      <td>347742</td>
      <td>11.1333</td>
      <td>NaN</td>
      <td>S</td>
      <td>female</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10</td>
      <td>1</td>
      <td>2</td>
      <td>Nasser, Mrs. Nicholas (Adele Achem)</td>
      <td>female</td>
      <td>14.0</td>
      <td>1</td>
      <td>0</td>
      <td>237736</td>
      <td>30.0708</td>
      <td>NaN</td>
      <td>C</td>
      <td>child</td>
    </tr>
  </tbody>
</table>
</div>



Großartig! Jetzt haben wir die Passagiere in Frauen, Männer und Kinder unterteilt. Das könnte später wichtig sein, wenn wir uns der "Kinder und Frauen zuerst!" Regelung widmen.

**Erstelle erneut ein countplot für die Klassen und trenne nach "person".**


```python
# Dein Code hier
```


```python
sns.countplot('Pclass',data=titanic_df,hue='person')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x10dfbe710>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_26_1.png)
    


Interessant. Es gab einige Kinder in der 3. Klasse, dafür kaum Kinder in der 1. Klasse. Als nächstes könnten wir uns die Altersverteilung der Passagiere anschauen, um ein besseres Verständnis für sie zu erhalten.

**Erstelle mit Pandas ein Histogram für Age (dt. Alter) und verwende 70 bins.**


```python
# Dein Code hier
```


```python
titanic_df['Age'].hist(bins=70)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x10efe52e8>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_29_1.png)
    


**Schaue dir nun noch an, wie viele "male", "female" und "child" Werte wir in der person Spalte haben.**


```python
titanic_df['person'].value_counts()
```




    male      537
    female    271
    child      83
    Name: person, dtype: int64



Eine weitere Möglichkeit die Daten zu visualisieren ist es mehrere Plots in einem FacetGrid unterzubringen.

**Baue die zu sehende Visualisierung nach. Verwende gerne die Tipps dazu:**

1. Die Quelle ist titanic_df
2. Wir trennen nach der Spalte "Sex"
3. Die Aspect Ration ist benutzerdefiniert (`aspect`)
4. Wir haben die x-Achse auf das Alter des ältesten Passagiers limitiert
5. Die Legende wird angezeigt


```python
# Dein Code hier
```


```python
fig = sns.FacetGrid(titanic_df, hue="Sex",aspect=4)
fig.map(sns.kdeplot,'Age',shade= True)
oldest = titanic_df['Age'].max()
fig.set(xlim=(0,oldest))
fig.add_legend()
```




    <seaborn.axisgrid.FacetGrid at 0x1a19a5f128>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_34_1.png)
    


**Mache jetzt das gleiche für die "person" Spalte.**


```python
# Dein Code hier
```


```python
fig = sns.FacetGrid(titanic_df, hue="person",aspect=4)
fig.map(sns.kdeplot,'Age',shade= True)
oldest = titanic_df['Age'].max()
fig.set(xlim=(0,oldest))
fig.add_legend()
```




    <seaborn.axisgrid.FacetGrid at 0x1a19c630f0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_37_1.png)
    


**Mache jetzt das gleiche für die "Pclass" Spalte.**


```python
# Dein Code hier
```


```python
fig = sns.FacetGrid(titanic_df, hue="Pclass",aspect=4)
fig.map(sns.kdeplot,'Age',shade= True)
oldest = titanic_df['Age'].max()
fig.set(xlim=(0,oldest))
fig.add_legend()
```




    <seaborn.axisgrid.FacetGrid at 0x1a19b27320>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_40_1.png)
    


Wir haben jetzt ein gutes Verständnis dafür erhalten, wer die Passagiere waren. Machen wir mit der 2. Frage weiter: Auf welchem Deck waren die Passagiere und wie hängt das mit ihrere Klasse zusammen?

**Schaue dir erneut den `head()` des DataFrames an.**


```python
titanic_df.head()
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
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
      <th>person</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
      <td>male</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
      <td>female</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
      <td>female</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1</td>
      <td>1</td>
      <td>Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>113803</td>
      <td>53.1000</td>
      <td>C123</td>
      <td>S</td>
      <td>female</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>0</td>
      <td>3</td>
      <td>Allen, Mr. William Henry</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>373450</td>
      <td>8.0500</td>
      <td>NaN</td>
      <td>S</td>
      <td>male</td>
    </tr>
  </tbody>
</table>
</div>



Wir sehen hier, dass die Spalte "Cabin" (dt. Kabine) die Information über das Deck enthält. Allerdings liegen auch viele NaN Werte vor. Wir sollten sie loswerden.

**Erstelle ein neues Objekt "deck", dass die Cabin-Werte des DataFrames ausschließlich der NaN Werte enthält.**


```python
deck = titanic_df['Cabin'].dropna()
```

**Kurzer Einblick in die ersten Zeilen des neuen Objekts.**


```python
deck.head()
```




    1      C85
    3     C123
    6      E46
    10      G6
    11    C103
    Name: Cabin, dtype: object



Wir sehen hier, dass wir für das Deck (A, B, C, usw.) nur den ersten Buchstaben der Kabine brauchen. 

**Erstelle eine leere Liste "levels".**


```python
levels = []
```

**Erstelle eine for-Schleife, die unserer Liste die Decks hinzufügt. Grundlage bildet die Kabine. Sortiere anschliesend deine Liste.**


```python
for level in deck:
    levels.append(level[0])
    
levels.sort()
```

**Erstelle aus unserer Liste einen DataFrame "cabin_df". Bennen außerdem die Spalte in "Cabin" um.**


```python
cabin_df = DataFrame(levels)
cabin_df.columns = ['Cabin']
```

**Nutze Seaborn, um ein countplot für die Passagiere pro Klasse zu erzeugen.**


```python
# Dein Code hier
```


```python
sns.countplot('Cabin',data=cabin_df)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1a1a2be940>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_55_1.png)
    


Komischerweise haben wir eine "T" Kabine, die aus der Reihe fällt.

**Lösche diesen Werte aus dem DataFrame und erzeuge das Countplot erneut.**


```python
# Dein Code hier
```


```python
cabin_df = cabin_df[cabin_df.Cabin != 'T']
sns.countplot('Cabin',data=cabin_df,palette='summer')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1a1a462198>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_58_1.png)
    


*Hinweis: Im letzten Plot habe die Palette "Summer" genutzt. Du kannst nuten, was du möchtest oder beim Standard bleiben.**

Link zu allen Paletten: [http://matplotlib.org/users/colormaps.html](http://matplotlib.org/users/colormaps.html).

Jetzt wo wir die Verteilung über die Decks kennen kommen wir schon zu Frage 3: Woher kommen die Passagiere?

**Erneut: Schaue dir zuerst den Head des DataFrames an.**


```python
titanic_df.head()
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
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
      <th>person</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
      <td>male</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
      <td>female</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
      <td>female</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1</td>
      <td>1</td>
      <td>Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>113803</td>
      <td>53.1000</td>
      <td>C123</td>
      <td>S</td>
      <td>female</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>0</td>
      <td>3</td>
      <td>Allen, Mr. William Henry</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>373450</td>
      <td>8.0500</td>
      <td>NaN</td>
      <td>S</td>
      <td>male</td>
    </tr>
  </tbody>
</table>
</div>



Die "Embarked" Spalte (dt. eingeschifft) enthält die Buchstaben C, Q und S. Diese stehen für Cherbourg, Queenstown und Southhampton.

**Erstelle ein countplot für Embarked und trenne zusätzlich nach der Klasse.**


```python
# Dein Code hier
```


```python
sns.countplot('Embarked',data=titanic_df,hue='Pclass')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1a1a6404e0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_63_1.png)
    


Wir können hier sehen, dass fast alle Passagiere aus Queenstown der 3. Klasse zugestiegen sind. Interessant könnte sein sich die wirtschaftlichen Bedingungen der Städte zur damiligen Zeit anzuschauen.

Doch fahren wir nun mit unserer 4. Frage fort: Wer war alleine und wer mit seine Familie unterwegs?

**Füge eine neue Spalte "Alone" (dt. allein) hinzu. Sie soll als Inhalt die Summe der Spalten "Parch" und "SibSp" haben. Zeige diese anschließend an.**

*Hinweis: So berechnen wir die Anzahl an Eltern/Kindern und Geschwistern, die auch an Bord waren.**


```python
titanic_df['Alone'] =  titanic_df.Parch + titanic_df.SibSp
titanic_df['Alone']
```




    0       1
    1       1
    2       0
    3       1
    4       0
    5       0
    6       0
    7       4
    8       2
    9       1
    10      2
    11      0
    12      0
    13      6
    14      0
    15      0
    16      5
    17      0
    18      1
    19      0
    20      0
    21      0
    22      0
    23      0
    24      4
    25      6
    26      0
    27      5
    28      0
    29      0
           ..
    861     1
    862     0
    863    10
    864     0
    865     0
    866     1
    867     0
    868     0
    869     2
    870     0
    871     2
    872     0
    873     0
    874     1
    875     0
    876     0
    877     0
    878     0
    879     1
    880     1
    881     0
    882     0
    883     0
    884     0
    885     5
    886     0
    887     0
    888     3
    889     0
    890     0
    Name: Alone, Length: 891, dtype: int64



Wir wissen jetzt, dass immer wenn die Alone Spalte etwas anders als 0 ist, jemand nicht alleine gereist ist. Wir können die Spalte jetzt weiter bearbeiten.

**Überschreibe die Alone Spalte wie folgt: Wenn der Wert 0 ist, dann füge "Alone" (dt. allein) ein. Wenn der Wert größer als 0 ist, dann füge "With Family" (dt. mit Familie) ein.**

*Hinweis: Manchmal taucht dabei ein Error auf, den wir ignorieren können.*


```python
titanic_df['Alone'].loc[titanic_df['Alone'] >0] = 'With Family'
titanic_df['Alone'].loc[titanic_df['Alone'] == 0] = 'Alone'
```

    /Users/davidmika/anaconda3/lib/python3.5/site-packages/pandas/core/indexing.py:194: SettingWithCopyWarning: 
    A value is trying to be set on a copy of a slice from a DataFrame
    
    See the caveats in the documentation: http://pandas.pydata.org/pandas-docs/stable/indexing.html#indexing-view-versus-copy
      self._setitem_with_indexer(indexer, value)


**Schaue dir das Ergebnis deiner Arbeit mit `head()` an.**


```python
titanic_df.head()
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
      <th>PassengerId</th>
      <th>Survived</th>
      <th>Pclass</th>
      <th>Name</th>
      <th>Sex</th>
      <th>Age</th>
      <th>SibSp</th>
      <th>Parch</th>
      <th>Ticket</th>
      <th>Fare</th>
      <th>Cabin</th>
      <th>Embarked</th>
      <th>person</th>
      <th>Alone</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>0</td>
      <td>3</td>
      <td>Braund, Mr. Owen Harris</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>A/5 21171</td>
      <td>7.2500</td>
      <td>NaN</td>
      <td>S</td>
      <td>male</td>
      <td>With Family</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>Cumings, Mrs. John Bradley (Florence Briggs Th...</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>PC 17599</td>
      <td>71.2833</td>
      <td>C85</td>
      <td>C</td>
      <td>female</td>
      <td>With Family</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1</td>
      <td>3</td>
      <td>Heikkinen, Miss. Laina</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>STON/O2. 3101282</td>
      <td>7.9250</td>
      <td>NaN</td>
      <td>S</td>
      <td>female</td>
      <td>Alone</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1</td>
      <td>1</td>
      <td>Futrelle, Mrs. Jacques Heath (Lily May Peel)</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>113803</td>
      <td>53.1000</td>
      <td>C123</td>
      <td>S</td>
      <td>female</td>
      <td>With Family</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>0</td>
      <td>3</td>
      <td>Allen, Mr. William Henry</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>373450</td>
      <td>8.0500</td>
      <td>NaN</td>
      <td>S</td>
      <td>male</td>
      <td>Alone</td>
    </tr>
  </tbody>
</table>
</div>



**Erzeuge mit Seaborn eine einfache Visualisierung, die die alleinreisend mit den anderne vergleicht.**


```python
# Dein Code hier
```


```python
sns.countplot('Alone',data=titanic_df,palette='Blues')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1a1a367e80>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_72_1.png)
    


Wir kennen unsere Daten jetzt schon ganz gut. Wir haben die Passagiere ziemlich umfassend kennengelernt und ein Gefühl dafür entwickelt, wer auf der Titanic gereist ist.

Beschäftigen wir uns nun mit der etwas komplexeren und offenen Frage danach, welche Faktoren beim Überleben eine Rolle gespielt haben.

Zum leichteren Verständnis wollen wir die Spalte "Survived" (dt. überlebt) mit der `map` Funktion etwas umwandeln.

**Ersteze die 0 mit "no" (dt. nein) und die 1 mit "yes" (dt. ja).**


```python
titanic_df["Survivor"] = titanic_df.Survived.map({0: "no", 1: "yes"})
```

**Schaue dir nun die Verteilung zwischen Überlebenden und Nicht-Überlebenden mit Seaborn an.**


```python
# Dein Code hier
```


```python
sns.countplot('Survivor',data=titanic_df)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1a1a367630>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_77_1.png)
    


Es sind also einige mehr Menschen gestorben, als überlebt haben. Lass uns untersuchen, ob die Klasse eine Rolle beim Überleben gespielt haben könnte. Wenn wir an den Film "Titanic" denken, hat er genau diesen Faktor sehr betont.

**Erstelle ein `factorplot`, das "Survived" und "Pclass" gegenüberstellt.**


```python
# Dein Code hier
```


```python
sns.factorplot('Pclass','Survived',data=titanic_df)
```




    <seaborn.axisgrid.FacetGrid at 0x1a1a37fb00>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_80_1.png)
    


Sieht aus, als ob die Überlebensrate für die 3. Klasse sehr viel niedriger ist. Das könnte aber auch damit zusammenhängen, dass es viel mehr Männer in der 3. Klasse gab. Erinnert euch an die "Kinder und Frauen zuerst!"-Politik.

**Erstelle das Factorplot erneut, trenne diesesmal aber nach "person".**


```python
# Dein Code hier
```


```python
sns.factorplot('Pclass','Survived',hue='person',data=titanic_df)
```




    <seaborn.axisgrid.FacetGrid at 0x1a1a878cf8>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_83_1.png)
    


Wir sehen hier, dass sowohl ein Mann zu sein, als auch in der 3. Klasse zu sein beides nicht begünstigend fürs Überleben war. Und auch unabhängig von der Klasse wurden die Überlebenschancen für Männer ziemlich stark reduziert.

Welche Rolle spielte das Alter? Hatte jünger oder älter zu sein einen Effekt?

**Erstelle ein `lmplot`, um den Zusammenhang zwischen Alter und Überleben zu überprüfen.**


```python
# Dein Code hier
```


```python
sns.lmplot('Age','Survived',data=titanic_df)
```




    <seaborn.axisgrid.FacetGrid at 0x1a1aade978>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_86_1.png)
    


Sieht nach einem Trend aus: Je älter die Passagiere waren, desto unwahrscheinlicher ihr Überleben. Schauen wir uns erneut an, ob das für alle Klasse gleich ist.

**Erstelle das Lmplot erneut, trenne diesesmal aber nach "Pclass".**


```python
# Dein Code
```


```python
sns.lmplot('Age','Survived',hue='Pclass',data=titanic_df,palette='winter')
```




    <seaborn.axisgrid.FacetGrid at 0x1a1aac1d68>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_89_1.png)
    


Wir können das `x_bins` Argument nutzen, um diese Darstellung etwas aufzuräumen. Dazu geben wir dir zunächst die Generationen:


```python
generations=[10,20,40,60,80]
```

**Erstelle das Lmplot erneut für Age und Survieved. Dabei trennen wir außerdem nach Klasse. Binde außerdem die "generations" per `x_bins` ein.**


```python
# Dein Code hier
```


```python
sns.lmplot('Age','Survived',hue='Pclass',data=titanic_df,palette='winter',x_bins=generations)
```




    <seaborn.axisgrid.FacetGrid at 0x1a1ad640f0>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_94_1.png)
    


Interessante Erkenntnis für die älteren Passagiere der 1. Klasse. Was sehen wir, wenn wir Geschlecht und Alter mit dem Überleben übeprüfen?

**Erstelle das Lmplot erneut, trenne aber diesesmal nach Geschlecht (Spalte: Sex).**


```python
# Dein Code hier
```


```python
sns.lmplot('Age','Survived',hue='Sex',data=titanic_df,palette='winter',x_bins=generations)
```




    <seaborn.axisgrid.FacetGrid at 0x1a1b8b37b8>




    
![png](/home/stefan/Code/Github_ContactStefanBauer/Cheatsheets-Python/02_DataScience/07_MeilensteinProjekte_DataScience/01-Titanic_Projekt/Markdown/02-Loesung_Titanic_Projekt_97_1.png)
    


Großartig! Wir konnten sehr viel über die Titanic, ihre Passagiere und deren Überleben herausfinden!

Falls du das möchtest kannst du gerne nioch weitere Faktoren untersuchen. Z.b den Zusammenhang zwischen dem Deck und dem Überleben. Alles weitere ist vollkommen freiwillig und optional.

# Gut gemacht!

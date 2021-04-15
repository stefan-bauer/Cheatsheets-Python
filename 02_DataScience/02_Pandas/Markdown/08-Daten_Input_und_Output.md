# Daten Input und Output

Quelle: Datamics

Dieses Notebook dient als Referenz, um Input und Output zu erhalten. Pandas kann eine Vielzahl von Dateitypen durch die Methode `pd.read_` lesen. Lasst uns die häufigsten Daten Typen anschauen:


```python
import numpy as np
import pandas as pd
```

## CSV
### CSV Input


```python
df = pd.read_csv('example.csv')
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
      <td>7</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>9</td>
      <td>10</td>
      <td>11</td>
    </tr>
    <tr>
      <th>3</th>
      <td>12</td>
      <td>13</td>
      <td>14</td>
      <td>15</td>
    </tr>
  </tbody>
</table>
</div>



### CSV Output


```python
df.to_csv('my_example.csv',index=False)
```

## Excel

Pandas kann Excel-Dateien lesen und schreiben. Beachtet aber, dass dabei nur Daten importiert werden. Formeln und Bilder sind dabei nicht eingeschlossen. Makros oder Bilder in der Datei zu haben kann die `read_excel` Methode zum Abstürzen bringen.

### Excel Input


```python
pd.read_excel('Excel_Sample.xlsx',sheetname='Sheet1')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4</td>
      <td>5</td>
      <td>6</td>
      <td>7</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>9</td>
      <td>10</td>
      <td>11</td>
    </tr>
    <tr>
      <th>3</th>
      <td>12</td>
      <td>13</td>
      <td>14</td>
      <td>15</td>
    </tr>
  </tbody>
</table>
</div>



### Excel Output


```python
df.to_excel('Excel_Sample.xlsx',sheet_name='Sheet1')
```

## HTML

Es ist gut möglich, dass du zuerst die html5lib, lxml und BeautifulSoup4 installieren müsst. In deinem Terminal bzw. deiner Kommandozeile führe folgenden Code aus:

    conda install lxml
    conda install html5lib
    conda install BeautifulSoup4
    
Dann starte das Jupyter Notebook neu.

Pandas kann Tabellen Tabs aus einem HTMl lesen. Zum Beispiel:

### HTML Input

Pandas `read_html` Methode wird Tabellen aus dem HTML auslesen und eine Liste von Data Frames zurückgeben:


```python
df_html = pd.read_html('http://www.fdic.gov/bank/individual/failed/banklist.html')
```


```python
df_html[0]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bank Name</th>
      <th>City</th>
      <th>ST</th>
      <th>CERT</th>
      <th>Acquiring Institution</th>
      <th>Closing Date</th>
      <th>Updated Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Fayette County Bank</td>
      <td>Saint Elmo</td>
      <td>IL</td>
      <td>1802</td>
      <td>United Fidelity Bank, fsb</td>
      <td>May 26, 2017</td>
      <td>July 26, 2017</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Guaranty Bank, (d/b/a BestBank in Georgia &amp; Mi...</td>
      <td>Milwaukee</td>
      <td>WI</td>
      <td>30003</td>
      <td>First-Citizens Bank &amp; Trust Company</td>
      <td>May 5, 2017</td>
      <td>July 26, 2017</td>
    </tr>
    <tr>
      <th>2</th>
      <td>First NBC Bank</td>
      <td>New Orleans</td>
      <td>LA</td>
      <td>58302</td>
      <td>Whitney Bank</td>
      <td>April 28, 2017</td>
      <td>July 26, 2017</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Proficio Bank</td>
      <td>Cottonwood Heights</td>
      <td>UT</td>
      <td>35495</td>
      <td>Cache Valley Bank</td>
      <td>March 3, 2017</td>
      <td>May 18, 2017</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Seaway Bank and Trust Company</td>
      <td>Chicago</td>
      <td>IL</td>
      <td>19328</td>
      <td>State Bank of Texas</td>
      <td>January 27, 2017</td>
      <td>May 18, 2017</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Harvest Community Bank</td>
      <td>Pennsville</td>
      <td>NJ</td>
      <td>34951</td>
      <td>First-Citizens Bank &amp; Trust Company</td>
      <td>January 13, 2017</td>
      <td>May 18, 2017</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Allied Bank</td>
      <td>Mulberry</td>
      <td>AR</td>
      <td>91</td>
      <td>Today's Bank</td>
      <td>September 23, 2016</td>
      <td>November 17, 2016</td>
    </tr>
    <tr>
      <th>7</th>
      <td>The Woodbury Banking Company</td>
      <td>Woodbury</td>
      <td>GA</td>
      <td>11297</td>
      <td>United Bank</td>
      <td>August 19, 2016</td>
      <td>June 1, 2017</td>
    </tr>
    <tr>
      <th>8</th>
      <td>First CornerStone Bank</td>
      <td>King of Prussia</td>
      <td>PA</td>
      <td>35312</td>
      <td>First-Citizens Bank &amp; Trust Company</td>
      <td>May 6, 2016</td>
      <td>September 6, 2016</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Trust Company Bank</td>
      <td>Memphis</td>
      <td>TN</td>
      <td>9956</td>
      <td>The Bank of Fayette County</td>
      <td>April 29, 2016</td>
      <td>September 6, 2016</td>
    </tr>
    <tr>
      <th>10</th>
      <td>North Milwaukee State Bank</td>
      <td>Milwaukee</td>
      <td>WI</td>
      <td>20364</td>
      <td>First-Citizens Bank &amp; Trust Company</td>
      <td>March 11, 2016</td>
      <td>March 13, 2017</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Hometown National Bank</td>
      <td>Longview</td>
      <td>WA</td>
      <td>35156</td>
      <td>Twin City Bank</td>
      <td>October 2, 2015</td>
      <td>April 13, 2016</td>
    </tr>
    <tr>
      <th>12</th>
      <td>The Bank of Georgia</td>
      <td>Peachtree City</td>
      <td>GA</td>
      <td>35259</td>
      <td>Fidelity Bank</td>
      <td>October 2, 2015</td>
      <td>October 24, 2016</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Premier Bank</td>
      <td>Denver</td>
      <td>CO</td>
      <td>34112</td>
      <td>United Fidelity Bank, fsb</td>
      <td>July 10, 2015</td>
      <td>August 17, 2016</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Edgebrook Bank</td>
      <td>Chicago</td>
      <td>IL</td>
      <td>57772</td>
      <td>Republic Bank of Chicago</td>
      <td>May 8, 2015</td>
      <td>July 12, 2016</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Doral Bank  En Espanol</td>
      <td>San Juan</td>
      <td>PR</td>
      <td>32102</td>
      <td>Banco Popular de Puerto Rico</td>
      <td>February 27, 2015</td>
      <td>May 13, 2015</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Capitol City Bank &amp; Trust Company</td>
      <td>Atlanta</td>
      <td>GA</td>
      <td>33938</td>
      <td>First-Citizens Bank &amp; Trust Company</td>
      <td>February 13, 2015</td>
      <td>April 21, 2015</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Highland Community Bank</td>
      <td>Chicago</td>
      <td>IL</td>
      <td>20290</td>
      <td>United Fidelity Bank, fsb</td>
      <td>January 23, 2015</td>
      <td>April 21, 2015</td>
    </tr>
    <tr>
      <th>18</th>
      <td>First National Bank of Crestview</td>
      <td>Crestview</td>
      <td>FL</td>
      <td>17557</td>
      <td>First NBC Bank</td>
      <td>January 16, 2015</td>
      <td>May 8, 2017</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Northern Star Bank</td>
      <td>Mankato</td>
      <td>MN</td>
      <td>34983</td>
      <td>BankVista</td>
      <td>December 19, 2014</td>
      <td>January 6, 2016</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Frontier Bank, FSB D/B/A El Paseo Bank</td>
      <td>Palm Desert</td>
      <td>CA</td>
      <td>34738</td>
      <td>Bank of Southern California, N.A.</td>
      <td>November 7, 2014</td>
      <td>November 10, 2016</td>
    </tr>
    <tr>
      <th>21</th>
      <td>The National Republic Bank of Chicago</td>
      <td>Chicago</td>
      <td>IL</td>
      <td>916</td>
      <td>State Bank of Texas</td>
      <td>October 24, 2014</td>
      <td>January 6, 2016</td>
    </tr>
    <tr>
      <th>22</th>
      <td>NBRS Financial</td>
      <td>Rising Sun</td>
      <td>MD</td>
      <td>4862</td>
      <td>Howard Bank</td>
      <td>October 17, 2014</td>
      <td>March 26, 2015</td>
    </tr>
    <tr>
      <th>23</th>
      <td>GreenChoice Bank, fsb</td>
      <td>Chicago</td>
      <td>IL</td>
      <td>28462</td>
      <td>Providence Bank, LLC</td>
      <td>July 25, 2014</td>
      <td>December 12, 2016</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Eastside Commercial Bank</td>
      <td>Conyers</td>
      <td>GA</td>
      <td>58125</td>
      <td>Community &amp; Southern Bank</td>
      <td>July 18, 2014</td>
      <td>July 11, 2016</td>
    </tr>
    <tr>
      <th>25</th>
      <td>The Freedom State Bank</td>
      <td>Freedom</td>
      <td>OK</td>
      <td>12483</td>
      <td>Alva State Bank &amp; Trust Company</td>
      <td>June 27, 2014</td>
      <td>March 25, 2016</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Valley Bank</td>
      <td>Fort Lauderdale</td>
      <td>FL</td>
      <td>21793</td>
      <td>Landmark Bank, National Association</td>
      <td>June 20, 2014</td>
      <td>June 29, 2015</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Valley Bank</td>
      <td>Moline</td>
      <td>IL</td>
      <td>10450</td>
      <td>Great Southern Bank</td>
      <td>June 20, 2014</td>
      <td>June 26, 2015</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Slavie Federal Savings Bank</td>
      <td>Bel Air</td>
      <td>MD</td>
      <td>32368</td>
      <td>Bay Bank, FSB</td>
      <td>May 30, 2014</td>
      <td>December 12, 2016</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Columbia Savings Bank</td>
      <td>Cincinnati</td>
      <td>OH</td>
      <td>32284</td>
      <td>United Fidelity Bank, fsb</td>
      <td>May 23, 2014</td>
      <td>November 10, 2016</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>523</th>
      <td>ANB Financial, NA</td>
      <td>Bentonville</td>
      <td>AR</td>
      <td>33901</td>
      <td>Pulaski Bank and Trust Company</td>
      <td>May 9, 2008</td>
      <td>August 28, 2012</td>
    </tr>
    <tr>
      <th>524</th>
      <td>Hume Bank</td>
      <td>Hume</td>
      <td>MO</td>
      <td>1971</td>
      <td>Security Bank</td>
      <td>March 7, 2008</td>
      <td>August 28, 2012</td>
    </tr>
    <tr>
      <th>525</th>
      <td>Douglass National Bank</td>
      <td>Kansas City</td>
      <td>MO</td>
      <td>24660</td>
      <td>Liberty Bank and Trust Company</td>
      <td>January 25, 2008</td>
      <td>October 26, 2012</td>
    </tr>
    <tr>
      <th>526</th>
      <td>Miami Valley Bank</td>
      <td>Lakeview</td>
      <td>OH</td>
      <td>16848</td>
      <td>The Citizens Banking Company</td>
      <td>October 4, 2007</td>
      <td>September 12, 2016</td>
    </tr>
    <tr>
      <th>527</th>
      <td>NetBank</td>
      <td>Alpharetta</td>
      <td>GA</td>
      <td>32575</td>
      <td>ING DIRECT</td>
      <td>September 28, 2007</td>
      <td>August 28, 2012</td>
    </tr>
    <tr>
      <th>528</th>
      <td>Metropolitan Savings Bank</td>
      <td>Pittsburgh</td>
      <td>PA</td>
      <td>35353</td>
      <td>Allegheny Valley Bank of Pittsburgh</td>
      <td>February 2, 2007</td>
      <td>October 27, 2010</td>
    </tr>
    <tr>
      <th>529</th>
      <td>Bank of Ephraim</td>
      <td>Ephraim</td>
      <td>UT</td>
      <td>1249</td>
      <td>Far West Bank</td>
      <td>June 25, 2004</td>
      <td>April 9, 2008</td>
    </tr>
    <tr>
      <th>530</th>
      <td>Reliance Bank</td>
      <td>White Plains</td>
      <td>NY</td>
      <td>26778</td>
      <td>Union State Bank</td>
      <td>March 19, 2004</td>
      <td>April 9, 2008</td>
    </tr>
    <tr>
      <th>531</th>
      <td>Guaranty National Bank of Tallahassee</td>
      <td>Tallahassee</td>
      <td>FL</td>
      <td>26838</td>
      <td>Hancock Bank of Florida</td>
      <td>March 12, 2004</td>
      <td>June 5, 2012</td>
    </tr>
    <tr>
      <th>532</th>
      <td>Dollar Savings Bank</td>
      <td>Newark</td>
      <td>NJ</td>
      <td>31330</td>
      <td>No Acquirer</td>
      <td>February 14, 2004</td>
      <td>April 9, 2008</td>
    </tr>
    <tr>
      <th>533</th>
      <td>Pulaski Savings Bank</td>
      <td>Philadelphia</td>
      <td>PA</td>
      <td>27203</td>
      <td>Earthstar Bank</td>
      <td>November 14, 2003</td>
      <td>July 22, 2005</td>
    </tr>
    <tr>
      <th>534</th>
      <td>First National Bank of Blanchardville</td>
      <td>Blanchardville</td>
      <td>WI</td>
      <td>11639</td>
      <td>The Park Bank</td>
      <td>May 9, 2003</td>
      <td>June 5, 2012</td>
    </tr>
    <tr>
      <th>535</th>
      <td>Southern Pacific Bank</td>
      <td>Torrance</td>
      <td>CA</td>
      <td>27094</td>
      <td>Beal Bank</td>
      <td>February 7, 2003</td>
      <td>October 20, 2008</td>
    </tr>
    <tr>
      <th>536</th>
      <td>Farmers Bank of Cheneyville</td>
      <td>Cheneyville</td>
      <td>LA</td>
      <td>16445</td>
      <td>Sabine State Bank &amp; Trust</td>
      <td>December 17, 2002</td>
      <td>October 20, 2004</td>
    </tr>
    <tr>
      <th>537</th>
      <td>Bank of Alamo</td>
      <td>Alamo</td>
      <td>TN</td>
      <td>9961</td>
      <td>No Acquirer</td>
      <td>November 8, 2002</td>
      <td>March 18, 2005</td>
    </tr>
    <tr>
      <th>538</th>
      <td>AmTrade International Bank  En Espanol</td>
      <td>Atlanta</td>
      <td>GA</td>
      <td>33784</td>
      <td>No Acquirer</td>
      <td>September 30, 2002</td>
      <td>September 11, 2006</td>
    </tr>
    <tr>
      <th>539</th>
      <td>Universal Federal Savings Bank</td>
      <td>Chicago</td>
      <td>IL</td>
      <td>29355</td>
      <td>Chicago Community Bank</td>
      <td>June 27, 2002</td>
      <td>April 9, 2008</td>
    </tr>
    <tr>
      <th>540</th>
      <td>Connecticut Bank of Commerce</td>
      <td>Stamford</td>
      <td>CT</td>
      <td>19183</td>
      <td>Hudson United Bank</td>
      <td>June 26, 2002</td>
      <td>February 14, 2012</td>
    </tr>
    <tr>
      <th>541</th>
      <td>New Century Bank</td>
      <td>Shelby Township</td>
      <td>MI</td>
      <td>34979</td>
      <td>No Acquirer</td>
      <td>March 28, 2002</td>
      <td>March 18, 2005</td>
    </tr>
    <tr>
      <th>542</th>
      <td>Net 1st National Bank</td>
      <td>Boca Raton</td>
      <td>FL</td>
      <td>26652</td>
      <td>Bank Leumi USA</td>
      <td>March 1, 2002</td>
      <td>April 9, 2008</td>
    </tr>
    <tr>
      <th>543</th>
      <td>NextBank, NA</td>
      <td>Phoenix</td>
      <td>AZ</td>
      <td>22314</td>
      <td>No Acquirer</td>
      <td>February 7, 2002</td>
      <td>February 5, 2015</td>
    </tr>
    <tr>
      <th>544</th>
      <td>Oakwood Deposit Bank Co.</td>
      <td>Oakwood</td>
      <td>OH</td>
      <td>8966</td>
      <td>The State Bank &amp; Trust Company</td>
      <td>February 1, 2002</td>
      <td>October 25, 2012</td>
    </tr>
    <tr>
      <th>545</th>
      <td>Bank of Sierra Blanca</td>
      <td>Sierra Blanca</td>
      <td>TX</td>
      <td>22002</td>
      <td>The Security State Bank of Pecos</td>
      <td>January 18, 2002</td>
      <td>November 6, 2003</td>
    </tr>
    <tr>
      <th>546</th>
      <td>Hamilton Bank, NA  En Espanol</td>
      <td>Miami</td>
      <td>FL</td>
      <td>24382</td>
      <td>Israel Discount Bank of New York</td>
      <td>January 11, 2002</td>
      <td>September 21, 2015</td>
    </tr>
    <tr>
      <th>547</th>
      <td>Sinclair National Bank</td>
      <td>Gravette</td>
      <td>AR</td>
      <td>34248</td>
      <td>Delta Trust &amp; Bank</td>
      <td>September 7, 2001</td>
      <td>February 10, 2004</td>
    </tr>
    <tr>
      <th>548</th>
      <td>Superior Bank, FSB</td>
      <td>Hinsdale</td>
      <td>IL</td>
      <td>32646</td>
      <td>Superior Federal, FSB</td>
      <td>July 27, 2001</td>
      <td>August 19, 2014</td>
    </tr>
    <tr>
      <th>549</th>
      <td>Malta National Bank</td>
      <td>Malta</td>
      <td>OH</td>
      <td>6629</td>
      <td>North Valley Bank</td>
      <td>May 3, 2001</td>
      <td>November 18, 2002</td>
    </tr>
    <tr>
      <th>550</th>
      <td>First Alliance Bank &amp; Trust Co.</td>
      <td>Manchester</td>
      <td>NH</td>
      <td>34264</td>
      <td>Southern New Hampshire Bank &amp; Trust</td>
      <td>February 2, 2001</td>
      <td>February 18, 2003</td>
    </tr>
    <tr>
      <th>551</th>
      <td>National State Bank of Metropolis</td>
      <td>Metropolis</td>
      <td>IL</td>
      <td>3815</td>
      <td>Banterra Bank of Marion</td>
      <td>December 14, 2000</td>
      <td>March 17, 2005</td>
    </tr>
    <tr>
      <th>552</th>
      <td>Bank of Honolulu</td>
      <td>Honolulu</td>
      <td>HI</td>
      <td>21029</td>
      <td>Bank of the Orient</td>
      <td>October 13, 2000</td>
      <td>March 17, 2005</td>
    </tr>
  </tbody>
</table>
<p>553 rows × 7 columns</p>
</div>



## SQL (optional)



```python
from sqlalchemy import create_engine
```


```python
engine = create_engine('sqlite:///:memory:')
```


```python
df.to_sql('data', engine)
```


```python
sql_df = pd.read_sql('data',con=engine)
```


```python
sql_df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
      <th>d</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>4</td>
      <td>5</td>
      <td>6</td>
      <td>7</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>8</td>
      <td>9</td>
      <td>10</td>
      <td>11</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>12</td>
      <td>13</td>
      <td>14</td>
      <td>15</td>
    </tr>
  </tbody>
</table>
</div>



## JSON


```python
import numpy as np
from pandas import Series, DataFrame
import pandas as pd
```


```python
# Heres an example of what a JSON (JavaScript Object Notation) looks like:
json_obj = """
{   "zoo_animal": "Lion",
    "food": ["Meat", "Veggies", "Honey"],
    "fur": "Golden",
    "clothes": null, 
    "diet": [{"zoo_animal": "Gazelle", "food":"grass", "fur": "Brown"}]
}
"""
```


```python
#Let import json module
import json

#Lets load json data
data = json.loads(json_obj)

#Show
data

#WE can also convert back to JSON
json.dumps(data)

#We can simply open JSON data after loading with a DataFrame
dframe = DataFrame(data['diet'])

#Show
dframe

# Theres lost of custom selection you can do, based on what you do or dont want in your DataFrame (you can specify columns..etc)
```

# Gut gemacht!

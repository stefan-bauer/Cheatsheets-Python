# Environment

[TOC]


## Anaconda

### Installation - Linux

[Herunterladen des Installers](https://www.anaconda.com/products/individual)

```bash
cd Downloads
bash Anaconda****.sh
```

AGBs bestätigen und Installationsordner festlegen und anschließend anaconda initialisieren mit **yes**

Überprüfen ob anaconda funktioniert

```bash
source ~/.bashrc
```

Dadurch sieht man dass im Terminal (base) angezeigt wird. Das zeigt die verwendete Environment, also Umgebung, an.
Mittels

```bash
python
```

wird die python shell gestartet. Da kann man schon mal ein wenig testen, ob python korrekt läuft. 

### Environments

#### Aktivierung von Environments

Um ein Environment zu starten wird folgendes verwendet.

```bash
source activate environment_name
```

Nach der Installation hat man nur eines, die _base_. Um diese zu aktivieren, wenn sie nicht schon läuft, kann man nun:

```bash
source activate base
```

verwenden.

#### Anzeigen von Environments

Um die vorhandenen Environments anzuzeigen, dient dieser Befehlt.

```bash
conda env list
```

Mittels list werden alle Pakete eines Environments aufgelistet, mit Versionsnummer. 

```bash
conda list
```

### Environments

Der Environmentname ist beliebig. Hier ist wurde pyLearning gewählt und wird mittels -n angegeben. Danach wird die python Version festgelegt die in dieser Environment verwendet werden soll.

```bash
conda create -n pyLearning python=3.8
```

Nach der Installation des Environments wird die Environment aktiviert.

```bash
conda activate pyLearning
```

Ergänzung: Um eine Environment zu deaktivieren wird folgendes verwendet.

```bash
conda deactivate
```

### Pakete

#### Pip vs. Anaconda

Ein wichtiger Unterschied ist, dass bei Pip nur einzelne Pakete installiert werden können, wo hingegen in Anaconda sogenannte Bundles vorhanden sind. Diese werden von z.B. Usern bereitgestellt.

__Hinweise:__ Um ein Pakte zu installieren bietet sich pip an. Da es aktuellere Versionen hat, und auch selbst ein Paket von anaconda ist. So zerschießt man sein Environment nicht. Es sprich also nichts dagegen.

##### Ueber Conda

Über das Bundle anaconda werden z.B. 90% der wichtigesten Pakete installiert. Braucht natürlich mehr Platz als wenn man nur die ausgewählten Pakte installiert.

```bash
conda install anaconda
```

##### Ueber Pip

Will man nun über pip eine Paketliste nachinstallieren. So kann man sich eine _requirements.txt_ Datei anlegen, worin die benötigten Pakete aufgelistet sind.

```markdown
# Linting
pylint>=2.6.0
flake8>=3.8.3
mypy>=0.782
isort>=5.4.2
black>=20.8b0
autopep8>=1.5.4
pre-commit>=2.6.0
```

Mittels des Terminals wird dann folgender bash Befehl ausgeführt. Hier steht das -r für rekursiven Durchlauf.

```bash
#mit Anconda Installation
pip install -r requirements.txt
```

Falls in Linux anaconda nicht installiert ist, wird nicht pip aufgerufen sondern pip3 für python3

```bash
#Ohne Anaconda Installation
pip3 install -r requirements.txt
```

#### Nachschlagen von Paketen



##### [pypi.org](https://pypi.org)

Auf dieser Webseite kann man einerseits nach Pakete suchen und auch die Versionen nachschlagen.

##### [anaconda](https://anaconda.org/anaconda/repo)

Hier kann man nach Bundles suchen. Also wenn man nicht nur einzelne Pakete braucht sonder, ein Bundle für eine gewisse Aufgabe - wie Tensor Flow - um auch alle zusätzlichen Pakte mitinstallieren zu können.  Meist sind auf anaconda ein wenig ältere Pakte vorhanden.

## VS Code

Die bevorzugte IDE.

### Installation

[Installation](https://code.visualstudio.com/)

### Einrichten

#### Installation der Erweiterungen für Python

| Erweiterung                                 | Author          | Extension Identifier                     | Beschreibung                                                 | Befehl Ctrl + P                                      |
| ------------------------------------------- | --------------- | ---------------------------------------- | ------------------------------------------------------------ | ---------------------------------------------------- |
| Cython                                      | Thomas Walther  | tcwalther.cython                         | syntax highlighting for Cython code.                         | ext install tcwalther.cython                         |
| Language-Cython                             | guyskk          | guyskk.language-cython                   | Syntax highlighter for Python                                | ext install guyskk.language-cython                   |
| Pylance                                     | Microsoft       | ms-python.vscode-pylance                 | IntelliSense experience                                      | ext install ms-python.vscode-pylance                 |
| Python                                      | Microsoft       | ms-python.python                         | IntelliSense, linting, debugging, code navigation, code formatting, Jupyter notebook support, refactoring, variable explorer, test explorer, snippets | ext install ms-python.python                         |
| Python Docstring Generator                  | Nils Werner     | njpwerner.autodocstring                  | quickly generate docstrings for python functions             | ext install njpwerner.autodocstring                  |
| Python Test Explorer for Visual Studio Code | Little Fox Team | littlefoxteam.vscode-python-test-adapter | Run your Python tests in the Sidebar of Visual Studio Code - __braucht Test explorer Ui__ | ext install LittleFoxTeam.vscode-python-test-adapter |
| Test Explorer UI                            | Holger Benl     | hbenl.vscode-test-explorer               | extension provides an extensible user interface for running your tests in VS Code. | ext install hbenl.vscode-test-explorer               |
| Visual Studio IntelliCode                   | Microsoft       | visualstudioexptteam.vscodeintellicode   | provides AI-assisted IntelliSense by showing recommended completion items | ext install VisualStudioExptTeam.vscodeintellicode   |

#### Setting Einstellungen

```json
{
  // Editor settings
  "files.autoSave": "onFocusChange",
  "explorer.confirmDragAndDrop": false,
  "explorer.confirmDelete": false,
  "workbench.startupEditor": "newUntitledFile",
  "editor.suggestSelection": "first",
  "window.zoomLevel": 0,
  // IntelliSense AI Extension
  "vsintellicode.modify.editor.suggestSelection": "automaticallyOverrodeDefaultValue",
  // Windows only settings
//   "terminal.integrated.shell.windows": "C://WINDOWS//System32//cmd.exe",
  // Python Linting settings
  "python.linting.enabled": true,
  "python.linting.lintOnSave": true,
  "python.linting.flake8Enabled": true,
  "python.linting.pylintEnabled": true,
  "python.linting.mypyEnabled": true,
  "python.formatting.provider": "autopep8",
  // Python Execution settings
  "python.languageServer": "Pylance",
  "python.showStartPage": false,
  // Python Docstring settings
  "autoDocstring.docstringFormat": "numpy", //"google",
  "autoDocstring.generateDocstringOnEnter": true,
  // Git settings
  "git.enableSmartCommit": true,
  "git.autofetch": true,
  "git.confirmSync": false,
}
```

#### Shortcuts

* <code>Ctrl + G </code> Zeilennummer - springt zu Codezeile
* <code>F12 </code> Zu der Definition der Funktion springen
* <code>Alt+F12 </code> Vorschau der Definition der Funktion
* <code>Shift+Alt+F12 </code> Zeigt wo die Funktion im Code überall vorkommen.  
* <code>Shift+Tab</code> Zurück taben
* <code>Ctrl+K,Ctrl+0,</code> Colaps Ebene 0
* <code>Ctrl+K,Ctrl+2,</code> Colaps Ebene 2
* <code>Ctrl+K,Ctrl+J,</code> Zurückklappen



#### Hinweise

* Über der geöffneten Datei kann man auf Variablen klicken und man sieht alle Variablen bzw. sieht die Ordnerstrucktur. Ideal für externe Pakete da die Ordnerstrucktur ja nicht in der Seitenleiste aufgelistet ist.
* 

### Anwendung

Wenn man im Linux Terminal ist und 

```bash
code .
```

verwendet, wird VS Code in diesem Ordner gestartet.


## Python Shell

### Start

```bash
python
```

### Help

Mittels Help und den Namen der Klasse kann man sich die Dokumentation anzeigen lassen

```bash
help(list)
```

### Ende

```bash
exit()
```

## IPython Shell

Hier kann man auch Datein ausführen und im Zwischenspeicher werden die Variable Werte erhalten

### Start

```bash
ipython
```

### Help

Mittels Help und den Namen der Klasse kann man sich die Dokumentation anzeigen lassen

```bash
help(list)
```

### Ausführen

In der IPython Shell mittels

```bash
%run Dateiname.py
```

kann die Python Datei ausgeführt werden

### Ende

```bash
exit()
```

## Jupyter Lab / Notebook

Sehr Hilfreich, da python code blockweise ausgeführt werden kann. Zusätzlich kann man auch Markdown Latex usw. verwenden. Zum Beispiel kann über markdown auch eine beschreibende mathematische Formel wie z.B. $\sum_{i}^{n} x_i$ eingeblendet werden.

```markdown
$\sum_{i}^{n} x_i$
```

Dateiendung: ipynb

Hilfreiche Links:

[Jupyter Notebook Doc]( https://jupyter-notebook.readthedocs.io/en/stable/)

[Jupyter Lab Doc]( https://jupyterlab.readthedocs.io/en/stable/)

[Jupyter Lab Blog Post]( https://blog.jupyter.org/jupyterlab-is-ready-for-users-5a6f039b8906?gi=2f871f60dc3)

Bash Befehle zum Starten

```bash
jupyter notebook
```

```bash
jupyter lab
```


### Jupyter Lab Keybord Shortcodes

Hier gibt es zwei Modi **command mode** and **edit mode**. Gewechselt zwischen den beiden wird mit Esc:

[Webseite von der ich die Shortcuts haben](https://towardsdatascience.com/jypyter-notebook-shortcuts-bf0101a98330)

#### Shortcodes für beide Modi

* <code>Shift + Enter</code> run the current cell, select below
* <code>Ctrl + Enter</code> run selected cells
* <code>Alt + Enter</code> run the current cell, insert below
* <code>Ctrl + S</code> save and checkpoint

#### command mode (press Esc to activate):

* <code>Enter</code> take you into edit mode
* <code>H </code>show all shortcuts
* <code>Up</code> select cell above
* <code>Down </code>select cell below
* <code>Shift + Up</code> extend selected cells above
* <code>Shift + Down</code> extend selected cells below
* <code>A</code> insert cell above
* <code>B</code> insert cell below
* <code>X</code> cut selected cells
* <code>C</code> copy selected cells
* <code>V</code> paste cells below
* <code>Shift + V</code> paste cells above
* <code>D, D</code> (press the key twice) delete selected cells
* <code>Z</code> undo cell deletion
* <code>S</code> Save and Checkpoint
* <code>Y</code> change the cell type to Code
* <code>M</code> change the cell type to Markdown
* <code>P</code> open the command palette.
  This dialog helps you run any command by name. It’s really useful if you don’t know some shortcut or when you don’t have a shortcut for the wanted command.
* <code>Shift + Space</code> scroll notebook up
* <code>Space</code> scroll notebook down

#### in edit mode (pressEnter to activate)

* <code>Esc </code>take you into command mode
* <code>Tab </code>code completion or indent
* <code>Shift + Tab</code> tooltip
* <code>Ctrl + ]</code> indent
* <code>Ctrl + [</code> dedent
* <code>Ctrl + A </code>select all
* <code>Ctrl + Z </code>undo
* <code>Ctrl + Shift + Z </code>or <code>Ctrl + Y </code>redo
* <code>Ctrl + Home </code>go to cell start
* <code>Ctrl + End </code>go to cell end
* <code>Ctrl + Left </code>go one word left
* <code>Ctrl + Right </code>go one word right
* <code>Ctrl + Shift + P </code>open the command palette
* <code>Down</code> move cursor down
* <code>Up</code> move cursor up
# Einführung zu Python Anweisungen

Quelle: Datamics

In dieser Lektion werden wir uns einen kurzen Überblick über Python Anweisungen (en.: Statements) verschaffen. Diese Lektion wird die Unterschiede zwischen Python und anderen Sprachen wie C++ herausstellen.

Es gibt zwei Gründe dafür, warum wir diesen Kontext nutzen, um Python Anweisungen zu lernen:

1. Wenn ihr aus einem anderen Programmierumfeld kommt, wird dies super schnell euer Verständnis von Python verbessern.
2. Anweisungen lesen und verstehen zu können wird es euch in der Zukunft erleichtern andere Sprachen schneller lesen und verstehen zu können. 

## Python vs. andere Sprachen

Lasst uns ein simples Statement erstellen, das besagt: "Wenn a größer ist als b, dann weise a die Zahl 2 zu und b die Zahl 4."

Schaut euch diese beiden Statements an:

### Version 1 (andere Sprachen)

    if (a>b){
        a = 2;
        b = 4;
    }
    
### Version 2 (Python)

    if a>b:
        a = 2
        b = 4
        
Ihr werdet feststellen, dass Python weniger überladen ist und sich viel einfacher lesen lässt als die erste Version. Wie stellt Python das an?

Lasst uns die Hauptunterschiede betrachten:

Python verzichtet auf () und {} durch zwei Hauptfaktoren: einen <i>Doppelpunkt</i> und <i>Leerraum</i>. Die Anweisung wird durch den Doppelpunkt beendet und der Leerraum (durch Zeileneinzug) beschreibt, was passiert, sofern das Statement zutrifft.

Zu guter Letzt, um diesen Überblick abzuschließen, schauen wir uns den Zeileneinzug in Python und anderen Sprachen genauer an:

## Blöcke

Ein Block von Code ist eine Gruppierung von Anweisungen in einem Programm oder Skript. Je nach Programmiersprache besteht er aus mindestens einer Anweisung und der Deklaration für den Block. Programmiersprachen, die Strukturierung mit Blöcken erlauben, nennt man **strukturierte Programmiersprachen**. 

Innerhalb von Blöcken können für gewöhnlich weitere Blöcke definiert werden. So entstehen verschachtelte Blockstrukturen. So kann man mehrere Blöcke zusammenfassen, um sie wie eine einzige Anweisung nutzen zu können. Darüber hinaus dienen Blöcke dazu, den Geltungsbereich von Variablen und Funktionen einzuschränken. Auf beides werden wir in der Lektion "*Verschachtelte Anweisungen und Geltungsbereich*" noch genauer eingehen. 

### Andere Sprachen

Viele andere Sprachen benutzen explizite Deklaration für Blöcke. Beispiele sind:
* begin...end
* do...done
* {...}
* if...fi

### Python

Ein großer Vorteil von Python ist es, dass diese explizite Deklaration nicht notwendig ist. Für die Ausführung vieler Programmiersprachen sind leere Räume und Zeileneinzug ohne jegliche Bedeutung. Python nutzt genau diese, um seine Blöcke zu definieren.

## Zeileneinzug

Hier ist ein bisschen Dummy Code um aufzuzeigen, wie Leerraum und Einzug in Python genutzt werden.

### Andere Sprache

    if (x) {
        if(y) {
            code-statement;
        }}
    else {
        anderes-code-statement;
        }

### Python

    if x:
        if y:
            code-statement
    else:
        anderes-code-statement
        
Achtet darauf, wie stark Python durch den Code Zeileneinzug und den Leerraum getrieben wird. Das bedeutet gleichzeitig, dass die Lesbarkeit des Codes eine der wichtigen Aspekte der Python Sprache ist.

Jetzt lasst uns tiefer ins Coden von Statements in Python einsteigen!

## Zeit zu coden!

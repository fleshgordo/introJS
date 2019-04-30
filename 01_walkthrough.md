### Einführung JS

#### Javascript Syntax

##### Statements

Ein Computerprogramm ist eine Liste von „Anweisungen“ die durch den Computer ausgeführt werden.

In einer Programmiersprache nennt man diese Programmanweisungen Aussagen/Statements.

JavaScript ist eine (interpretierte) Programmiersprache (sie wird nicht kompiliert so wie z.B. C).

JavaScript - Statements werden durch Semikolons getrennt.

```js
var x, y, z;
x = 5;
y = 6;
z = x + y;
```
##### Kommentare

Nicht alle JavaScript-Anweisungen werden „ausgeführt“.

Code nach doppelten Schrägstrichen // oder zwischen / * und * / wird als  Kommentar behandelt.

Kommentare werden ignoriert und nicht ausgeführt:
```javascript
var x = 5;   // I will be executed

// var x = 6;   I will NOT be executed

/*
.:::.   .:::.
:::::::.:::::::
:::::::::::::::
':::::::::::::'
  ':::::::::'
    ':::::'
      ':'
*/
```
##### Variablen

JavaScript Variablen sind Container für Datenwerte zu speichern.

```javascript
// Ganzzahl
var jahr = 2017;

// Fliesskomma
var pi = 3.14;

// String, Text
var message = "Hello world!";
var message = 'Hello world!';

// Boolean
var isIpad = true;

// undefined
var dada;
console.log(dada);

// Objekte und arrays
var objekt = { x: 12, y: 15};
var zahlenreihe = [1,2,3];
```

Einmal als Variable gespeichert, können diese Container nun wiederverwendet werden:

```javascript
var preis1 = 9;
var preis2 = 6;
var total = preis1 + preis2;
console.log(total);
```

Die Wahl des Variablennamen ist einem freigestellt. Einzig folgende Wörter dürfen nicht verwendet werden:

```js
abstract arguments  boolean  break  byte
case	 catch     char        class      const
continue debugger  default     delete     do
double   else      enum        eval       export
extends  false     final       finally    float
for      function  goto        if         implements
import   in        instanceof  int        interface
let      long      native      new        null
package  private   protected   public     return
short    static    super       switch     synchronized
this     throw     throws      transient  true
try      typeof    var         void       volatile
while    with      yield
```
**JavaScript unterscheidet zwischen Gross- und Kleinschreibung**: Aa, aa, AA und aA bezeichnen unterschiedliche Variablen!

Arithmetik versus Zeichenketten aneinanderhängen

```javascript
var x = 5 + 2 + 3;
var x = "Hello" + " " + " world!";

// achtung beim aneinanderhaengen von Zahlen und Zeichen!
var x = "5" + 2 + 3;
```

Multiplikation, Subtraktion, etc

```javascript
var x = 5;
var y = 2;
var z = x * y;
console.log(z);
```
##### Inline JS versus externem file

Dieser Block kann innerhalb einer HTML Seite an einem beliebigem Ort eingefügt werden.
```javascript
<script type="text/javascript">
  window.alert("test");
</script>
```

Übersichtlicher ist es aber, den Javascript Code in einem JS File abzuspeichern und es aus dem HTML File aufzurufen (hier haben wir den Javascript Code in einem index.js gespeichert):

```javascript
<script type="text/javascript" src="js/index.js"></script>
```

##### Funktionen
Eine JavaScript-Funktion ist ein Codeblock, um eine bestimmte Aufgabe (meist repititve) auszuführen.

Eine JavaScript-Funktion wird erst ausgeführt, wenn man sie direkt aufruft (achtung Gross/Kleinschreibung). Die zwei Variablen in den Klammern nennt man Parameter. Möchte man die Funktion aufrufen, muss man immer exakt dieselbe Anzahl an Parametern übergeben.

Eine JavaScript - Funktion wird mit dem Schlüsselwort **function**, gefolgt von einem Namen, gefolgt von Klammern () erstellt.

Funktionsnamen können Buchstaben, Ziffern Unterstrichen enthalten (gleichen Regeln wie Variablen).

Die Klammern können durch Komma getrennte Parameternamen enthalten:
( Parameter1, Parameter2, ... )

Der Code welcher durch Funktion ausgeführt werden soll, ist in geschweiften Klammern gesetzt: {}

```javascript
function meineFunktion(p1, p2) {
    return p1 * p2; // Gibt die Multiplikation von p1 und p2 zurück
}

var ergebnis = meineFunktion(3,9);
console.log(ergebnis);
console.log(meineFunktion(4,4));
```

Versuche eine Funktion zu erstellen, die Celsius in Fahrenheit umwandelt und/oder umgekehrt.

##### Funktionen Scopes

Variablen, die innerhalb einer Funktion deklariert werden, sind lokale Variablen.

Lokale Variablen haben einen lokalen Gültigkeitsbereich -> Sie können nur innerhalb der Funktion zugegriffen werden.

```javascript
// code here can not use carName

function myFunction() {
    var carName = "Tesla";
    console.log(carName);
    // code here can use carName

}
```

Globale Variablen sind Variablen, die ausserhalb einer Funktion deklariert werden. Eine globale Variable hat globale Reichweite: Alle Skripten und Funktionen einer Webseite können auf sie zugreifen.

```javascript
var carName = "Tesla";

// code here can use carName

function myFunction() {

    // code here can use carName

}
```

##### Kontroll Strukturen

Wie in anderen Sprachen, kann man in Javascript bedingte Anweisungen (if elseif etc.), sowie verzweigte Anweisungen und Schleifen (Loops) sehr einfach erstellen.

Hier eine kurze Auswahl an gebräuchlichen Kontrollstrukturen:

###### Bedingte Anweisung if

```javascript
var isIpad = true;
if (isIpad == true) {
  // your code here
}
else {
  // wenn variable nicht true ist
}
```
###### Verzweigte Anweisung switch

```javascript
var text = "pizza";

switch (text) {
  case "napoli":
    console.log("napoli + mozzarella");
  break;
  case "rucola":
    console.log("vegetarian rucola");
  break;
  case "margharita":
    console.log("cheapest");
  break;
}
```

###### For Schleifen
```javascript
for (var i=0; i<10; i++) {
  console.log(i);
}
```

###### while Schleifen

```javascript
var i = 0;
while (i<10) {
  console.log(i);
  i = i + 1;
}
```

#### Tools
 - [Atom text editor](https://atom.io)
 - [Grunt](https://gruntjs.com/)
 - [NodeJs](https://nodejs.org/en/)
 - [Htmlshell](http://htmlshell.com/)
 - [Initalizer](http://www.initializr.com/)
 - [ish by Brad Frost](http://bradfrost.com/demo/ish/)

#### Weiterführende Links
 - [JS intro w3schools](https://www.w3schools.com/js/default.asp)
 - [Javascript Book](http://javascriptbook.com/)
 - [Frontend developer handbook](https://www.frontendhandbook.com/)
 - [You don't know JS](https://github.com/getify/You-Dont-Know-JS)
 - [Programming Design Systems Buch](https://programmingdesignsystems.com/introduction/)
 - [Two JS book recommendations](https://tommcfarlin.com/recommended-javascript-books/)

#### Aufgabe

Erzeuge die Variable, damit der untenstehende Code ausgeführt werden kann.
```
<p id="demo">Display the result here.</p>

<script>
// Create the variables here
document.getElementById("demo").innerHTML =
firstName + " " + lastName + " is " + age;
</script>
```

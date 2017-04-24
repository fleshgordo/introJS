### Einführung JS

#### Javascript Syntax

##### Statements

Ein Computerprogramm ist eine Liste von „Anweisungen“ die durch den Computer ausgeführt werden.

In einer Programmiersprache nennt man diese Programmanweisungen Aussagen/Statements.

JavaScript ist eine (interpretierte) Programmiersprache (sie wird nicht kompiliert so wie z.B. C).

JavaScript - Statements werden durch Semikolons getrennt.

```
var x, y, z;
x = 5;
y = 6;
z = x + y;
```
##### Kommentare

Nicht alle JavaScript-Anweisungen werden „ausgeführt“.

Code nach doppelten Schrägstrichen // oder zwischen / * und * / wird als  Kommentar behandelt.

Kommentare werden ignoriert und nicht ausgeführt:
```
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
/*
```
##### Variablen

JavaScript Variablen sind Container für Datenwerte zu speichern.

```
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
```

Einmal als Variable gespeichert, können diese Container nun wiederverwendet werden:

```
var preis1 = 9;
var preis2 = 6;
var total = preis1 + preis2;
console.log(total);
```

Arithmetik versus Zeichenketten aneinanderhänderungen

```
var x = 5 + 2 + 3;
var x = "Hello" + " " + " world!";

// achtung beim aneinanderhaengen von Zahlen und Zeichen!
var x = "5" + 2 + 3;
```

Multiplikation, Subtraktion, etc

```
var x = 5;
var y = 2;
var z = x * y;
console.log(z);
```

#### Weiterführende Links
[JS intro w3schools](https://www.w3schools.com/js/default.asp)

#### Aufgaben

Erzeuge die Variable, damit der untenstehende Code ausgeführt werden kann.
```
<p id="demo">Display the result here.</p>

<script>
// Create the variables here

document.getElementById("demo").innerHTML =
firstName + " " + lastName + " is " + age;
</script>
```

# Task Runner + Server

## Lokaler Server

Die einfachste Möglichkeit euren Computer in einen Server zu verwandeln ist einen kleinen Webserver über den Terminal zu starten. Dazu müsst ihr den Terminal öffnen, ins jeweilige Verzeichnis wechseln (mit dem **cd** Kommando). Verwendet die Tab-Taste (Tabulator) zum Auto-vervollständigen. Um das aktuelle Verzeichnis auf den Schreibtisch zu ändern, tippt man:

```
cd Desktop
```

Danach startet man den Server:
```
python -m SimpleHTTPServer
```

Dies kreirt einen lokalen Server (auf dem Port 8000) und ihr könnt im Browser folgende Adresse eingeben:

```
http://localhost:8000
```

Findet nun heraus welche IP Adresse euer Rechner hat und ändert die Adresse im Webbrowser dementsprechend:

```
http://192.168.1.66:8000
```

Falls euer Smartphone im selben Netzwerk verbunden ist, dann könnt ihr es auch von dort aus probieren.

Falls ihr einen anderen Port wünscht, könnt den Server auch so starten:

```
python -m SimpleHTTPServer 8080
```

Mit der Tastenkombination **CTRL-C** kann man den Server stoppen.

## Taskrunners

Mit dem Aufkommen von immer mehr Requirements an Frontend-Code und standardisierten Verfahren kommt es in der Entwicklung von Websiten sehr häufig zu repetitiven Aufgaben. Ihr habt es wahrscheinlich schon selbst gemerkt wie mühsam es ist, ständig ein "frisches" index.html zu schreiben, die Ordner für CSS/JS und für Bilder anzulegen, etc.

Sogenannte Javascript Task Runner, wie z.B. [Gulp](http://gulpjs.com/) oder [Grunt](https://gruntjs.com/) sind so etwas wie die heimlichen Helfer vieler Web-Developer. Wie bei vielen anderen Entwicklungen bei Web-Technologien, gibt es für diese Taskrunner auch einen Haufen an Tools und jedes Jahr einen neuen Trend. Mittlerweile wird das hier vorgestellte Gulp von [Broccoli](http://broccolijs.com/), [webpack](https://webpack.js.org/) oder einfach nur [npm Skripten](https://docs.npmjs.com/getting-started/what-is-npm) abgelöst. Was mir dabei wichtig ist, dass man das Prinzip dieser Tools verstehen soll und dabei ist es egal mit welchen man von diesen Tools anfängt. Das Prinzip bleibt gleich, einzig die Syntax ändert sich.

### Gulp

#### Installation von nodejs

Geht auf folgende [Seite](https://nodejs.org/en/) und lädt das pkg File für euer Betriebssystem herunter (am besten die Version "recommended for most users"). Nach der erfolgreichen Installation, öffnet einen Terminal und tippt:

```
node -v
```

Ihr solltet sowas ähnliches sehen, wie:

```
#~ node -v
v6.7.0
```

Falls ihr folgende Meldung bekommt, dann hat die Installation nicht geklappt:

```
bash: command not found: node
```

#### Installation von gulpjs

Gulp kann man über den Packet-Manager von nodejs installieren. Das Kommando im Terminal heisst diesbezüglich *npm*. Führt bitte beide Kommandos jeweils einzeln aus.

```
npm config set prefix /usr/local
```

```
sudo npm install gulp –g
sudo npm install yo -g 
```

Das -g nennt man Flag und bedeutet das gulp "global" installiert werden soll. Der zweite Befehl installiert [yeoman](http://yeoman.io/), ein weiteres Tool, welches unsere Arbeit erleichtern soll.
Es gibt einen Haufen an sogenannten Generatoren für Yeoman. Wir sehen uns zunächst nur den Web Generator an. Wie auch alles andere, muss man diesen zunächst erst installieren.

```
sudo npm install -g generator-webapp
```

Mit dem Befehl **yo doctor** könnt ihr überprüfen, ob alles geklappt hat.

Nun versucht im Terminal den Ordner auf den Desktop zu wechseln.

```
cd Desktop
```

Wir erstellen ein neues Verzeichnis (diesmal anstatt im Finder "New folder" zu klicken). Mit dem Kommando mkdir erstellt man ein neues Verzeichnis

```
mkdir memyself
```

Und mit **cd** wechselt man wieder in das Verzeichnis

```
cd memyself
```

Jetzt können wir unser erstes Web Projekt automatisiert erstellen lassen

```
yo webapp
```

Ihr könnt auswählen, welche Elemente in euer Webprojekt bereits vorinstalliert werden soll. Wir bestätigen zunächst einfach mit **Enter**. Nächste Frage nochmal **Enter** (Mehr über [TDD BDD](http://joshldavis.com/2013/05/27/difference-between-tdd-and-bdd/)). Nochmals **Enter**

Danach werden verschieden *Dependencies* installiert und nach kurzer Zeit ist das Projekt startklar.

Wenn ihr im selben Folder nochmal ein **ls** schreibt, dann solltet ihr diese Files und Folder sehen
```
app              bower_components node_modules     test
bower.json       gulpfile.js      package.json
```

Im selben Terminal-Fenster tippt diesen Befehl:

```
gulp serve
```

Der Parameter "serve" startet den Live-Server und einige andere Helpers. Ein Web-Browser Fenster sollte sich automatisch öffnen. Falls nicht, im Terminal steht auch die Adresse von eurem lokalen Development-Server, wie z. B.:

```
Local: http://localhost:9000
External: http://192.168.178.36:9000
```

Die Source-Files von dem Webprojekt liegen im Folder **app**. Dieser sieht so aus:

```
apple-touch-icon.png images               scripts
favicon.ico          index.html           styles
fonts                robots.txt
```

Der Folder **app** ist sozusagen der Ort wo man die Source Files zum Projekt hat. Sobald man im Terminal folgendes tippt,

```
gulp build
```

wird ein **dist** (Abkürzung für Distribution) Folder erstellt, wo u. a. die Bilder komprimiert werden, das SASS file in ein einziges CSS File "kompiliert" wird, genauso wie alle Javascript Files komprimiert und minifiziert werden. Typischerweise wird der dist Folder dann automatisiert auf den Fileserver hochgeladen.

### Live Server

Der Live Server überwacht eure Source Files und nach jedem Mal speichern, führt dieser automatisch einen Browser-Referesh durch.

### SASS

SASS steht für Syntactically Awesome Stylesheets. Es ist eine Meta-Sprache für CSS. Der Vorteil von SASS liegt in den zusätzlichen Features die es mit sich bringt, unter anderem Variablen und [Mixins](https://scotch.io/tutorials/how-to-use-sass-mixins). Diese verkleinern den selbst geschrieben Code und ermöglichen vor allem eine saubere und einfache Verwaltung. Mit SASS kann man z. B. Variablen verändern, was bei einem grossen Projekt die Verwaltung des Codes extrem vereinfacht. SASS wird in scss Files gespeichert. Ein klassische Anwendung ist das Speichern von Farben in Variablen. Mehr Anwendungen gibts [http://sass-lang.com/guide](hier).

```
$primary-color = "#ccc"
```

Danach könnt ihr diese Variable innerhalb des gesamten Projektes verwenden:

```
body {
  background-color: $primary-color;
}
```

Der "kompilierte" CSS Code würde dann so aussehen:

```
body {
  background-color: #ccc;
}
```

Wie ihr eventuell bereits gesehen habt, ist der CSS Code (von Animationen z. B.) für verschiedene Browser anders bzw. man muss [Vendor-Prefixes](http://shouldiprefix.com/) verwenden. Man schreibt häufig folgendes:

```
-webkit-transition: all 4s ease;
-moz-transition: all 4s ease;
-ms-transition: all 4s ease;
-o-transition: all 4s ease;
transition: all 4s ease;
```  

Mixin sind vorbereitete Funktionen und können einfach in eurer scss File hinzugefügt werden.

```
@mixin transition($transition...) {
    -moz-transition:    $transition;
    -o-transition:      $transition;
    -webkit-transition: $transition;
    transition:         $transition;
}
```

Danach kann die mixin Funktion im scss File schreiben (hier wird für ein div mit der Klasse "one" die Hintergrundfarbe verändert):

```
div.one {
  @include transition(background-color 1s);
}
div.one:hover {
  background-color: blue;
}
```

Der SASS Prozessor verwandelt euer File dann automatisch in diesen CSS Code:
```
div.one {
  -moz-transition: background-color 1s;
  -o-transition: background-color 1s;
  -webkit-transition: background-color 1s;
  transition: background-color 1s;
}
```

### Bower

[Bower](https://bower.io/) ist ein Paketmanager. Im Unterschied zu Gulp geht es bei Bower nicht um die Automatisierung der Abarbeitung von Aufgaben, sondern um die automatisierte Verwaltung von JavaScript Bibliotheken. Bower ist ebenfalls ein Node.js Modul und benötigt wie Gulp eine Konfigurationsdatei, in diesem Fall ein „Bower File“ (bower.json), in dem alle Anweisungen stehen. Bei einer Website bestehen im Frontend Bereich meistens Abhängigkeiten zu bestimmten JavaScript Bibliotheken und Frameworks wie Bootstrap.

Anstatt das zip File von einer z. B. jQuery Bibliothek von der Seite des Entwicklers herunterzuladen, verwaltet Bower die Installation diverser Bibliotheken über das Kommandozeilen-Interface.

Man kann seinem Projekt einfach über dieses Kommando jQuery hinzufügen. Es lädt die neueste Version aus dem Web und speichert diese automatisch im js Folder.

```
bower install jquery
```

Man kann nach Bibliotheken suchen, wie z. B.:

```
bower search parallax
```

In der [Anleitung](https://bower.io/docs) zu Bower findet man noch viel mehr Kommandos.

Bower wird aber langsam von npm, [webpack](https://webpack.js.org/) und [browserify](http://browserify.org/) verdrängt. Liest [hier](https://github.com/bower/bower/issues/2298) weshalb Bower nach wie vor verwendet wird.

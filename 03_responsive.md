# Einführung Responsive + Parallax

## Responsive

Responsive Webdesign ist eine Technik, welche es ermöglicht mit Hilfe von CSS Media-Queries (teilweise auch mittels JS) das einheitliche Anzeigen von Inhalten auf einer Website zu gewährleisten. Das Layout einer Website wird so gestaltet, dass dieses entweder auf Desktop, Tablet oder Smartphone eine konsistente Erscheinung bietet. Der Inhalt der angezeigten Webseiten kann dabei je nach Bildschirmgrösse varieren.

Standard-Auflösung von Smartphones, Computer und Tablets:

 - Smartphones: 320px bis 480px
 - Tablets: 768px bis 1024px
 - Computer-Desktop: 1024px+

Auf dieser [Seite](https://mediaqueri.es/) kann man das Aussehen von verschiedenen Webseiten beobachten.

Prinzipiell muss man drei Bestandteile für ein responsive Design identifizieren:

  - Ein flexibles Layout Grid
  - Media Queries
  - Flexible Bilder und Videos

In dem Essay von [John Allsopp](https://alistapart.com/article/dao) (2000) beschreibt er die neue Herausforderung an Designer für das neue Medium "Web" zu gestalten.

> The control which designers know in the print medium, and often desire in the web medium, is simply a function of the limitation of the printed page. We should embrace the fact that the web doesn’t have the same constraints, and design for this flexibility. But first, we must “accept the ebb and flow of things.”


Dieser Gedanke ist selbst nach 17 Jahren noch aktuell, wenn wir uns vergegenwärtigen wieviele verschiedene Auflösungen und Bildschirmgrössen heutzutage exisitieren.

![Screen resolutions](http://1.bp.blogspot.com/-4c1PCfJfRbA/URznMZ93SCI/AAAAAAAAKZ4/IxgOTPbryTk/s1600/Aram+Bartholl+TRIANGULATION+03.jpeg)*[Graphic Arrays](http://datenform.de/graphic-arrays.html), Collage by Aram Bartholl, 2013*

#### Layout Grid

Viele Webseiten basieren auf einer Raster Ansicht, welche die Seite in Spalten unterteilt. Ein Raster hat oft 12 Spalten und eine Gesamtbreite von 100%. Es kann schrumpfen und erweitert werden je nach Browser-Fenster-Grösse.

Nehmen wir an, wir arbeiten mit 12 Spalten so ergibt sich eine Rastereinteilung von:

```
100% / 12 Spalten = 8,33%
```

Das CSS würde dann so aussehen:

```
.col-1 {width: 8.33%;}
.col-2 {width: 16.66%;}
.col-3 {width: 25%;}
.col-4 {width: 33.33%;}
.col-5 {width: 41.66%;}
.col-6 {width: 50%;}
.col-7 {width: 58.33%;}
.col-8 {width: 66.66%;}
.col-9 {width: 75%;}
.col-10 {width: 83.33%;}
.col-11 {width: 91.66%;}
.col-12 {width: 100%;}
```

Man sollte noch das Attribute float:left zu allen Spalten hinzufügen, damit sie aneinandergereiht werden:

```
[class*="col-"] {
    float: left;
    padding: 15px;
    background: #ccc;
}
```

Für die Reihe benötigen wir noch folgende CSS Regel:

```
.row::after {
    content: "";
    clear: both;
    display: table;
}
```

Und zuallerletzt stellen wir der Regel *box-sizing* sicher, dass das die Grösse von Elementen immer die gesamte Breite und Höhe der Elemente enthalten (i. e. es wird das Padding miteinberechnet. Früher war dies nicht der Fall. Mehr Infos [hier](https://www.w3schools.com/css/css3_box-sizing.asp)).

```
* {
    box-sizing: border-box;
}
```

##### Media Queries

Mediaqueries ist eine CSS-Technik, die mit CSS3 eingeführt worden ist. Mit Hilfe von Mediaqueries kann man steuern, wie einzelne Elemente bei verschiedenen Auflösungen angezeight werden, z. B.: wenn das Browserfenster kleiner als 800px ist, wird die Hintergrundfarbe geändert:
```
@media only screen and (max-width: 800px) {
    body {
        background-color: pink;
    }
}
```  

Media Queries werden von allen modernen Browser unterstützt. Viele Seiten müssen leider nach wie vor kompatibel mit dem Internet Explorer 8 sein, weshalb einem die Bibliothek [respond.js](https://github.com/scottjehl/Respond) hilfreich sein kann.

In unserem Beispiel mit dem Raster würde man dann beispielsweise die Breite jeder Spalte auf 100% vergrössern, wenn ein Smartphone auf die Seite zugreift:

```
@media only screen and (max-width: 768px) {
    /* For mobile phones: */
    [class*="col-"] {
        width: 100%;
    }
}
```

Man kann aber noch viele weitere Parameter per Media Queries abfragen, wie z.B. die Orientierung des Screens (landscape oder portrait)

```
@media only screen and (orientation: landscape) {
    body {
        background-color: pink;
    }
}

```

Diese Parameter kann man nun auch miteinander verbinden:

```
@media screen and (min-device-width: 480px) and (orientation: landscape) { … }
```

Ein weitere wichtige Erweiterung mit dem Aufkommen von Smartphone Browsern war, dass der Browser Zoom und die tatsächliche Grösse des Smartphone Screens je nach Seite stark varieren. Das Darstellungsfeld variiert mit dem Gerät, und wird auf einem Mobiltelefon kleiner sein als auf einem Computerbildschirm. Über einen Meta Tag in der <head> Section kann man dies aber kontrollieren. Typischerweise sollte eure Seite folgendes beinhalten:

```
<meta name="viewport" content="initial-scale=1.0, width=device-width" />
```

##### Druckversion

Mediaqueries kann man aber auch für die Druckansicht einer Seite verwenden. Hier werden zum Beispiel Header, Footer und Navigation für die Druckansicht ausgeblendet:

```
@media print {
 /* All your print styles go here */
 #header, #footer, #nav { display: none !important; }
}
```

Der "old-way" dies zu tun war über ein seperates CSS File
```
<link href="/print.css" rel="stylesheet" media="print" type="text/css" />
```

Das muss man aber nicht mehr tun. Seht euch die Sektion *Print Styles* vom [HTML5 Boilerplate](https://github.com/h5bp/html5-boilerplate/blob/master/src/css/main.css) mal genauer an.

#### Bilder

Für Bilder ist es hilfreich die *max-width* Regel anzuwenden. Die Bildgrösse wird automatisch proportional umgerechnet.

```
img {
    max-width: 100%;
    height: auto;
}
```

Man kann diese Regel aber auch auf Video Objekte anwenden:

```
img,
embed,
object,
video {
  max-width: 100%;
}
```

#### Beste Vorgehensweise im Responsive Design?

Es gibt verschiedene Stimmen, die behaupten man muss mittlerweile das Webdesign immer mit dem Fokus "mobile First" gestalten und programmieren. Die Realität ist, dass es keine allgemeine Formel gibt, sondern dass man je nach Projekt immer abschätzen muss welche Technologie/Methodologie besser geeignet wäre.

Brad Frost hat eine sehr reiche Übersicht zu dem Thema [Responsive Design](http://bradfrost.com/demo/ish/) zusammengestellt.

Im Kapitel 4 gibt es noch mehr Infos zu Best Practices.


## Parallax

Diesen Effekt trifft man häufig in modernen Webseiten auf und er geht zurück auf die [Mehrfachebenen-Kamera](https://www.youtube.com/watch?v=YdHTlUGN1zw) von Disney Studios in 1937. Durch die Verschiebung einzelner Elemente wird der Eindruck von Räumlichkeit verstärkt. Im Internet ist dieser Effekt vorwiegend als Parallax bekannt. Als Parallaxe bezeichnet man die scheinbare Änderung der Position eines Objektes, wenn der Beobachter seine eigene Position verschiebt.

Hier eine kurze Übersicht von Seiten wo dieser Effekt eingesetzt wird:

  - [Klassisches Beispiel von Parallax mit CSS](http://www.cssscript.com/demo/pure-css-parallax-scrolling-effect/)
  - [10 years Intacto](http://www.intacto10years.com/index_start.php)
  - [The boat](http://www.sbs.com.au/theboat/)
  - [Firewatch](http://www.firewatchgame.com/)

Parallax wird auch oft in sogenannten "One-page" Webseiten eingesetzt. Hier ein paar Beispiele zu interessanten Projekten, die mit der Idee eines "langen" Scroll experimentieren (Hinweis: Diese Beispiele verwenden meist nur einen Scrolling Effekt, sprich kein Parallax):

  - [NASA prospect](http://nasaprospect.com/)
  - [Every last drop](http://everylastdrop.co.uk/)
  - [Atlantis](http://www.lostworldsfairs.com/atlantis/)
  - [James Bond vehicles](http://www.evanshalshaw.com/more/bondcars/)
  - [Gradient's motherfucker](http://prinzhorn.github.io/skrollr/examples/gradientsmotherfucker.html)

### Parallax.js

Parallax.js ist eine jQuery Library mit welcher man den Gyroscope eines Smartphones den Parallax Effekt steuern kann. Wenn parallax.js keine Accelerometer Sensor findet, dann wird die Animation einfach über die Mausposition gesteuert.

Besuche folgende [Seite](http://saloneludico.ch) und sehe Dir das obere Logo auf dem Smartphone und auf dem Desktop an. Hier werden vier verschiedene Ebenen (SVG Files) übereinandergelagert.

Die Implementierung ist sehr einfach. Zunächst muss die Bibliothek im richtigen Ordner liegen und vom index.html referenziert werden:

```
<script src="js/jquery.parallax.min.js"></script>
```

Danach muss man im HTML Code vier (oder mehrere) Layer definieren:

```
<div id="scene">
  <div class="layer" data-depth="0.00"><img src="layer1.png"></div>
  <div class="layer" data-depth="0.20"><img src="layer2.png"></div>
  <div class="layer" data-depth="0.40"><img src="layer3.png"></div>
  <div class="layer" data-depth="0.60"><img src="layer4.png"></div>
</div>
```

Und im Javaskript File fügt man folgendes hinzu:

```
$(document).ready(function () {
 var $scene = $('#scene').parallax();
 $scene.parallax('scalar', 0, 50);
 $scene.parallax('enable');
});
```

Mehr Infos gibts [hier](https://github.com/wagerfield/parallax).

### Stellar.js

Es gibt eine Vielzahl von Plugins und Bibliotheken. [Stellar.js](http://markdalgleish.com/projects/stellar.js/) ist eine Bibliothek, die eine jede Menge an Einstellungsmöglichkeiten für den Parallax Effekt anbietet.

### Skrollr

Es lohnt sich auch einen Blick auf die Beispiele von [Skrollr](https://github.com/Prinzhorn/skrollr/tree/master/examples#examples) zu werfen. Man kann damit sogar SVG Pfade über den Skroll animieren.

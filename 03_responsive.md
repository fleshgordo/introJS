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

```
  The control which designers know in the print medium, and often desire in the web medium, is simply a function of the limitation of the printed page. We should embrace the fact that the web doesn’t have the same constraints, and design for this flexibility. But first, we must “accept the ebb and flow of things.”
```

Dieser Gedanke ist selbst nach 17 Jahren noch aktuell, wenn wir uns vergegenwärtigen wieviele verschiedene Auflösungen und Bildschirmgrössen heutzutage exisitieren.

![Screen resolutions](http://1.bp.blogspot.com/-4c1PCfJfRbA/URznMZ93SCI/AAAAAAAAKZ4/IxgOTPbryTk/s1600/Aram+Bartholl+TRIANGULATION+03.jpeg)*[Graphic Arrays](http://datenform.de/graphic-arrays.html), Collage by Aram Bartholl, 2013*

#### Layout Grid

Viele Webseiten basieren auf einer Raster Ansicht, was bedeutet, dass die Seite in Spalten unterteilt sind. Ein Raster hat oft 12 Spalten und eine Gesamtbreite von 100%. Es kann schrumpfen und erweitert werden je nach Browser-Fenster-Grösse.

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

##### Media Queries

Mediaqueries ist eine CSS-Technik, die mit CSS3 eingeführt worden ist. Mit Hilfe von Mediaqueries kann man steuern, wie einzelne Elemente bei verschiedenen Auflösungen angezeight werden, z. B.: wenn das Browserfenster kleiner als 800px ist, wird die Hintergrundfarbe geändert:
```
@media only screen and (max-width: 800px) {
    body {
        background-color: pink;
    }
}
```  

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

Ein weitere wichtige Erweiterung mit dem Aufkommen von Smartphone Browsern war, dass man den Browser Zoom und die tatsächliche Grösse des Smartphone Screens über einen Meta Tag in der <head> Section einer Seite kontrollieren konnte. Typischerweise sollte eure Seite folgendes beinhalten:

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

#### Beste Vorgehensweise?

Es gibt verschiedene Stimmen, die behaupten man muss mittlerweile das Webdesign immer mit dem Fokus "mobile First" gestalten und programmieren. Die Realität ist, dass es keine allgemeine Formel gibt, sondern dass man immer abschätzen muss

Brad Frost hat eine sehr reiche Übersicht zu dem Thema [Responsive Design](http://bradfrost.com/demo/ish/) zusammengestellt.

Im Kapitel 4 gibt es noch mehr Infos zu Best Practices.


## Parallax

Diesen Effekt trifft man häufig in modernen Webseiten auf und er geht zurück auf die [Mehrfachebenen-Kamera](https://www.youtube.com/watch?v=YdHTlUGN1zw) von Disney Studios in 1937. Durch die Verschiebung einzelner Elemente wird der Eindruck von Räumlichkeit verstärkt. Im Internet ist dieser Effekt vorwiegend als Parallax bekannt. Als Parallaxe bezeichnet man die scheinbare Änderung der Position eines Objektes, wenn der Beobachter seine eigene Position verschiebt.

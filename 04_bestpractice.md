## Anleitung zu einigen "best practices" im Web


### File und Ordnerstruktur

Um einen guten Überblick über die einzelnen Files zu eurem Projekt zu bewahren, legt euch diese Ordnerstruktur an:

```
/       -> Stammverzeichnis (hier liegt das index.html)
/js     -> Verzeichnis für alle JavaSkript Files
/css    -> Alle CSS Files hier ablegen
/img    -> Bilder hier
```

Achtet dann darauf die entsprechenden Files dann richtig verlinkt werden, sprich:

```
<link rel="stylesheet" href="css/main.css">
<script src="js/main.js" type="text/javascript">
```

### Mischen von CSS, HTML und JS

CSS Code direkt im HTML ist keine gute Idee und trägt nicht wirklich zur Lesbarkeit bei. Vermeidet folgendes:

```
<a href="http://www.catswhocode.com" style="background:#069;padding:3px;font-weight:bold;color:#fff;">Cats Who Code</a>
```

Und schreibt keinen Javascript im HTML (auch wenn es möglich ist)

```
<a id="cwc" href="http://www.catswhocode.com" onclick="alert('I love this site!');">Cats Who Code</a>
```

Derselbe Code würde mit jQuery folgendermassen aussehen:

```
$(document).ready(function() {
  $('#cwc').click(function() {
    alert('I love this website');
  });
});
```
### HTML

Setze immer einen Doctype und das korrekte Character Encoding

```
<!doctype html>
```

```
<meta charset="UTF-8">
```


### Platzierung von Javascript Code

Legt sämtliche Javaskript Files die ihr zusätzlich lädt an das untere Ende von eurem HTML Code:

```
...
   <script type='text/javascript' src='jquery.js?ver=1.3.2'></script>
 </body>
</html>
```

### Optimisiere Bilder

Tools wie [Imageoptim](https://imageoptim.com/) helfen Bilder fürs Web zu optimieren.

### Validierung

Es gibt verschiedene Tools, um zu checken ob die eigene Seite den Standards entspricht und ob die Performance im Vergleich gut ist. Hier eine kleine Auflistung:

  - [w3 validator](https://validator.w3.org/)
  - [Google Page Speed Tools](https://developers.google.com/speed/pagespeed/)
  - [Webpagetest](https://www.webpagetest.org/)
  - [Can i use?](http://caniuse.com/)
  - [Browserstack Cross-browser testing](https://www.browserstack.com/)

### Lerne von Profis

Grosse Firmen mit aufwändigem Frontend-Design veröffentlichen ihre Best practices teilweise, wie z. B.

  - [Front End Tips @ Gitbook](https://www.gitbook.com/book/znack/front-end-tips/details)
  - [Good HTML practices to follow](http://sixrevisions.com/web-standards/20-html-best-practices-you-should-follow/)
  - [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)
  - [Standards for developing flexible, durable, and sustainable HTML and CSS](http://codeguide.co/)

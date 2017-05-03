# Task Runner + Server

Die einfachste Möglichkeit euren Computer in einen Server zu verwandeln ist einen kleinen Webserver über den Terminal zu starten. Dazu müsst ihr den Terminal öffnen, ins jeweilige Verzeichnis wechseln (mit dem **cd** Kommando) und dann folgende Zeile eintippen:

```
python -m SimpleHTTPServer
```

Dies kreirt einen lokalen Server (auf dem Port 8000) und ihr könnt im Browser einfach folgende Adresse eingeben:

```
http://localhost:8000
```

Falls ihr einen anderen Port wünscht, könnt den Server auch so starten:

```
python -m SimpleHTTPServer 8080
```

Mit der Tastenkombination **CTRL-C** kann man den Server stoppen.

# 03: Coding Style

Programme können sehr schnell sehr komplex werden.
Daher ist es wichtig, sich an Stil-Regeln zu halten, um sie möglichst
verständlich zu schreiben.

## 1. Selbsterklärend

Code sollte sich so gut wie möglich selbst erklären.
Dazu sind sprechende Variablen-, Funktions-, Klassennamen etc. erforderlich.
Kurze Namen sind nur in kleinen Gültigkeitsbereichen oder bei klarer Bedeutung
(z.B. `i` für for-Schleifen Iteratoren, `y` für vertikale Position) erlaubt.

### 1.1 Kommentare

Kommentare sind in diesem Zusammenhang vorallem zur Strukturierung/Abgrenzung
des Codes empfohlen, und um die
Verständlichkeit zu erhöhen.
Kommentare sollten nicht das Offensichtliche wiederholen (siehe Bild).

![Cat labeled Cat](https://i.redd.it/iuy9fxt300811.png)

Selbstverständlich kann Code zum besseren eigenen Verständnis kommentiert
werden.
Denken Sie aber daran, dass bei Code Änderungen auch die Kommentare mit gepflegt
werden müssen.

## 4. Benennung

Die folgenden Regelungen sind empfohlen und in keinster Weise verpflichtend.

### 4.1 camelCase für Variablen und Funktionen

Variablen- und Funktionsnamen beginnen mit Kleinbuchstaben und folgen der
camelCase Notation, d.h. bei zusammengesetzten
Namen beginnen die Wortteile im Inneren mit einem Großbuchstaben.  
Funktionsnamen beschreiben dabei eine Aktivität (
z.B. `calculateHorizontalPosition()`) oder eine Frage (z.B. `isHit()`).

Gleiches gilt für Attribute und Methoden.

### 4.2 Unterstrich vor formalen Parametern

Formale Parameter folgen dem Variablen-Benennungs-Schema, mit dem Zusatz eines
Unterstriches am Anfang.
(z.B. `moveTo(_x: number, _y: number)`).

### 4.3 PascalCase für Klassen und Interfaces

Die Namen von Klassen und Interfaces beginnen mit einem Großbuchstaben und
folgen sonst der Kamelnotation (also
PascalCase).  
Klassen und Interfaces beschreiben im Normalfall ein bestimmtes Objekt, nicht
eine Gruppe von Objekten.
Dies sollte sich im Namen wiederspiegeln (`Produkt` statt `Produkte`).

### 4.4 Großschreibung für Enumeratoren

Die Namen von Enumerationen und deren Elemente werden durchgehend mit
Großbuchstaben geschreiben. Wortteile werden bei
Bedarf mit Unterstrich getrennt.

## 5. Doppelte und einfache Anführungszeichen

Es empfielt sich, einfache Anführungszeichen `' '` für char und doppelte
Anführungszeichen `" "` für Strings zu verwenden.

## 6. Formatierung

Code ist sinnvoll Formatiert mit Einschüben etc.
Im Regelfall unterstützt VSCode dies Automatisch. Machen Sie Gebrauch von der
automatischen Formatierungsfunktion.

* [Anleitung für IntelliJ](https://www.jetbrains.com/help/idea/reformat-and-rearrange-code.html#reformat_file)
* [Anleitung für Visual Studio Code](https://stackoverflow.com/questions/29973357/how-do-you-format-code-in-visual-studio-code-vscode)
* [Anleitung für Eclipse](https://praxistipps.chip.de/eclipse-autoformat-code-so-gehts_98369)

## 8. "Magische" Zahlen

Der Gebrauch von "magischen" Zahlen sollte vermieden werden. Solange es nicht
extrem offensichtlich ist, wofür eine Zahl
steht (z.B. `Math.pow(x, 5)`), sollte eine Variable (nach den oben genannten
Guidelines) angelegt werden, welcher die
Zahl als Wert zugewiesen wird. So entsteht der Zusammenhang zwischen der
Variablen und ihrer Bedeutung, und der Wert
kann an einer zentralen Stelle angepasst werden.

## 9. Dateinamen und -aufteilung

Dateinamen dürfen keine Leerzeichen oder Umlaute enthalten, sind sonst aber frei
wählbar (s.u. für Einschränkungen). Es
wird empfohlen, die Zeichenwahl auf a-z, A-Z, 0-9 und _ zu beschränken.  
Code kann auf mehrere Dateien aufgeteilt werden, sofern dies sinnvoll
erscheint (z.B. um eine Trennung von Funktion und
Daten zu erreichen). Wenn Klassen verwendet werden, sollte jede ihre eigene
Datei bekommen. Sofern eine Datei eine
bestimmte Klasse enthält, soll die Datei mit dem Namen der Klasse benannt sein.

## 10. Wiederholungen sind schlecht

Code der sich ohne oder nur mit minimalen Änderungen wiederholt, kann in den
allermeisten Fällen besser geschrieben
werden, z.B. über eine Funktion mit Übergabeparametern, oder indem man nur den
geänderten Teil implementiert oder
überschreibt, während der Rest für alles gleich generiert wird.  
Dies hat viele Vorteile: Es macht den Code generell übersichtlicher (und damit
besser verständlich), kürzer, und
wartungsfreundlicher.
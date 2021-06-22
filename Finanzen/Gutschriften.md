# Gegenstand der Maske

In dieser Maske können Überweisungsgutschriften, die in camt54-Dateien als Detallierung zum Kontoauszug geliefert werden, auf die jeweiligen Mitgliedskonten verbucht werden.

# Vorbereitung

Bevor Dateien eingelesen werden sollten einige Anpassungen in den Systemeinstellungen vorgenommen werden.

## Parameter 'GSRegExp'

Mit diesem Parameter wird ein Suchmuster festgelegt, mit dessen Hilfe MIA versucht die Mitgliedsnummer im Verwendungszweck einer Gutschrift zu finden.

Wenn Ihr Verein z. B. Mitgliedsnummern mit 5 und 6 Stellen vergibt sieht das Muster so aus: \[0-9\]{5,6}

Bei 5-stelligen Nummern würde das Muster so aussehen: \[0-9\]{5,5}

MIA versucht eine Gutschrift automatisch zu verbuchen, wenn im Verwendungszweck nur eine Nummer vorkommt, die dem eingegeben Suchmuster entspricht. Wenn es mehrere gibt kann MIA nicht entscheiden, welche davon die Mitgliedsnummer ist und verbucht nichts automatisch.

## Parameter 'GSRegExpMNr'

Wenn Sie ein komplexeres Suchmuster im Parameter GSRegExp angeben, können Sie im Parameter GSRegExpMNr ein Muster angeben, mit dem innerhalb des Ergebisses dessen suchen können, was mit GSRegExp gefunden wurde.

 Ist z. B. in GSRegExp das Muster 'AB\[0-9\]{6,6}CD angegeben, so findet MIA alle 6-stelligen Nummern, die von AB und CD eingerahmt werden. Also z. B. AB123456CD oder AB654321CD. Mit dem Muster \[0-9\]{5,5} in Parameter GSRegExpMNr kann im zweiten Schritt die eigentliche Mitgliedsnummer extrahiert werden.

## Parameter 'GSKonto'

Mit diesem Parameter legen Sie das Konto fest, auf das die Gutschriften verbucht werden sollen. Im Normalfall ist das das Bankkonto, auf das die Gutschriften eingegangen sind.

## Parameter 'GSBuchText'

Mit dem Parameter wird der Buchungstext bestimmt, der in den Mitgliedskonten für die Gutschriften eingetragen wird.

# Einlesen der Dateien

Das Einlesen der Dateien ist [hier](http://des-mia.de/confluence/display/MIA/camt54-Dateien+einlesen) beschrieben.

Verarbeiten der Gutschriften

Nach dem Einlesen einer Datei wird die Verarbeitung automatisch gestartet. In der Spalte Status können Sie den Stand der Bearbeitung einer Datei erkennen:

-   in Bearbeitung – erfolgreich importiertes Dokument wird autom. verarbeitet, eine manuelle Weiterverarbeitung ist momentan nicht möglich
-   aktiv – Dokument wurde erfolgreich importiert und kann manuell weiterverarbeitet werden
-   inaktiv – beim Importieren/Verarbeiten des Dokuments ist ein Fehler aufgetreten, eine Weiterverarbeitung ist nicht möglich
-   abgeschlossen – Verarbeitung abgeschlossen, keine offenen Buchungen mehr
Hier ist die korrigierte Version der README:

# Linux auf einem Mac installieren (Dual Boot)

Um alte Macs wieder auf den Stand der Zeit zu bringen, folgt hier eine Anleitung, wie man bei nicht länger unterstützten Intel-Macs Linux installiert.

## Vorbereitung

Zuerst ist es nötig, in den Recovery-Modus zu gelangen. Dort partitionieren wir die Festplatte und schalten den Integritätsschutz ab, um problemlos Linux installieren zu können.

### Schritt 1: Partitionierung

- Mac starten und sofort Option (Windows-Taste) + R gedrückt halten. Der Mac sollte im Recovery-Modus starten.
- Festplattendienstprogramm starten.

![macOS Recovery Menü](/Bilder/mac-recovery-mode-die-macos-dienstprogramme.png)

- Festplatte auswählen und auf den „Partitionieren“-Button drücken.
- Es öffnet sich ein Fenster, in dem unten links noch ein „Partitionieren“-Button ist. Nachdem dieser gedrückt wurde, gelangt man in die Partitionierungsübersicht.
- Dann die macOS-Partition auswählen und auf das „+“ (unten links) klicken.
- Die neue Partition muss auf FAT (MS-DOS-Dateisystem) formatiert werden.
- Anschließend auf „Anwenden“ klicken.

Die Partition ist jetzt erstellt und das Dienstprogramm kann geschlossen werden.

### Schritt 2: Integritätsschutz deaktivieren

- Das Terminal im „Dienstprogramme“-Reiter auswählen.
- Folgenden Befehl eingeben: `csrutil disable`

![macOS Recovery Terminal öffnen](/Bilder/terminal-in-recovery-mode.png)

Danach sind wir im Recovery-Modus fertig und der Mac kann heruntergefahren werden.

## Linux-Installation

### Schritt 1: Vom Installationsstick booten

- Den Mac starten und sofort die Command-Taste (Alt) gedrückt halten.
- Danach sollte dieses oder ein ähnlich aussehendes Menü auftauchen:

![macOS Recovery Menü](/Bilder/sjod07fjjy5f.jpg)

- Dort das USB-Gerät (EFI-Boot) auswählen.

### Schritt 2: Installation

Diese ist bei vielen Distributionen unterschiedlich, das ist aber nicht schlimm, da nur die Festplattenformatierung in der Installation eine Rolle spielt. Da es in Pop_OS am einfachsten ging und auf viele komplizierte Menüs verzichtet wird, eignet sich diese Distribution am ehesten zur Demonstration.

### Schritt 2.1: Festplatte partitionieren

- Der grafische Einrichtungsassistent ist in den meisten Fällen selbsterklärend. Diesem also einfach folgen, bis man an den Punkt gelangt, an dem gefragt wird, wo und wie installiert werden soll.
- Meistens gibt es zwei Optionen: „Alles löschen und Linux installieren“ oder „Benutzerdefiniert“ (Custom, Advanced, etc.).
- Da wir einen Dual Boot möchten, müssen wir die benutzerdefinierte Installation wählen.

![Pop_OS Festplatte partitionieren "Benutzerdefiniert"](/Bilder/Linux%20Part%201.png)

- Daraufhin auf „Partitionen verwalten“ klicken, dann öffnet sich ein GParted-Fenster.

![GParted](/Bilder/Linux%20Part%202.png)

- Dort die vorhin erstellte Partition in der Liste auswählen und löschen (Rechtsklick).
- Dann Rechtsklick auf den nicht zugeordneten Speicher und auf „Neu“ klicken. Da entsteht eine Partition für den Bootloader, diese darf **mindestens 500 MB** groß sein und muss auf **FAT32** formatiert werden.

![Boot-Partition](/Bilder/Linux%20Part%203.png)

- Dasselbe nochmal für das eigentliche Betriebssystem: Die Größe kann hier frei gewählt werden, es sollten aber noch ca. **4–8 GB** übrig bleiben. Das Ganze muss in **ext4** (oder dem von der Distro vorgeschlagenen Hauptdateisystem) formatiert werden.

![Root-Partition](/Bilder/Linux%20Part%204.png)

- Die letzte zu erstellende Partition ist der Auslagerungsspeicher (falls der RAM voll ist). Den **restlichen Speicher** nutzen und als **Swap** formatieren.

![Swap-Partition](/Bilder/Linux%20Part%205.png)

- Zum Abschluss sollte die Liste so aussehen:

![GParted Übersicht mit allen Partitionen](/Bilder/Linux%20Part%206.png)

- Die Konfiguration muss mit dem Haken bestätigt werden, erst dann werden die Änderungen wirksam. Man kann also vorher noch nichts kaputt machen.

- Im letzten Schritt der Partitionierung müssen alle drei Partitionen einzeln ausgewählt und wie in den Bildern konfiguriert werden.

![Boot einhängen](/Bilder/Linux%20Part%207.png)

![Root einhängen](/Bilder/Linux%20Part%208.png)

![Swap einhängen](/Bilder/Linux%20Part%209.png)

- Danach „Löschen und Installieren“ anklicken und dem Installationsassistenten folgen, bis das System installiert und bereit für den Neustart ist.

## Es ist geschafft

Das System muss jetzt nur noch neu gestartet werden. Beim Neustart die Command-Taste (Alt) gedrückt halten und die Festplatte mit EFI-Boot auswählen.

Über das Menü, das auftaucht, kann beim Starten jetzt immer zwischen Linux und macOS gewechselt werden.

## Anmerkungen zur Doku

### Outdated

Diese Doku wurde zuletzt 2022 von mir bearbeitet und ist daher bestimmt nicht mehr allzu aktuell. Zudem hat sich unter Pop_OS über die Jahre auch einiges geändert. Das Grundprinzip funktioniert aber dennoch auf allen Intel-basierten Maschinen und für alle Distros.

### Mein Mac geht nicht mehr an oder fährt nicht herunter

Ich habe bei einer kurzen Recherche herausgefunden, dass Linux wohl Probleme mit dem Hoch- und Herunterfahren auf Apple-Geräten hat. Manchmal startet das System neu, obwohl man auf „Herunterfahren“ klickt, und meistens startet der Mac nicht mehr nach dem Herunterfahren.

#### Temporäre Lösungen

- Wenn der Mac nicht startet, einfach den Power-Button für 5–10 Sekunden gedrückt halten, loslassen und dann erneut drücken. Danach sollte der Mac wieder starten.
- Falls er nicht ausgehen möchte, einfach über macOS herunterfahren.

Leider habe ich noch keinen Weg gefunden, diese Probleme dauerhaft zu beheben. 

### Bilder in der Doku

Die ersten 3 Bilder sind leider Irgendwo von Google, sollte jemand der Anleitung folgen, wäre ich froh, wenn einer mal einheitliche Screenshots Comitten könnte.

Verbesserungsvorschläge sind auch gern gesehen c:

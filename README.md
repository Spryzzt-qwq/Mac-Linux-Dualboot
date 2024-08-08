# Linux auf einem Mac installieren (Dual Boot)

Um alte Mac,
0’s wieder auf den Stand der Zeit zu bringen, ist hier eine Anleitung, wie man
bei nicht länger unterstützten Intel Mac’s Linux installiert.

## Vorbereitung

Zuerst ist es nötig in den Recovery Modus zu kommen. Dort Partitionieren wir
die Festplatte und schalten die Integritätskontrolle ab, um problemlos Linux
installieren zu können.

### Schritt 1: Partitionierung

- Mac Starten und sofort Option (Windows Taste) + R gedrückt halten
    Der Mac sollte im Recovery Modus starten
- Festplattendienstprogramm Starten

![MacOS Recovery Menü](/Bilder/mac-recovery-mode-die-macos-dienstprogramme.png)

- Festplatte auswählen und auf den Partitionieren Button drücken
- Es öffnet sich ein Fenster indem unten links noch ein Partitionieren
    Button ist. Nachdem dieser gedrückt wurde landet man in der
    Partitionierungsübersicht
- Dann die MacOS Partition auswählen und auf das „+“ (unten Links)
    klicken
- Die neue Partition muss auf FAT (MS-Dos Dateisystem) formatiert
    werden
- anschließend auf Anwenden klicken
Die Partition ist jetzt erstellt und das Dienstprogramm kann geschlossen
werden.


### Schritt 2: Integritätsschutz Deaktivieren

- Das Terminal im Dienstprogramme Reiter auswählen
- Folgenden Befehl eingeben: ’ _csrutil disable_ ’

Danach sind wir im Recovery Modus fertig und der Mac kann
Heruntergefahren werden.

## Linux Installation

### Schritt 1: Vom Installationsstick Booten

- Den Mac Starten und sofort die Command-Taste (Alt) gedrückt halten
- Danach sollte dieses oder ein ähnlich aussehendes Menü auftauchen
- Dort das USB-Gerät (EFI-Boot auswählen)


### Schritt 2: Installation

Diese ist bei vielen Distributionen nicht gleich, das ist aber auch nicht
schlimm, da nur die Festplattenformatierung in der Installation eine Rolle
spielt. Da es in Pop_OS am einfachsten ging und auf viele komplizierte
Menüs verzichtet eignet sich diese Distribution am ehesten zur
Demonstration.

### Schritt 2.1: Festplatte Partitionieren

- Der Grafische Einrichtungsassistent ist in den meisten Fällen
    selbsterklärend, dem also einfach Folgen, bis man an dem Punkt
    angelangt ist, an dem gefragt wird Wo/Wie installiert werden soll.
- Meistens gibt es 2 Optionen, alles Löschen und Linux installieren oder
    Benutzerdefiniert (Custom, Advanced, etc.)
- Da wir einen Dual Boot wollen, müssen wir die Benutzerdefinierte
    Installation wählen
- Daraufhin, auf „Partitionen verwalten“ klicken, dann öffnet sich ein
    GParted Fenster
- Dort die vorhin erstellte Partition in der Liste auswählen und löschen
    (Rechtsklick)


- Dann Rechtsklick auf den nicht zugeordneten Speicher und auf Neu
    klicken
    da entsteht eine Partition für den Bootloader, diese darf
    **minimal 500 MB** groß sein und muss auf **Fat32** formatiert werden
- Dasselbe nochmal für das eigentliche Betriebssystem
    Die Größe kann hier frei gewählt werden, es sollten aber noch ca.
    **4-8 GB übrig bleiben** , dass ganze muss in **ext4** (oder dem von der
    Distro vorgeschlagenem Hauptdateisystem) formatiert werden


- Die letzte zu erstellende Partition ist der Auslagerungsspeicher
    (falls der Ram voll ist)
    Den **restlichen Speicher** nutzen und als **Swap** formatieren
- Zum Abschluss sollte die Liste so aussehen:
- Die Konfiguration muss mit dem Haken bestätigt werden, erst dann
    werden die Änderungen wirksam. Man kann also vorher noch nicht’s
    kaputt machen.


- Im letzten Schritt der Partitionierung müssen alle 3 Partitionen einzeln
    Ausgewählt werden und wie in den Bildern konfiguriert werden.
- Danach „Löschen und Installieren“ anklicken und dem
    Installationsassistenten folgen bis das System installiert und bereit für
    den Neustart ist.


## Es ist geschafft

Das System muss jetzt nur noch neugestartet werden.
Beim Neustart die Command Taste (Alt) gedrückt halten und die Festplatte
mit EFI-Boot auswählen

Über das Menü was auftaucht kann beim Starten jetzt immer zwischen Linux
und MacOS gewechselt werden.



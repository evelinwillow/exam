# PRÜFUNGSTHEMEN AP2

## Networking

## Hardware

## Software

### Backups

Es gibt drei Arten von Backups; *Vollbackup*, *inkrementelles Backup*, und *differenzielles Backup*. 
Windows versieht Daten mit einem sogenannenten *Archivbit*, das wie eine Warnflagge funktioniert. Wird eine Datei mittels Backup gesichert, wird das Archivbit zurückgesetzt.
Sobald eine Datei erstellt oder verändert wird, wird das Archivbit gesetzt. 

#### Vollbackup

Bei einem Vollbackup werden *alle Daten komplett gesichert*. Der Vorteil hier ist, dass diese Art von Backup *komplett unabhängig von früheren Sicherungen* ist. 
Der Nachteil ist, dass hier mitunter *sehr grosse Datenmengen* gesichert werden, obwohl sich eventuell nur wenige Daten tatsächlich verändert haben, und der *hohe Zeitaufwand*.

Ein Vollbackup sichert alle Daten *ohne Beachtung des Archivbits*. Das Archivbit wird *zurückgesetzt*.

#### Inkrementelle Backups

Bei inkrementellen Backups werden nur die Daten gesichert, die sich *seit dem letzten Vollbackup* verändert haben. 
Dies hat den Nachteil, dass die Daten bei einer *Wiederherstellung aus mehreren Teilen* zusammengesetzt werden müssen. 
Um zum Beispiel bei einem Totalverlust aller Daten eine vollständige Restauration durchzuführen, muss das *letzte Vollbackup gefolgt von allen inkrementellen Backups* in der Reihenfolge der Erstellung wiederhergestellt werden.

Ein inkrementelles Backup sichert alle Daten, die über ein *gesetztes Archivbit* verfügen. Es wird *zurückgesetzt*.

#### Differenzielle Backups

Differenzielle Backups werden immer *ausgehend vom letzten Vollbackup* durchgeführt. Es werden diejenigen Daten gesichert, die sich *seit dem Vollbackup geändert* haben. 
Dadurch fallen grössere Datenmengen als beim inkrementellen Backup an, da jede Datei, die auch nur einmal seit dem letzten Vollbackup verändert wurde, *immer wieder neu gesichert* wird. 
Jedoch spart man Speicherplatz und Zeit gegenüber einer vollständigen Datensicherung.

Ein differenzielles Backup sichert alle Daten, die über ein *gesetztes Archivbit* verfügen. Es bleibt allerdings *unberührt*.

- TODO snapshots

---

### Struktogramme

Struktogramme sind eine Möglichkeit, Algorithmen unabhängig von einer Programmiersprache aufzuschreiben. Sie sind Veranschaulichungen von Algorithmen mittels einfacher geometrischer Formen, deren Grundbaustein ein Rechteck darstellt. Jedes Rechteck ist mit einer elementaren Anweisung beschriftet oder es stellt eine Kontrollstruktur wie z.B. eine Schleife oder Verzweigung dar. Rechtecke können aufeinander gestapelt und ineinander geschachtelt werden. Diese Konstruktionsprinzipien findet man in vielen Programmiersprachen wieder, sodass die Notation eines Algorithmus als Struktogramm einen hilfreichen Zwischenschritt auf dem Weg vom Problem zum Programm darstellt. 

```
Baustein                    Struktogramm

Anweisung                   ---------------------
                            | Schritt 1         |
                            ---------------------

Sequenz                     ---------------------
                            | Schritt 1         |
                            ---------------------
                            | Schritt 2         |
                            ---------------------

Schleife mit Bedingung      ---------------------
                            |  wiederhole bis   |
                            |  ------------------
                            |  | Schritt 1      |
                            ---------------------

Schleife mit Zähler         ---------------------
                            | wiederhole 10 mal |
                            |  ------------------
                            |  | Schritt 1      |
                            |  ------------------
                            |  | Schritt 2      |
                            ---------------------

Verzweigung                 ---------------------
                            | ist x = y ?       |
                            --------\   /--------
                            | ja     \ /   nein |
                            ---------------------
                            | Pfad 1  | Pfad 2  |   -> Es müssen nicht zwingend beide Pfade ausgefüllt sein! (z.B. Abbruchbedingung)
                            ---------------------

Blockaufruf                 ---------------------
                            | | Subroutine    | |
                            ---------------------
```

## Programmablaufplan

Ein Programmablaufplan ist ein Ablaufdiagramm für ein Computerprogramm, das auch als Flussdiagramm oder Programmstrukturplan bezeichnet wird. Es ist eine grafische Darstellung zur Umsetzung eines Algorithmus. Es beschreibt die Folge von Operationen zur Lösung einer Aufgabe.
Er ist älter als das Struktogramm und wird nur noch sehr selten eingesetzt.

```
Baustein            Beschreibung                    PAP

Terminator          Rechteck mit abgerundeten       /------------\
                    Ecken / Oval                    | Start/Stop |
                                                    \------------/

Verbindung          Linie, Pfeil                    --------------
                                                    ------------->

Operation           Rechteck                        --------------
                                                    | Operation  |
                                                    --------------

Subroutine          Rechteck mit doppelten          --------------
                    vertikalen Linien               | | Subr.  | |
                                                    --------------

Verzweigung         Raute                             ----/\----
                                                    / Verzweig.  \
                                                    \            /
                                                     ----\/----

Ein-/Ausgabe        Parallelogram                     /----------/
                                                     /   I/0    /
                                                    /----------/


```

## Security

# EHEMALIGE PRÜFUNGEN

## 2023 Sommer FISI

GA 1

- Note: 67/100 1. Durchlauf
                
~~1ba) -> ROUTING~~
~~3aa) RAID !!! ja auch RAID 6 kommt dran !!!!~~
~~3bb) Struktugramme...~~
~~3c) Formel für USV~~
~~4a) Unit conversion...~~
~~4cb) Dif/Inc/Full backup wiederherstellung~~
~~5d) Inhalt Certificate~~

GA 2 

~~1a) Lasten/Pflichtenheft~~
~~1da) Zinsrechnung~~ 
2b) Application-Virtualisierung
~~SQL~~ 
~~DSGV~~ 

WiSo

3) Arbeitszeit 
7) Betriebsrat Mitbestimmungsrecht 
10) Sozialpartner
12) Beitragsrechnung
18) Mutterschutz
20) Wirtschaftlichkeit
26) Tarifverhandlung Ablauf
27) Kündigungsfrist 


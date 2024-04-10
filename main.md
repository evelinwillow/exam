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

- Struktogramme
    - Syntax

## Mathe

- Unit conversion (MiB zu MB, Mbit/s...)

## Security

# EHEMALIGE PRÜFUNGEN

## 2023 Sommer FISI

- Note: 67/100 1. Durchlauf
                
1ba) -> ROUTING
3aa) RAID !!! ja auch RAID 6 kommt dran !!!!
3bb) Struktugramme...
3c) Formel für USV
4a) Unit conversion...
4cb) Dif/Inc/Full backup wiederherstellung
5d) Inhalt Certificate

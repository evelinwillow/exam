# GA1

## Aufgabe 1

### a)

#### aa)

Falsche Adresse für DNS-Server; 10.0.0.220

(Korrekt: 10.0.0.200)
                                    
**1 PUNKT**

#### ab)

Gateway nicht im Subnet (Korrekt: vermutlich .30)

**3 PUNKTE**

#### ac) 

Subnetzmaske inkorrekt; 255.255.255.224

**4 PUNKTE**

### b)

#### ba)

##### Köln

172.16.10.0     255.255.255.252     ETH1    ----
Korrektur: 
172.16.30.0     255.255.255.252     ----    172.16.20.2

192.168.1.0     255.255.255.224     ----    172.16.10.2
Korrektur:
192.168.1.0     255.255.255.224     ----    172.16.20.2


##### Hamburg

0.0.0.0         0.0.0.0             ----    172.16.10.1
Korrektur:
0.0.0.0         0.0.0.0             ----    172.16.30.2

##### Frankfurt

192.168.1.0     255.255.255.224     ----    172.16.30.1

**3 PUNKTE** -- aber warum? Meine Routen sollten korrekt sein...

#### bb)

Dynamisches Routing würde in Zukunft dafür sorgen, dass manuelle Korrektur der Routen bei Serviceausfällen nicht mehr nötig ist. Routen werden automatisch eingetragen, und die schnellste Route würde bevorzugt werden.

**3 PUNKTE**

**14/25 GESAMT**

## Aufgabe 2

### a) 

- Webserver; 80/442
- FTP-Server: 23

**1 PUNKT**

### b)

#### ba)

Regel 1 erlaubt Zugriff auf den HTTP-Proxy aus dem internen Netz; Regel n verbietet jeden anderen Traffic.

**4 PUNKTE**

#### bb) 

```
ACCEPT  TCP     172.16.100.4/32     ANY     >1023   80  DMZ-EXT     WAN
ACCEPT  TCP     172.16.100.4/32     ANY     >1023   442 DMZ-EXT     WAN
ACCEPT  UDP     172.16.100.4/32     ANY     >1023   53  DMZ-EXT     WAN
DENY    IP      ANZ                 ANY     -       -   ANY         ANY 
```

**6 PUNKTE**

### c) 

#### ca)

Durch Verwendung von kurzen Schlüsselwörter könnten URLs, die das Schlüsselwort beinhalten, auch gesperrt werden. ( z.B. sex -> m**sex**change )

**3 PUNKTE**

#### cb)

Blacklists schützen z.B. nicht vor Websites, die über merhere URLS verfügen, oder die direkt über die IP-Adresse eingetragen werden. Weiterhin schützt dies nicht vor DNS-Rebind-Attacken, wodurch gesperrte Websites wieder erreichbar werden. Ausserdem kann sich die URL einer Website auch ändern.

**4 PUNKTE**

### d)

#### da)

UDP (User Datagram Protocol)

**2 PUNKTE**

#### db)

DNS-Filter sind meist einfacher zu konfigurieren, und jeder DNS-Dienst hat integrierte Filterlisten-Funktionen. Die Implementation einer HTTP-Filter-Lösung ist wesentlich komplexer.

**0 PUNKTE**

**20/25 GESAMT**

## Aufgabe 3)

### a)

#### aa)

RAID 5 kann mit 12 8-TB-Platten bestückt werden ( 11 * 8 TB = 88 TB Kapazität + eine Platte für Parität ) oder 9 12-TB-Platten ( 8 * 12 TB = 96 TB Kapazität + eine Platte für Parität ). 4-TB-Platten kommen aufgrund mangelnder Einschübe nicht in Frage.

RAID 6 benötigt eine weitere Platte für Parität. Damit kommen nur 12-TB-Platten in Frage ( 10 Platten - 8 * 12 TB = 96 TB Kapazität + 2 Platten für Parität )

**6 PUNKTE** 

#### ab)

RAID-10-Systeme haben maximal 50% der Gesamtkapazität der Platten zur Verfügung ( 12 * 12 TB = 144 TB; 144 TB / 2 = 72 TB ).

**3 PUNKTE**

### b)

#### ba)

0 */1 * * * /usr/local/lib/SANSpeicherVoll.sh

**4 PUNKTE**

#### bb)

```
_____________________________________________
| GESAMTSPEICHER ERMITTELN                  |
---------------------------------------------
| Aktuellen Speicher ermitteln              |
---------------------------------------------
| Gesamtspeicher/Aktuellen Speicher >= 80%? |     -> Korrektur: Aktueller Speicher/Gesamtspeicher
------------------\   /----------------------
|               ja \ / nein                 |
--------------------|------------------------
| Mail senden       | nichts tun            |
---------------------------------------------
```

**6 PUNKTE**

#### bc)

Gegeben:
- USV_Leistung = 2400 VA
- Last_aktuell = 1200 VA
- Storage_Leistung = 600 VA
- Kapazität_Akku = 1500 VAh

Gesucht:
- Autonomiezeit

Autonomiezeit = ( Kapazität / Leistung ) / ;
Autonomiezeit = ( 1500 VAh / ( 1200 VA + 600 VA ) ) / 2
Autonomiezeit = ( 1500 VAh / 1800 VA ) /2
Autonomiezeit = 0.83...h / 2
Autonomiezeit = 0.416...h * 60

Autonomiezeit = 25 Minuten

**4 PUNKTE**

**23/25 GESAMT**

## Aufgabe 4

### a)

Gegeben:
- Uplink: 75% von 1 Gbit/s
- Datenmenge: 800 GiB

Gesucht:

- Dauer

Dauer = Datenmenge / Geschwindigkeit
Dauer = 800 GiB / ( 0.75 * 1 Gbit/s )
Dauer = ( 800 * 1024 * 1024 * 1024 * 8 ) / ( 0.75 * ( 1 * 1024 * 1024 * 1024 ) )
Dauer = 6,871,947,673,600 bit / 805,306,36 bit/s 
Dauer = 8,533.3... s = 142.2 m = 2.37 h
Dauer = 2 h + ( 0.37h * 60 )
Dauer = 2 h + 22m

**0 PUNKTE**

### b)

#### ba)

Ein mögliches Problem ist versehentliches Überschreiben von Daten während das Backup-Prozesses. Dadurch werden Daten eventuell nicht korrekt gesichert, oder korruptiert.
Weiterhin kann auf High-Availability-Systemen der Write-Access nicht ausgeschaltet werden, um dieses Problem zu umgehen, da das System durchgehend schreiben können muss.

**4 PUNKTE**

#### bb)

Ein Snapshot ist eine Momentaufnahme des gesamten Speichers zu einem bestimmten Zeitpunkt. Auf die Kopie kann nur lesend zugegriffen werden. Weiterhin dauert die Erstellung eines Snapshots nicht länger, wenn der genutzte Speicher steigt.

**2 PUNKTE**

#### bc)

Ein Snapshot liegt weiterhin auf dem selben Speicher, von dem der Snapshot erstellt wurde. Damit handelt es sich nicht um eine Datensicherung, da bei Ausfall der Festplatte die Daten trotzdem verloren sind.

**4 PUNKTE**

### c)

#### ca)

```
                            Archivbit
Aktion                      wird gesetzt    wird zurückgesetzt  wird nicht verändert
Datei erstellen             x               -                   -
Datei lesen                 -               -                   x
Datei ändern                x               -                   -
Voll-Backup                 -               x                   - 
Dif-Backup                  -               -                   x
Ink-Backup                  -               x                   -
```

**3 PUNKTE**

#### cb)

Bei dem differenziellen Backup wird erst das Backup von letztem Sonntag wiederhergestellt, anschliessend das Backup von Freitag.

Bei dem inkrementellen Backup wird erst das Backup von letztem Sonntag wiederhergestellt, danach alle erstellten inkrementellen Backups seit Sonntag.

Das letzte wiederhergestellte Backup ist bei beiden das Backup vom Freitag; das Samstag-Backup würde erst Abends erstellt werden.

**7 PUNKTE**

**20/25 PUNKTE**

## Aufgabe 5

### a)

#### aa)

Verschlüsselung der Email mit asymmetrischen Schlüsselpaaren

**2 PUNKTE**

#### ab)

Digitale Signatur des Absenders

**2 PUNKTE**

#### ac)

Hash-Funktion bzw. Checksum (z.B.SHA, MD5)

**2 PUNKTE**

### b)

  2   5
1               1

6       4
    3       7
4       6

**4 PUNKTE**

### c)

Ein Hash-Algorithmus darf nicht reversibel sein (d.H. aus der Prüfsumme darf man nicht die Quelldatei berechnen können), und jedes Ergebnis muss eindeutig sein (verschiedene Quelldateien dürfen nie die selbe Prüfsumme ergeben.

**4 PUNKTE**

### d)

- Aussteller
- Gültigkeit
- Adresse des zertifizierten Objektes
- Digitale Signatur

**3 PUNKTE**

### e)

Deaktivierung von nicht benötigten Diensten und Ports, um Angriffsfläche zu minimieren; Implementation von Benutzerkonten mit Fokus auf minimierung der vergebenen Rechte

**6 PUNKTE**

**23/25 PUNKTE**

**GESAMTPUNKTE: 77 oder 80**

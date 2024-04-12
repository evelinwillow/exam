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

# GA2

## Aufgabe 1 

### a)

Das Lastenheft beinhaltet grundlegende Projektinformationen und stellt die Grundlage für die erstellung des Pflichtenheftes darf

Das Pflichtenheft beinhaltet die Gesamtheit der Anforderungen des Projektes.

**0 PUNKTE**

### b) 

Hochverfügbarkeit, da 0.08h ( knapp 5 Minuten ) Downtime im Jahr trotzdem problemlos 15m Bearbeitungszeit eingehalten werden, FALLS die Proben innerhalb von 10 Minuten bearbeitet werden können. Falls NICHT, kommt nur Nonstopverfügbarkeit in Frage.

**3 PUNKTE**

### c)

Kompatabilität - Systeme können ohne Probleme miteinander arbeiten und kommunizieren, oder Software wird von Systemen unterstützt (z.B. ist jeder Webserver mit dem HTTP-Protokol kompatibel)
Skalierbarkeit - Systeme können bei Bedarf erweitert werden, z.B. kann ein Server-Cluster um weitere Server erweitert werden
AI - Künstliche Intelligenz, genauer neurale Netzwerke oder deep learning - ChatGTP
Nachhaltigkeit - Umweltschutz, oder auch verfügbare Ressourcen nicht überbelasten - Minimierung von z.B. Einmalverpackungen

**7 PUNKTE**

### d)

#### da)

Gegeben: 240,000 Euro
Feste Tilgungsrate
Zinssatz 5% p.a.

```
Jahr    Anfang          Zinsen 5%       Tilgung         Kreditrate      Restschuld
1       240,000         12,000          78,000         
2 
3 
4 
ges                     48,0000         288,000
```

**0 PUNKTE**

#### db)

6000
288,000
16,000
304,000

**2 PUNKTE**

#### dc)

Der Kredit ist wirtschaftlicher, da 288,000 < 304,000. 
Das Leasing ist um 5.5% teurer. ( ( Summe Kredit / 100 * Summe Leasing ) - 100 )

**2 PUNKTE**

**11/25 PUNKTE**

## Aufgabe 2

### a)

#### aa)

Virtuelle Server werden über einen Hypervisor realisiert. Dies erlaubt es, auf einem physischem Server mehrere virtuelle Systeme gleichzeitig laufen zu lassen. Physische Server können (logischerweise) nur einen Server bereitstellen. Best Practice schreibt vor, je nur einen Dienst pro Server laufen zu lassen. 
Virtuelle Server lassen sich weiterhin im Gegensatz zu physischen Servern softwareseitig verwalten, und so kann z.B. ein virtueller Server bei Bedarf in einen anderes Rechenzentrum live-migriert werden. Dies geht mit physischen Servern nur schwer bis gar nicht.

**4 PUNKTE**

#### ab)

- Bessere Auslastung der verfügbaren Hardware
- Geringere Hardwarekosten
- Standortunabhängigkeit

- Bei z.B. Cloud-Servern können Netzwerkprobleme den Zugriff auf den Server komplett unterbinden. Physische Server können weiterhin mit z.B. KVM-Konsolen bedient werden

**4 PUNKTE**

#### ac)

Netzwerkadapter
Serielle Konsolen 
Monitor via z.B. VNC, SPICE, ...

**2 PUNKTE**

### b) 

Application-Virtualisierung erlaubt es, nicht zwingend eine gesamte Server/Desktopumgebung bereitstellen zu müssen.

**0 PUNKTE**

### c)

Core-Switch: Haupt-Switch, das Rückgrat eines Netzwerkes. Weitere Switches werden an diese Switch angeschlossen (z.B. Coreswitch im Rechenzentrum und einzelne Switches in z.B. jedem Stockwerk)

NAS: Network Attached Store - über das Netzwerk angebunderer File Server, häufig ein network-enabled RAID 

DC: Rückgrat einer AD-Struktur. Zentrale Verwaltungseinheit der Domäne, wie z.B. Verwaltung der Domänenmitglieder (Server, Clients) und Benutzer (Admin, User...)

DMZ: Demilitarized Zone - Abgetrennter Netzwerkbereich, häufig zur Trennung öffentlich erreichbarer Dienste wie Webserver und Firmeninternem lokalem Netzwerk

DHCP: Dynamic Host Configuration Protocol - Ermöglicht Systemen im Netzwerk, sich automatisch eine IP-Adresse sowie weitere Konfigurationsinformationen zu beziehen

**10 PUNKTE**

**20/25 PUNKTE**

## Aufgabe 3 

### a)

Gegeben:
- 8 Stunden pro Tag, 7 Tage pro Woche, 30 Tage pro Monat, 12 Monate pro Jahr
- Eine Analyse pro Gerät pro Minute 
- Ein Datensatz pro Analyse 
- 100 Zeichen zu je 1 Byte und 300 double zu je 8 Byte pro Datensatz

Gesucht:
- Datenvolumen in GiB pro Jahr und Gerät

data = ( Summe Datensatz ) * ( Summe Analysen )
data = ( ( 100 * 1 B ) + ( 300 * 8 ) ) * ( 60 Analysen * 8 h * 30 t * 12 m ) 
data = ( ... ) * ( 172,800 Analysen )
data = ( ( 100 B ) + ( 2,400 B ) ) * ( ... )
data = ( 2,500 B ) * ( 172,800 Analysen )
data = 432,000,000 B = 421,875 KiB = 411.9873046875 MiB =~ 0.40 GiB 

**9 PUNKTE** aber: offzielle Lösung falsch, eventuell 3 Punkte

### b)

IDK was Pseudonymisierung ist...

### c)

#### ca)

Eine USV sorgt dafür, dass bei Stromausfall Systeme weiterhin online bleiben können. Somit können sie kontrolliert heruntergefahren werden oder der Ausfall überbrückt.

**2 PUNKTE**

#### cb)

Datenverlust

Hardwareschäden durch Spannungsspitzen

Verletzung des Verfügbarkeit-Schutzzieles

**0 PUNKTE**

#### cc)

Gegeben: 
- 1 USV
    - 8 Akkus
        - Q = 200 Ah 
        - U = 12 V
    - Ladestand: 100%
- 10 Server
    - 750 W Netzteil

Gesucht:
- P in W und VA 
- Q_gesamt
- Wh_gesamt 
- t in h:m 

Formeln:
- W = Q * U 
- P = W / t 

##### P 

10 Server mit je 750 W = 7500 W.
Scheinleistung: 7500 W * 1.55 
Scheinleistung: 11,625 VA 

##### Q_gesamt 

8 Akkus mit je 200 Ah. 
Q_gesamt = 8 * 200 Ah = 1,600 Ah 

##### Wh_gesamt 

Wh_gesamt = ( Q * U )
Wh_gesamt = ( 1,600 Ah * 12 V )
Wh_gesamt = 19,200 Wh 

##### t 

P = W / t 
P * t = W 
t = W / P 
t = 19,200 Wh / 7,500 W 
t = 2.56 h | 0.56 * 60 = 33.6 =~ 34 m 

t = 2 h 34 m 

**8 PUNKTE** aber: OFFIZIELLE LÖSUNG FALSCH, evtl. nur 7

**19/25 PUNKTE** oder **12/25 PUNKTE**

## Aufgabe 4

### a)

#### aa)

rosa    rosa
gelb    grün
gelb    blau
grün    grün 
blau    gelb 

**10 PUNKTE**

#### ab) 

Betäubungsmittelrezepte werden in jedem Fall falsch erkannt. Privat versicherte Rezepte werden falls erkannt, falls es sich um verschreibungspflichtige Rezepte handelt.

**4 PUNKTE**

### b)

#### ba)

SELECT Nachname, Vorname FROM Patient WHERE LEFT(Nachname, 1) = M ORDER BY Nachname ASC

#### bb) 

SELECT Datum FROM ( SELECT Befund FROM Patient AS table ) WHERE BID = 734 UPDATE Datum = 01.04.2023

#### bc)

SELECT Befund FROM ( SELECT * FROM Patient ) WHERE MONTH(Date) = Februar AND YEAR(Date) = 2023 SUM(Befund) 

**0 PUNKTE**

**14/25 PUNKTE**

## Aufgabe 5 

### a)

#### aa)

Beim Datenschutz handelt es sich um den Schutz personenbezogener Daten vor unerlaubter Einsicht oder Verarbeitung. Die personenbezogenen Daten müssen davor geschützt werden, von Personen oder Systemen, die nicht direkt mit der Verarbeitung der Daten beauftragt wurden, eingesehen oder gar entwendet zu werden.

**1 PUNKT**

#### ab)

Bei der Datensicherheit handelt es sich um die Garantierung des Schutzzieles Integrität und Eindeutigkeit (nicht offizieller Name; vergessen). Es muss gewährleistet werden, dass die Daten nicht eventuell korruptiert werden, oder dass Daten den falschen Personen zugeordnet werden.

**1 PUNKT**

### b) 

Es dürfen nur Daten erhoben werden, die tatächlich auch nötig sind (legitimate interest), jeder muss über Speicherung der Daten informiert werden, und es muss erst eine explizite Erlaubnis eingeholt werden.

**2 PUNKTE**

### c)

5 
1 
2 
4
3 
6 
7 

**4 PUNKTE**

### d)

Einwilligungsformular
Zugriffseinschränkung (z.B. durch Benutzerkonten)
Zutrittseinschränkung (z.B. Kameraüberwachung, physisch abgeschottete Speicherorte)

**6 PUNKTE**

**14/25 PUNKTE**

**GESAMTPUNKTE: 64 oder 51**

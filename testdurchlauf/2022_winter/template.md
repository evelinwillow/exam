# GA 1 

## Aufgabe 1 

### a)

OnPrem:

- Schnelleres Netzwerk
- Verfügbarkeit bei Netzausfall
- Erfordert etwas weniger Fachkenntnis

Cloud:

- Niedrigere laufende Kosten
- Niedrigere Anschaffungskosten
- Verfügbarkeit von überall (Anbindung von Standorten)

**5/6 PUNKTE**

### b)

#### ba)

Ping (Verzögerung bzw Transportzeit); Grosse physische Entfernung, Hoher Datendurchsatz

**4/4 PUNKTE**

#### ba)

Echtzeitanwendungen (Computerspiele online hehe)

**2/2 PUNKTE**

### c)

#### ca)

Failover-Clusterung  |   Erhöhung der Verfügbarkeit durch Vermeidung eines Serviceausfalles bei Serverausfall
Headless OS | Einsparung von Ressourcen, erhöht Geschwindigkeit
Redundante Netzanbindung | Vermeidung eines Serviceausfalles bei Netzausfall (Kabel kaputt) -> Relevant bei Clusterung 

**4/6 PUNKTE**

#### cb) 

Gegeben: 

- 5 TiB Datenbank 
- 3 TiB Nutzdaten 
- 5 TiB Puffer 

- Zwei Arrays mit je 8 Platten zu 2 TiB -> 16 TiB gesamt 

Gesucht: 
 
- Anzahl Festplatten

Daten_gesamt = 5 TiB + 3 TiB + 5 TiB Puffer = 13 TiB 
Platten_Ohne_Raid = 13 TiB / 2 TiB = 7 Platten 
Platten_Raid = Platten_Ohne_Raid + 2 Platten 
Platten_Raid = 9 Platten 

**4/5 PUNKTE**

### d) 

#### da)

Gegeben: 

- 30 GiB Daten pro Monat 
- 60% Komprimierung 
- 10 Jahre Speicherdauer

MAX 1 TiB! 

Gesucht: 

- Datenmenge 

Datenmenge = ( 10 * 12 ) * ( 30 GiB * 0.4 ) 
Datenmenge = 120 * 12 GiB
Datenmenge = 1,440 GiB / 1024 = 1.4 TiB -> Speicher reicht nicht!

**2/2 PUNKTE**

#### db) 

Datenmenge_Jahr = 12 * 12 GiB = 144 GiB / 1024 = 0.14 TiB/j 

Jahre = 1 TiB / 0.14 TiB/j = 7.1 =~ 7 Jahre 

**2/2 PUNKTE**

**23/27 PUNKTE**

## Aufgabe 2 

### a)

#### aa)

int 
boolean 
int -> char(5)
char(11) -> 16
date
char(22)

**2/3 PUNKTE**

#### ab) 

```sql
SELECT COUNT(Kunde.Kunde_Aktiv) 
FROM Kunde 
WHERE Kunde.Ort = "Augsburg"
```

**2/4 PUNKTE**

#### ac)

```sql
Werbepartner varchar(), 
Werbung_verschickt date,
WerbungsID, -> WerbungsID NOT NULL,
KundenNr -> KundenNR int,
-> PRIMARY KEY (WerbungID),
-> FOREIGN KEY (KundenNr) REFERENCES Kunde(KundenNr)
```

**2/6 PUNKTE**

#### ad)

SELECT COUNT(Werbeaktion_verschickt)
FROM Kunde JOIN Werbeaktion
WHERE Kunde.PLZ LIKE 8%
AND Werbung.Werbung_verschickt < 31.12.2021

**0/6 PUNKTE**

### b)

Redis (Cache) 

**2/4 PUNKTE**

**8/23 PUNKTE**

## Aufgabe 3 

LTO wird vermutlich jahrelang wesentlich günstiger als Festplattenplatz bleibe. LTFS ermöglicht ausserdem, Daten mit traditionellem Festplattenspeicher ensprechenden Geschwindigkeiten zu lesen und schreiben.

**4/4 PUNKTE**

### b)

alle daten, archivbit zurückgesetzt
alle seit letztem vollbackup, archivbit nicht zurückgesetzt
alle seit letztem inkrement, archivbit zurückgesetzt
alle daten, archivbit ignoriert

**10/10 PUNKTE**

### c)

V2 - D2 - D3 - D5 

**4/6 PUNKTE**

### d)

x 
x
    x
x     ->    x
    x -> x  x

**3/5 PUNKTE**

**21/25 PUNKTE**

## Aufgabe 4 

### a)

```c 
int counter;

for ( counter = 0; counter < 24; counter++ )
{
    sum = sum + usedRAM[counter];
}

average = sum / 24;

if ( sum > 75% )
{
    MessageBox.Show("RAMn't","uh oh");
}

```

**16/16 PUNKTE**

### b)

Datenkapselung bedeutet, dass Daten innerhalb von Klassen/Objekten gespeichert werden, anstatt lose im Arbeitsspeicher herumzufliegen und von jedem gelesen/geschrieben werden zu können. Dadurch müssen sie durch definierte getter/setter-Funktionen ausgelesen oder geschrieben werden.

Vererbung bedeutet, dass Klassen, die von anderen Erben, dessen Methoden und Daten (wort vergessen) übernehmen. Dadurch müssen häufig geschriebene oder allgemeingültige Funktionen bei ähnlichen oder derivativen Klassen nicht jedes mal neu definiert werden.

**6/6 PUNKTE**

### c)

3200
?
16

**3/3 PUNKTE**

**25/25 PUNKTE**

**GESAMTPUNKTE: 77**

# GA 2 

## Aufgabe 1 

## a)

### aa)

/30 - 4 
/29 - 8

8 12 24 32 40 48 56 64 72 80 ....

NA: 203.0.113.64
FH: 203.0.113.65 -> ...-ext
LH: 203.0.113.70 -> ...-int
BC: 203.0.113.71

**2/2 PUNKTE**

### ab) 

/30 -> 2 Bit Hostanteil -> 252
/29 -> 3 Bit Hostanteil -> 248
/8  -> 24 Bit Hostanteil

```table 
NID             Subnet          Schnittstelle/Next Hop

198.51.100.2    255.255.255.252 LWL
203.0.113.64    255.255.255.248 ETH 
10.0.0.0        255.0.0.0       203.0.113.70
172.16.0.0      255.255.0.0     192.0.2.121
0.0.0.0         ----            LWL
```

**6/8 PUNKTE**

### b)

SPI betrachtet auch höhere Ebenen des OSI-Modells und unterstützt z.B. auch NAT und weitere Funktionen.
Aufgebaute Verbindungen (States) werden getrackt und protokolliert, können eigene, spezielle Regeln erhalten

**4/4 PUNKTE** -> aber nur Glück! Lernen! 

### c) 

```table 
Aktion  Protokoll   Quelle      Ziel            Quellport   Zielport    Von Interface   Nach Interface
PASS    TCP         *           203.0.113.67    *           80          LWL             ETH 
PASS    TCP         *           203.0.113.67    *           443         LWL             ETH
PASS    TCP         *           203.0.113.68    *           25          LWL             ETH  
PASS    TCP         *           203.0.113.68    *           113         LWL             ETH
DROP    *           *           *               *           *           LWL             ETH
PASS    *           *           *               *           *           ETH             LWL
```

**8/10 PUNKTE**

**20/24 PUNKTE**

## Aufgabe 2 

### a)

DNS löst Domain Names in Adressen auf 

**3/3 PUNKTE**

### b) 

142.250.184.227

**4/4 PUNKTE**

### c)

10.0.0.101
2001:...

**4/4 PUNKTE**

### d) 

fd00:...

**3/3 PUNKTE**

### e) 

4001 kam zuerst zurück, und der Ping startete, bevor 4016 überhaupt ankam.

**3/3 PUNKTE**

### f) 

5 Hops ( ( 128 - 118 ) / 2 )

**0/3 PUNKTE** -> fast richtig!

### g) 

Load Balancing

**3/3 PUNKTE**

**20/23 PUNKTE**

## Aufgabe 3 

### a) 

TLS ist auf Transportebene verschlüsselt. Daten können nicht mitgelesen werden, ferner kann durch Digest überprüft werden, ob Daten abgeändert wurden.

**4/4 PUNKTE**

### b) 

1.2 erlaubt unsichere Verschlüsselung 
Handshakes sind vor ServerHello nicht verschlüsselt -> MITM-Anfällig
Session Hijacking möglich

**9/9 PUNKTE**

### c) 

Interne CA können zentral vom Unternehmen verwaltet werden, und Ausstellung sowie Sperrung von Zertifikaten erfolgt einfacher, einfachere Integration in z.B. RADIUS
Externe CA oft kostspielig; intern keine Lizenz nötig.

**6/6 PUNKTE**

### d)

Einfach für MA 
Kann komplett ohne extraaufwand für MA eingerichtet werden 
Physisches Gerät ist sicherste Lösung (2FA, aber ein Faktor physisch) 
2FA ohne extrakosten 

**8/8 PUNKTE**

**27/27 PUNKTE**

## Aufgabe 4 

### a)

Gegeben: 
- 5 interne Gespräche 
- 15 externe Gespräche 
- Overhead 10% 
- 64kBit/s 

5 Intern -> 10 Verbindungen 
15 Extern -> 15 Verbindungen -> 25 gesamt 

Gesucht: 

- Bandbreite

Bandbreite = 25 * 64kBit/s * 1.1 
Bandbreite = 1600 kBit/s * 1.1 
Bandbreite = 1760 kBit/s 

**5/5 PUNKTE**

### b) 

#### ba) 

Audio wird prioritisert

**3/3 PUNKTE**

#### bb) 

Video Layout 
Videoauflösung 
Framerate 

**3/3 PUNKTE**

### c) 

2.500/4.000 

10 * 2 = 20 Verbindungen 

50.000 / 80.000

**0/2 PUNKTE**

### d) 

Gegeben: 

- 34 MiB/m 
- 5 m 
- 16 Mbit/s 

Gesucht: 

- Dauer 

Daten = ( 5 m * 34 MiB/m )  
Daten = 170 MiB 
Daten = 178,257,920 B = 1,426,063,360 b 
Daten = 1,426 Mbit 

Dauer = 1,426 Mbit / 34 Mbit/s 
Dauer = 42 s

**2/4 PUNKTE**

### e)

QoS prioritisiert gewissen Traffic, basierend auf Protokoll/Art. Dadurch soll Traffic, der in Echtzeit stattfinden soll, wesentlich flüssiger und schneller übertragen werden. Nutzer sollen somit möglichst latenzfrei mit maximaler Qualität kommunizieren können.

**4/4 PUNKTE**

### f) 

VoIP nutzt UDP, um höhere Geschwindigkeiten zu erreichen. UDP garantiert keine korrekte Datenübertragung.

**5/5 PUNKTE**

**21/26 PUNKTE**

**GESAMTPUNKTE: 88**

# WiSO 

## Aufgabe 1 

3

**3.3/3.3 PUNKTE**

## Aufgabe 2 

1

**3.3/3.3 PUNKTE**

## Aufgabe 3 

Gegeben:
- Einlage 375,000 Euro 
- Gewinn 28,125 Euro 

Gesucht:
- Rentabilität

R = 100 / 375,000 * 28,128 
R = 7.5%

**3.3/3.3 PUNKTE**

## Aufgabe 4 

4

**3.3/3.3 PUNKTE**

## Aufgabe 5 

3 -> 4

**0/3.3 PUNKTE**

## Aufgabe 6 

2

**3.3/3.3 PUNKTE**

## Aufgabe 7 

3

**3.3/3.3 PUNKTE**

## Aufgabe 8 

5 -> 2

**0/3.3 PUNKTE**

## Aufgabe 9 

5

**3.3/3.3 PUNKTE**

## Aufgabe 10 

2 
1 
3
2 
3 

**3.3/3.3 PUNKTE**

## Aufgabe 11 

2

**3.3/3.3 PUNKTE**

## Aufgabe 12 

- 537 MA >18, davon 250 MA seit 1/2 Jahr befristet 
- 17 >18 Azubis
- 2 <18 Azubis

11

**3.3/3.3 PUNKTE**

## Aufgabe 13 

3 
5 -> nope 

**?/3.3 PUNKTE**

## Aufgabe 14 

1 -> 4

**0/3.3 PUNKTE**

## Aufgabe 15 

4

**3.3/3.3 PUNKTE**

## Aufgabe 16 

2

**3.3/3.3 PUNKTE**

## Aufgabe 17 

5 (3??)

**3.3/3.3 PUNKTE**

## Aufgabe 18 

4

**3.3/3.3 PUNKTE**

## Aufgabe 19 

3

**3.3/3.3 PUNKTE**

## Aufgabe 20 

2 -> 4

**0/3.3 PUNKTE**

## Aufgabe 21 

2

**3.3/3.3 PUNKTE**

## Aufgabe 22 

2 
6

**3.3/3.3 PUNKTE**

## Aufgabe 23 

2

**3.3/3.3 PUNKTE**

## Aufgabe 24 

5 -> 3

**0/3.3 PUNKTE**

## Aufgabe 25 

1

**3.3/3.3 PUNKTE**

## Aufgabe 26 

6 
3 
4 
2 
1
5 

**3.3/3.3 PUNKTE**

## Aufgabe 27 

5 

**3.3/3.3 PUNKTE**

## Aufgabe 28 

4

**3.3/3.3 PUNKTE**

## Aufgabe 29 

5

**3.3/3.3 PUNKTE**

## Aufgabe 30 

2

**3.3/3.3 PUNKTE**

**GESAMTPUNKTE: 79.2**

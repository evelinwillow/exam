# GA 1 

## Aufgabe 1 

### a) 

- Kosteneinsparung durch weniger Hardware
- Leichtere Verwaltung
- Einfacher für Mitarbeiter -> meh

**4/6 PUNKTE**

### b) 

#### ba) 

- Physische Distanz und Datendurchsatz der Verbindung zwischen den Servern
- Redundanz und evtl. Failover-Clusterung

-> Falsch verstanden :(

**2/4 PUNKTE**

#### bb) 

Hypervisor ermöglicht Virtualisierung mehrerer Server auf einem physischen Gerät/Containerisierung bei z.B. Proxmox

**4/4 PUNKTE**

#### bc) 

Container nutzen den selben Kernel wie das Host-OS, sind aber per chroot isoliert. Es handelt sich um abgeschottete Umgebungen, um gewisse Dienste bereitzustellen, sie allerdings vom Host getrennt zu halten. 

**5/5 PUNKTE**

#### bd) 

Gegeben: 
- Kosten vorher: 1359.44 Euro
- 4 Server
    - je 600 W 
- 24/7 Betrieb
- 40 ct / KWh
- Nebenkosten 20 Euro

Gesucht: Differenz Kosten

Kosten_neu = Anzahl Server * Leistungsaufnahme * Betriebszeit_gesamt * Kosten_kwh + Nebenkosten
Kosten_neu = 4 * 600 W * ( 24 * 365 ) * 0.4 Euro + 20 Euro
Kosten_neu = ... ( 8,760 h ) ... 
Kosten_neu = ( ( 2.400 kW * 8,760 h ) / 1000 ) * 0.4 Euro + 20 Euro
Kosten_neu =  21,024 kWh * 0.4 Euro + 20 Euro
Kosten_neu = 8,429.6 Euro 

Dif = 8,429.6 - 1359.44 = 7,050.16 Euro -> Nebenkosten falsch! 

**5/6 PUNKTE**

**20/25 PUNKTE**

## Aufgabe 2 

### a)

Vertraulichkeit gewährleistet, dass Daten nur vom vorgesehenen Empfänger und/oder mit der Verarbeitung beauftragten Personen eingesehen werden dürfen.
Integrität gewährleistet, dass die Daten vollständig und unverändert vorliegen.
Authentizität gewährleistet, dass es sich beim Absender und Empfänger um die tatsächlich vorgesehenen Personen handelt.

**6/6 PUNKTE**

### b)

DES ist veraltet und kommt damit nicht in Frage.
AES ist der gängige Standard (auch wenn es mittlerweile bessere gibt)
RSA ist etwas weniger sicher als AES -> keine Encryption!!

Empfehlung: mindestens AES-256

**5/7 PUNKTE**

### c)

#### ca)

Meyer ist Eigentümer, hat dadurch allerdings keine Leserechte und ist wohl kein Mitglied der Gruppe alster 
Zur Gruppe hinzufügen, oder `chmod +r <datei>` (da sowieso jeder Leserechte hat, was dumm ist.)

**3/3 PUNKTE**

#### cb) 

4 - r 
2 - w 
1 - x

Eigentümer: 6 = 4 + 2 -> rw 
Gruppe: ^^^ 
Andere: r 

**6/6 PUNKTE**

**20/22 PUNKTE**

## Aufgabe 3 

### a)

```c
sumLast = 0;

for ( int n = 0; n < 6: n++ )
{
    sumLast = sumLast + maxRAM20231119[n];
}
mwVormittag = sumLast / 6;
```
---
```c
sumLast = 0;

for ( int m = 20; m < 24: m++ )
{
    sumLast = sumLast + maxRAM20231119[m];
}
mwNachmittag = sumLast / 4;
```
---
```c 
Console.WriteLine("Mittelwert Vormittag: " + mwVormittag);
Console.WriteLine("Mittelwert Nachmittag: " + mwNachmittag");
```

**17/17 PUNKTE** -> technically 0, aber Aufgabe nicht wirklich gelesen da Kindergarten

### b)

Pseudocode ist nicht von bestimmtem Syntax abhängig und kann daher von jedem, der eine beliebige Programmiersprache kann, Problemlos verstanden werden (Ausser eventuell Haskell-Programmierern oder ähnliche Esolangs)
Pseudocode kann sehr schnell erstellt werden und "korrektheit" des Codes ist nicht so relevant wie lesbarkeit

**6/6 PUNKTE**

### c)

Segfault - Zugriff auf Speicher, der nicht vom Programm alloziiert wurde
Aufruf einer Funktion, die nicht definiert wurde (streng genommen auch ein Segfault, da Funktionen auch nur Pointer auf Speicherplatz sind)

**4/4 PUNKTE**

**27/27 PUNKTE**

## Aufgabe 4 

### a)

VD 5 -> 5D4

Differenzielle Backups speichern alle Änderungen seit dem letzten Vollbackup

**6/6 PUNKTE**

### b)

Personenbezogene Daten müssen anonymisiert werden

**2/4 PUNKTE**

### c) 

Zuordnungseinheiten sollten immer entsprechend der grösse der physischen Sektoren/Blöcke auf den tatächlichen Festplatten eingestellt werden. Daraus resultieren logischerweise aus die korrekten Anwendungsfälle.

-> Kleine Daten: Kleinere Einheiten und vice verstanden

**0/4 PUNKTE**

### d)

- Einheitliche Zustände 
- Einfachere Administration
- Gesteigerte Sicherheit

**4/6 PUNKTE**

### e) 

Solange sich die "major revision number" nicht verändert, kann der Nutzer die Software über einen auf der Website des Herstellers bereitgestellten Patch kostenfrei Updaten.
Falls sie sich verändert hat, kann der Nutzer eine vergünstigte Lizenz für die neue Version erwerben.

**6/6 PUNKTE**

**18/25 PUNKTE**

**GESAMTPUNKTE: 85/100**

# GA 2 

## Aufgabe 1 

### a)

#### aa)

172.16.64.0/22 über 10.2.2.2 falsch -> korrekt: über 10.1.1.2 
192.168.100.0/24 über 10.1.1.2 falsch -> korrekt: über 10.2.2.2 

**4/4 PUNKTE**

#### ab)

Automatische Eintragung von Routen und Optimisierung bzw. Korrektur bei Routenausfall

**6/6 PUNKTE**

#### ac) 

Zeigt an, wie schnell die Route ist -> wichtig für optimierung -> niedrigste Cost wird bevorzugt

**4/4 PUNKTE**

#### ad) 

VPN

**2/2 PUNKTE**

### b)

#### ba)

WPA-Enterprise benutzt z.B. RADIUS-Server, Verbindung nicht via Netzwerkpasswort, sondern User-Login

**2/3 PUNKTE**

#### bb)

Sicherer, da weniger Risiko bei Leak von Key
Nutzer können individuell verwaltet werden

**2/2 PUNKTE**

**20/21 PUNKTE**

## Aufgabe 2 

### a)

#### aa)

NAT -> Network Address Translation: Weiterleitung bestimmter Ressourcen/Domains/Addressen auf bestimmte Hosts 

**2/4 PUNKTE**

#### ab) 

Quell-IP: 172.16.32.150
Ziel-IP: 172.16.32.1
Ziel-Port: 443

**2/3 PUNKTE**

#### ac) 

Quell-IP: 203.0.113.13
Ziel-IP: 135.125.254.20
Ziel-Port: 443

**5/5 PUNKTE**

#### ad)

Ephemeral Ports -> Zufallsgeneriert in bestimmter Reichweite (variiert je nach OS)

**2/2 PUNKTE**

### b)

#### ba)

Ziel-IP: 203.0.113.13
Quell-Port: wat?
Ziel-Port: 22 

**4/4 PUNKTE**

#### bb) 

Quell-IP: 203.0.113.13
Ziel-IP: 10.10.10.2
Quell-Port: verarschen?
Ziel-Port: 22 

**3/4 PUNKTE**

### c)

Grösste Klasse -> Maximale Hosts, da viele Mobilfunkgeräte in einer Zelle 

Keine statische IP möglich, Endgerät nicht direkt ansprechbar

**3/3 PUNKTE**

**21/25 PUNKTE**

## Aufgabe 3 

### a)

Kupfer unterstützt kaum bis gar nicht 10Gbit 
Zukunftssicher

**3/6 PUNKTE**

### b)

#### ba)

Etwas leichtere Verwaltung (keine Berechnung wie Subnetting)
?? 

**2/4 PUNKTE**

#### bb) 

VLAN-Tagging?

**2/2 PUNKTE**

#### bc) 

VLAN-Tagging???

**1/3 PUNKTE**

### c)

Eventuell läuft kein DNS-Resolver/Forwarding-Dienst auf dem Router (es wurde nicht erwähnt, ob der DNS-Server ebenfalls korrekt eingetragen wurde)

**3/3 PUNKTE**

#### cb)

192.168.100.212

**2/2 PUNKTE**

#### cc)

11 

**2/2 PUNKTE**

#### cd)

Kein DNS 

DNS einschalten 

**0/6 PUNKTE oder 6/6 PUNKTE**

**15/28 PUNKTE oder 21/28 PUNKTE**

## Aufgabe 4 

### a)

Certs sind eindeutig einer CA zugeordnet und müssen von dieser Signiert werden, was durch asym. Verschlüsselung nicht gespooft werden kann
Certs lassen sich einfacher zentral verwalten und z.B. deaktivieren

**4/4 PUNKTE**

### b)

#### ba)

Hashfunktionen gewährleisten mehrere Schutzziele wie z.B. Authentiziät und Integrität 

**4/4 PUNKTE**

#### bb) 

Hash-Funktionen müssen eindeutige, "unique" Werte ergeben -> Collision-Attack: Bruteforce, um eine Quelle zu finden, aus der sich das selbe Ziel errechnen lässt -> Authenticity nicht mehr gewährleistet

**4/4 PUNKTE**

### c)

#### ca)

priv Key -> CA kompromittiert

**4/4 PUNKTE**

#### cb) 

Neuen priv. key erstellen, alle Certs neu ausstellen

**4/4 PUNKTE**

### d)

#### da)

Absicherung des Key Exchange

**1/3 PUNKTE**

#### db)

Symmetrische Schlüssel sind anfällig dafür, abgefangen zu werden, da sie unverschlüsselt übertragen werden (Ohne Schlüssel keine verschlüsselung)

**0/3 PUNKTE**

**21/26 PUNKTE**


**GESAMTPUNKTE: 77 oder 83**

# WiSO 

## Aufgabe 1 

**/3.3 PUNKTE**

## Aufgabe 2 

**/3.3 PUNKTE**

## Aufgabe 3 

**/3.3 PUNKTE**

## Aufgabe 4 

**/3.3 PUNKTE**

## Aufgabe 5 

**/3.3 PUNKTE**

## Aufgabe 6 

**/3.3 PUNKTE**

## Aufgabe 7 

**/3.3 PUNKTE**

## Aufgabe 8 

**/3.3 PUNKTE**

## Aufgabe 9 

**/3.3 PUNKTE**

## Aufgabe 10 

**/3.3 PUNKTE**

## Aufgabe 11 

**/3.3 PUNKTE**

## Aufgabe 12 

**/3.3 PUNKTE**

## Aufgabe 13 

**/3.3 PUNKTE**

## Aufgabe 14 

**/3.3 PUNKTE**

## Aufgabe 15 

**/3.3 PUNKTE**

## Aufgabe 16 

**/3.3 PUNKTE**

## Aufgabe 17 

**/3.3 PUNKTE**

## Aufgabe 18 

**/3.3 PUNKTE**

## Aufgabe 19 

**/3.3 PUNKTE**

## Aufgabe 20 

**/3.3 PUNKTE**

## Aufgabe 21 

**/3.3 PUNKTE**

## Aufgabe 22 

**/3.3 PUNKTE**

## Aufgabe 23 

**/3.3 PUNKTE**

## Aufgabe 24 

**/3.3 PUNKTE**

## Aufgabe 25 

**/3.3 PUNKTE**

## Aufgabe 26 

**/3.3 PUNKTE**

## Aufgabe 27 

**/3.3 PUNKTE**

## Aufgabe 28 

**/3.3 PUNKTE**

## Aufgabe 29 

**/3.3 PUNKTE**

## Aufgabe 30 

**/3.3 PUNKTE**

**GESAMTPUNKTE:**

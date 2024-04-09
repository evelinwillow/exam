# PRÜFUNGSTHEMEN AP2

## Networking

### OSI Model

Data type   Layer                   Protocols

DATA        Application layer       HTTP, FTP, DNS, Telnet
DATA        Presentation layer      SSL, TLS
DATA        Session layer           NetBIOS, SMB, RPC, SCP, SIP
SEGMENTS    Transport layer         TCP, UDP
PACKETS     Network layer           IP, ARP, IGMP, ICMP
FRAMES      Data link layer         Ethernet, PPP, ATM
BITS        Physical layer          RS 232, CAT5, CAT6, DSL

### Common ports

#### Email

- SMTP      25
- POP3      110
- IMAP4     143
- SMTPs     587
- POP3s     995

---

#### Web

- HTTP      80
- HTTPS     443

---

#### Networking

- DNS       53

---

### DMZ

Als *DMZ* wird ein Netzwerk bezeichnet, welches sich zwischen dem eigentlichen Netzwerk und dem Internet befindet.
Es dient dazu, das betriebsinterne Intranet vor unbefugtem Zugriff zu schützen.
Die DMZ beinhaltet häufig von ausserhalb erreichbare Ressourcen, wie z.B. DNS, FTP-Server, Mail-Server, Proxy-Server, VoIP-Services und Web-Server.
Diese Server werden isoliert und haben nur beschränkten bis gar keinen Zugriff auf das interne Netzwerk.
Normalerweise befindet sich die DMZ zwischen zwei Firewalls. alternativ reicht auch eine Firewall; hier wird die DMZ über ein Subnet realisiert, welches keinen Zugriff auf das restliche Netzwerk hat. 

Häufig wird in der DMZ ein Proxy-Server installiert; dieser dient dazu, den Traffic zwischen LAN und DMZ zu filtern, und Nutzeraktivität zu überwachen und protokollieren.

Vorteile einer DMZ beinhalten:
- Implementierung von Access Control
- Verhinderung von Network Reconnaissance
- Blockierung von IP-Spoofing

### *Routing*

Es gibt grob unterteilt zwei Arten von Routing: *static routing* und *dynamic routing*.

Im folgenden Beispiel wird die folgende Netzwerktopologie benutzt:

```
        192.168.12.1                                          192.168.12.2
        fa16.3e02.83a1                                        fa16.3e01.0c98
[R1] -- Gi0/2 ----------------------------------------------- Gi0/2 -- [R2]
  |                                                                     |
  Gi0/1                                                                 Gi0/1
  192.168.1.254                                                         192.168.2.254
  fa16.3e3f.fd3c                                                        fa16.3e3c.7da4
  |                                                                     |
  |                                                                     |
  |                                                                     |
  192.168.1.1                                                           192.168.2.2
  fa16.3e87.9c2a                                                        fa16.3e4a.f598
  |                                                                     |
[H1]                                                                   [H2]
```

Hier sind zwei Host-Computer (H1 und H2) dargestellt. H1 wird ein IP-Paket an H2 schicken, welches von R1 und R2 geroutet werden muss.

#### IP Routing-Prozess

##### H1

Als erstes erstellt H1 ein IP-Paket mit der eigenen IP-Adresse (*192.168.1.1*) als Quelle und H2 (*192.168.2.2*) als Ziel. Die erste Frage, die H1 beantwortet ist folgende:

- Ist das Ziel lokal oder remote?

H1 beantwortet diese Frage, indem die eigene IP-Adresse, Subnetzmaske, und die Ziel-IP betrachtet werden. 
H1 ist hier im Netzwerk *192.168.1.0/24*, also sind alle Adressen von *192.168.1.1* bis *192.168.1.254* lokal. 
Da unser Ziel (*192.168.2.2*) ausserhalb des lokalen Subnetzes ist, müssen wir den *default gateway* benutzen.
H1 wird nun das erstellte IP-Packet in ein Ethernet-Frame verpacken; dazu wird unter anderem die eigene Quell-MAC-Adresse benutzt. Anschliessend fragt H1 die zweite Frage:

- Kenne ich die Ziel-MAC-Adresse des default gateway?

H1 schaut in der ARP-Tabelle nach. Falls ein Eintrag gefunden wird, wird dieser benutzt; falls nicht, wird eine ARP-Anfrage gestellt. Nun haben wir einen kompletten Ethernet-Frame, welcher ein IP-Paket mit den folgenden Adressen beinhaltet:

```
| Source:        | Destination:   | Source:       | Destination:   |
| fa16.3e87.9c2a | fa16.3e3f.fd3c | 192.168.1.1   | 192.168.2.2    |
```

Dieser Frame wird jetzt zu R1 geschickt.

##### R1

Als erstes überprüft R1 die FCS (*Frame Check Sequence*) des Ethernet-Frames auf Korrektheit:

```
| Preamble | SFD | Destination | Source | Type | IP Packet | FCS |
                                                         ^^^^^^^
```


## Hardware

### RAID

#### RAID level

##### RAID 0 aka JBOD

**Block-level striping without parity or mirroring**
Bei RAID 0 (auch bekannt als *stripe set* oder *striped volume*) werden Daten *gleichmässig über mehrere Datenträger verteilt*, *ohne Parität*, Redundanz, oder Fehlertoleranz. 
Falls ein Datenträger ausfällt, fällt das gesamte Array aus. 
Es werden *mindestens 2 Platten benötigt*, und der *gesamte Speicherplatz* kann genutzt werden.
Lese- und Schreibgeschwindigkeit sind teilweise schneller als komplett ohne RAID.

##### RAID 1

**Mirroring without parity or striping**
Als RAID 1 wird eine *exakte Kopie* (auch *mirror* genannt) auf *zwei oder mehr Festplatten* bezeichnet; eine klassische Konfiguration besteht aus 2 Festplatten. Sie bietet *keine Parität* und *kein Striping*.
Ein RAID 1 Array ist immer nur *so gross wie der kleinste enthaltene Datenträger*.
Lesegeschwindigkeit kann sehr schnell sein, allerdings ist die Schreibgeschwindigkeit normal.

##### RAID 4

**Block-level striping with dedicated parity**
Bei RAID 4 wird auf *Block-level* gestriped, und es wird eine *dedizierte Paritätsplatte* eingesetzt. Dadurch ist die *Lesegeschwindigkeit relativ gut*, während die *Schreibgeschwindigkeit niedrig* ist, da die gesamten Paritätsdaten auf eine einzige Festplatte geschrieben werden. Ein Vorteil von RAID 4 ist die Möglichkeit, leicht im laufenden Betrieb den verfügbaren Speicherplatz erweitern zu können.
Die Grösse eines RAID 4-Arrays ist die *Summe der Platten minus einer Platte* für Parität.

##### RAID 5

**Block-level striping with distributed parity**

In einem RAID 5-Array wird der selbe Ansatz wie in einem RAID 4-Array genutzt, allerdings werden die *Paritätsdaten auf alle Festplatten verteilt*. Es werden *mindestens 3 Platten* benötigt, und der *Ausfall einer Platte kann toleriert werden*. Im Vergleich zu RAID 4 wird allerdings der Schreibaufwand der Paritätsdaten gleichmässig auf alle Festplatten verteilt. Dadurch ist RAID 5 dazu in der Lage, mit *fast so guter Geschwindigkeit wie RAID 0 zu schreiben*. 
Die Grösse eines RAID 5-Arrays ist ebenfalls die *Summe der Platten minus einer Platte* für Parität.

##### RAID 6

**Block-level striping with double distributed parity**

RAID 6 erweitert RAID 5 um eine *weitere Paritätsplatte*. Dadurch kann der Ausfall von *zwei Festplatten* toleriert werden, allerdings sind auch *mindestens 4 Festplatten* nötig. *Lesegeschwindigkeit ist vergleichbar mit RAID 5*, allerdings ist die *Schreibgeschwindigkeit durch weitere Paritätsberechnungen etwas niedriger*. Die Grösse eines RAID 6-Arrays ist die *Summe der Platten minus zwei Platten für Parität*.

##### RAID 10

Bei RAID 10 handelt es sich um eine mögliche Kombination der RAID-level. Dabei werden *gespiegelte Paare* an Festplatten *in einem RAID 0* zusammengefasst. Im Gegensatz zu RAID 5 muss hier allerdings *keine Parität* berechnet werden, wodurch *Schreibvorgänge schneller* sind. Der Nachteil eines RAID 10-Arrays ist allerdings, dass nur *50% des Gesamtspeichers* nutzbar sind.
Es kann der *Ausfall einer Festplatte* toleriert werden. In diesem Fall allerdings ist die *Lesegeschwindigkeit nicht beeinträchtigt*, da die Daten nicht erst aus Parität berechnet werden müssen. RAID 10 benötigt *mindestens 4 Festplatten*.

- USV

## Software

- *Backups*
    - Arten
    - Berechnung Grösse, Transfer
- Struktogramme
    - Syntax

## Mathe

- Unit conversion (MiB zu MB, Mbit/s...)

## WiSo

- Versicherungsbeiträge

## Security

- Inhalte eines Zertifikats

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


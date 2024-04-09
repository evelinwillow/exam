# PRÜFUNGSTHEMEN AP2

## Networking

### OSI Model

```
Data type   Layer                   Protocols                       Role

DATA        Application layer       HTTP, FTP, DNS, Telnet          Human/Computer interaction layer
DATA        Presentation layer      SSL, TLS                        Ensures a usable data format; handles encryption
DATA        Session layer           NetBIOS, SMB, RPC, SCP, SIP     Maintains connections and controls ports and sessions
SEGMENTS    Transport layer         TCP, UDP                        Transmits data using protocols such as TCP and UDP
PACKETS     Network layer           IP, ARP, IGMP, ICMP             Decides the physical path data will take
FRAMES      Data link layer         Ethernet, PPP, ATM              Defines the format of the data on the network
BITS        Physical layer          RS 232, CAT5, CAT6, DSL         Transmits raw bit stream over the physical medium 
```

### Common ports

```
Protocol    Port        Role

# Email
SMTP        25          Simple mail transfer protocol
POP3        110         Post Office Protocol; erlaubt Zugriff auf die Inbox auf einem Email-Server
IMAP4       143         Internet Mail Access Protocol; ermöglicht das Lesen von von Emails, ohne sie herunterladen oder zwischenspeichern zu müssen.
SMTPs       587         Simple Mail Transfer Protocol Secure; Modernes, verschlüsseltes SMTP
POP3s       995         Post office Protocol Secure; Verschlüsseltes SMTP

# VoIP
SIP         5060, 5061  Session Initiation Protocol; wird benötigt, um z.B. VoIP-Sessions zu initiieren, aufrecht zu erhalten, und zu schliessen.
RTP         ephemeral   Real-Time Transport Protocol; Nötig für z.B. Audio- und Videostreams.

# Web
HTTP        80          Hypertext transfer protocol; Web
HTTPS       443         HTTP Secure; HTTP mit SSL

# Networking
DNS         53          Domain Name Service; löst Domain-Namen zu IP-Adressen auf
SSH         22          Secure Shell; Verschlüsseltes Tunneling-Protokoll
NTP         123         Network Time Protocol; Erlaubt Computern, ihre Uhr zu synchronisieren
BGP         179         Border Gateway Protocol; Nötig, um effiziente Routen zwischen grossen Netzwerken (autonomen Systemen) zu erstellen
ISAKMP      500         Internet Security Association and Key Management Protocol (nötig für IPSec)
RDP         3389        Remote Desktop Protocol; Windows-Remotedesktop-Protokoll
NetBIOS     137         Network Basic Input and Output System; API zur Kommunikation von Anwendungen in lokalen Netzwerken
RPC         135         Remote Procedure Call; ermöglicht IPC

# Data transfer/File-Sharing
FTP         20, 21      File Transfer Protocol; zum Transferieren von Daten zwischen Server und Client
SMB         445, 139    Server Message Blocks; Netzwerk-Filesharing-Protokoll, ermöglicht auch Drucker- und Device-Sharing.
SCP         22          Secure Copy; File Transfer basierend auf SSH
```

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

---

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

### USV

USV werden in 3 Arten unterteilt:

- VFD (Voltage Frequency Dependent), auch bekannt als Offline-USV
- VI (Voltage Independent), auch bekannt als Line Interactive-USV
- VFI (Voltage and Frequency Independent), auch bekannt als Online-USV

Basierend auf der Art kann eine USV gegen verschiedene Arten von Netzstörung schützen:

```
Störungstyp             Dauer               Definition

Netzausfall             mehr als 10ms       Netzausfall wird als Nullspannungsbedingung definiert
Spannungsschwankung     weniger als 16ms    Einbrüche, die kurz unter dem Normalwert liegen. Kann beim Einschalten grosser Anlagen auftreten.
Spannungsspitzen        4ms bis 16ms        Oft durch statische Entladungen verursacht
Spannungsstösse         weniger als 4ms     Plötzliche und kurzfristige Spitzen. Treten z.B. bei Blitzeinschlag auf.
Unterspannungen         forlaufend          Spannung fällt unter zulässigen Grenzwert
Überspannung            fortlaufend         Wenn z.B. grosse Anlagen aktiviert werden, kann der Normalbetrieb auf über 100% steigen.
Frequenzschwankungen    sporadisch          Frequenz weicht von normalerweise konstanten Netzfrequenz ab
Spannungsverzerrung     periodisch          Wird auch als Störspannung bezeichnet.
```

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



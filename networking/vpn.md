# VPN

Die meisten VPN-Protokolle funktionieren auf Schicht 3 des OSI-Modells. Viele Router unterstützen heutzutage VPN-Protokolle.

## VPN-Typen

### LAN to LAN / Site to Site

Baut eine Verbindung zwischen zwei Gateways auf.
Diese Endgeräte (VPN-Gateways) werden auch als VPN-terminating device bezeichnet.
Das VPN ist also transparent, und die Endgeräte müssen nicht wissen, dass über ein VPN kommuniziert wird.

```
[ Host ] <-LAN-> { Router } <-WAN-> { Router } <-LAN-> [ Hosts ]
                 |---------------------------|
```

### Remote Access / End to Site

Erlaubt dem Host, auf ein remotes Netzwerk zuzugreifen.
Das Endgerät benötigt dafür allerdings einen VPN-Client und übernimmt die Verschlüsselung selber.

```
[ Host ] <-LAN-> { Router } <-WAN-> { Router } <-LAN-> [ Hosts ] 
|--------------------------------------------|
```

### End to End

Verbindet zwei Hosts und verschlüsselt die gesamte Kommunikation zwischen ihnen. (z.B. ssh)
```
[ Host ] <-LAN-> { Router } <-WAN-> { Router } <-LAN-> [ Hosts ]
|--------------------------------------------------------------| 
```

## VPN-Protokolle

### IPSec

IPSec ist eine Sammlung von Protokollen und Funktionen zur Realisierung von VPNs, und kein Protokoll -> Protokoll-Suite
IPSec ist ein IETF(Internet Engineering Task Force)-Standard (RFC 2401-2412)
Der Schlüsselaustausch ist durch Diffie-Hellman gesichert.
IPSec gewährleistet folgende Schutzziele:

- Vertraulichkeit durch Verschlüsselung 
- Integrität durch Hash-Funktionen
- Authentizität durch Identititätsüberprüfung 

IPSec besteht aus folgenden Aufgaben:

- Verschlüsselung mit DES, AES, ...
- Prüfsummen mit MD5, SHA 
- Authentifizierung mit RSA, Pre-Shared-Key
- Schlüsselaustausch mit DH1, DH2, DH5, DH14, ...

All diese Parameter müssen für eine VPN-Verbindung ausgehandelt werden (*Security Association*).

### openVPN

### wireguard

### SSL-VPN 

Funktionert auf Basis von HTTPS

### PPTP

Veraltet, sollte nicht mehr genutzt werden.

### MPLS

### GRE

### L2F

Cisco-Protokoll

### L2TP 

Microsoft-Protokoll

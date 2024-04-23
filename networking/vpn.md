# VPN

## VPN-Typen

### Remote Access

Erlaubt dem Host, auf ein remotes Netzwerk zuzugreifen.

```
[ Host ] <-LAN-> { Router } <-WAN-> { Router } <-LAN-> [ Hosts ] 
|--------------------------------------------|
```

### LAN to LAN 

Baut eine Verbindung zwischen zwei Routern auf (verbindet beide LANs miteinander)
```
[ Host ] <-LAN-> { Router } <-WAN-> { Router } <-LAN-> [ Hosts ]
                 |---------------------------|
```

### End-to-End

Verbindet zwei Hosts und verschlüsselt die gesamte Kommunikation zwischen ihnen. (z.B. ssh)
```
[ Host ] <-LAN-> { Router } <-WAN-> { Router } <-LAN-> [ Hosts ]
|--------------------------------------------------------------| 
```

## VPN-Protokolle

### IPSec

### openVPN

### wireguard

### SSL-VPN 

Funktionert auf Basis von HTTPS

### PPTP

Veraltet, sollte nicht mehr genutzt werden.

### L2F

Cisco-Protokoll

### L2TP 

Microsoft-Protokoll

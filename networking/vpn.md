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





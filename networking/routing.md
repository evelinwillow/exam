# Routing

## Default Gateway

Als ein *Gateway* ist ein System definiert, welches Netzwerke unter Zuhilfename verschiedener Transportprotokolle so miteinander verbinden, dass Informationen zwischen den Netzwerken ausgetauscht werden können.
Somit ist ein Gateway eine TCP/IP-Node mit Routingfunktion, und ein Gateway kann als eine Art Router betrachtet werden.

Als *Router* definiert ist ein System, welches Pakete mithilfe von logischen Netzwerkadressen, meist IP-Adressen, zwischen zwei oder mehr Netzwerksegmenten versendet.

Dieser Gateway ist der Standardgateway für ein Ziel, das dem Absender nicht bekannt ist und damit der Punkt, an dem Pakete, die an Ziele ausserhalb des lokalen Netzwerkes adressiert sind, das Netzwerk verlassen.

## Routing-Tabelle

Auf Windows kann über *route print* die Routingtabelle angezeigt werden. 

```
Description         Network Destination	    Netmask             Gateway	            Interface	        Metric
Default route	    0.0.0.0                 0.0.0.0             192.168.69.111      192.168.69.111      20
Loopback network    127.0.0.1	            255.0.0.0           127.0.0.1           127.0.0.1	        1
Local network       192.168.69.0            255.255.255.0       192.168.69.111	    192.168.69.111      20
Local IP address    192.168.69.111          255.255.255.255     127.0.0.1           127.0.0.1	        20
Subnet broadcast    192.168.69.255          255.255.255.255     192.168.69.111	    192.168.69.111      20
Multicast address   224.0.0.0               240.0.0.0           192.168.69.111	    192.168.69.111      20
Limited broadcast   255.255.255.255         255.255.255.255     192.168.69.111	    192.168.69.111      1
```

Der Wert "Metric" für *loopback* und *limited broadcast* ist immer 1. 
Alle anderen Adressen haben eine Metrik basierend auf den Kosten, die die Nutzung der Route mit sich bringt.

Mit z.B. mehreren Netzwerkadaptern würde die Routingtabelle verschiedene Metriken für die verschiedenen Default-Routen anzeigen, aber nur eine würde genutzt werden:

```
Description         Network Destination	    Netmask             Gateway	            Interface           Metric
Default route       0.0.0.0                 0.0.0.0             192.168.69.111      192.168.69.111      20
Default route	    0.0.0.0                 0.0.0.0             192.168.70.100      192.168.70.100      30
Loopback network    127.0.0.1               255.0.0.0           127.0.0.1           127.0.0.1           1
Local network       192.168.69.0            255.255.255.0       192.168.69.111      192.168.69.111      20
Local IP address    192.168.69.111          255.255.255.255     127.0.0.1           127.0.0.1           20
Local network       192.168.70.0            255.255.255.0       192.168.70.100      192.168.70.100      30
Local IP address    192.168.70.111          255.255.255.255     127.0.0.1           127.0.0.1           30
Subnet broadcast    192.168.69.255          255.255.255.255     192.168.69.111      192.168.69.111      20
Multicast address   224.0.0.0               240.0.0.0           192.168.69.111      192.168.69.111      20
Multicast address   224.0.0.0               240.0.0.0           192.168.70.100      192.168.70.100      20
Limited broadcast   255.255.255.255         255.255.255.255     192.168.69.111      192.168.69.111      1
Limited broadcast   255.255.255.255         255.255.255.255     192.168.70.100      192.168.70.100      1
```

In diesem Beispiel ist die Metrik für die default Route des zweiten Netzwerkes höher. Daher wird der Netzwerkadapter des ersten Netzwerkes präferiert. 
Der zweite Gateway wird nie benutzt werden und ist daher nicht nötig.

Mit dem Kommado `route add -p <Ziel> <Netzmaske> <Gateway> <Interface> <Metrik>` kann eine neue Route hinzugefügt werden. 
Der Switch `-p` sorgt hier dafür, dass die Route persistent ist. Das bedeutet, dass die Route bei einem Neustart nicht gelöscht wird.

## IP Routing-Prozess

Es gibt grob unterteilt zwei Arten von Routing: *static routing* und *dynamic routing*. 
Beim dynamischen Routing werden Routen, die dem Router bekannt werden, automatisch in die Tabelle eingetragen, und der Router sucht dynamisch die beste Route selber. 


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

### Zusammenfassung

Der Host, der ein Paket verschicken möchte, muss erst eine simple Frage beantworten:

- Ist das Ziel im lokalen Subnet?
    - Falls ja: Schau in der ARP-Tabelle nach, ob die Ziel-IP in der Tabelle enthalten ist, und nutze die entsprechende MAC-Adresse im Ziel-Feld des Ethernet-Frames.
- Ist das Ziel in einem remoten Subnet?
    - Falls ja: Schau in der ARP-Tabelle nach, ob die IP-Adresse des *default gateways* enthalten ist, und nutze die entsprechende MAC-Adresse im Ziel-Feld des Ethernet-Frames.

Der Router führt folgende Schritte aus:

- FCS (Frame Check Sequence) des Ethernet-Frames überprüfen und falls inkorrekt, Frame verwerfen
- Überprüfen, ob die Zieladresse des Frames eine der folgenden ist:
    - MAC-Adresse des Routers
    - Broadcast-Adresse des Subnetzes, in dem das Interface ist
    - Eine Multicast-Adresse, auf die wir hören
- IP-Paket entkapseln und Frame verwerfen
- In der Routingtabelle nach einer passenden Adresse schauen, und das das ausgehende Interface und optional den next hop ermitteln
- TTL des IP-Headers verringern und Checksum neu berechnen
- IP-Paket in einen neuen Frame kapseln
- In der ARP-Tabelle nach der Ziel-Adresse oder dem next hop suchen
- Den Frame verschicken

---

### H1

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

---

### R1

Als erstes überprüft R1 die FCS (*Frame Check Sequence*) des Ethernet-Frames auf Korrektheit:

```
| Preamble | SFD | Destination | Source | Type | IP Packet | FCS |
                                                           ^^^^^^^
```

Falls die FCS inkorrekt ist, wird der Frame direkt verworfen. Es gibt keine error correction für Ethernet; das ist etwas, worum sich ausschliesslich höhere Protokolle kümmern, wie z.B. *TCP* auf dem *transport layer*.
Falls die FCS korrekt ist, wird der Frame verarbeitet, falls:

- Die Ziel-MAC des Frames die *MAC des Interfaces des Routers* ist
- Die Ziel-MAC des Frames die *Broadcast-Adresse des Subnets* ist, mit dem das Interface verbunden ist
- Die Ziel-MAC des Frames eine *Multicast-Adresse* ist, auf die der Router hört.

In diesem Fall entspricht die Ziel-MAC der MAC-Adresse des GigabitEthernet 0/1-Interfaces von R1; daher wird der Frame verarbeitet. Das IP-Paket wird entkapselt, und der Frame wird weggeworfen.

```
| Preamble | SFD | Destination | Source | Type | IP Packet | FCS |
                                               ^^^^^^^^^^^^^
```

Nun schaut der Router sich die *header checksum* des IP-Paketes an.

```
| Version | Header Length | Type of Service | Total Length | ID | IP Flags | Fragment Offset | TTL | Protocol | Header Checksum | Source | Destination | IP Option |
                                                                                                              ^^^^^^^^^^^^^^^^^^^
```

Falls die Checksum nicht korrekt ist, wird das Paket direkt verworfen. Hier gibt es ebenfalls keine error correction; es wird sich auf die höheren Schichten verlassen. Falls die Checksum korrekt ist, schauen wir uns nun die Ziel-IP an:

```
| Version | Header Length | Type of Service | Total Length | ID | IP Flags | Fragment Offset | TTL | Protocol | Header Checksum | Source | Destination | IP Option |
                                                                                                                                         ^^^^^^^^^^^^^^^
```

R1 schaut nun in seiner Routing-Tabelle nach, ob diese IP bekannst ist:

```
R1#show ip route
Codes:  L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
        D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area 
        N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
        E1 - OSPF external type 1, E2 - OSPF external type 2
        i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
        ia - IS-IS inter area, * - candidate default, U - per-user static route
        o - ODR, P - periodic downloaded static route, H - NHRP, l - LISP
        a - application route
        + - replicated route, % - next hop override, p - overrides from PfR

Gateway of last resort is not set

        192.168.1.0/24 is variably subnetted, 2 subnets, 2 masks
C       192.168.1.0/24 is directly connected, GigabitEthernet0/1
L       192.168.1.254/32 is directly connected, GigabitEthernet0/1
S       192.168.2.0/24 [1/0] via 192.168.12.2
        192.168.12.0/24 is variably subnetted, 2 subnets, 2 masks
C       192.168.12.0/24 is directly connected, GigabitEthernet0/2
L       192.168.12.1/32 is directly connected, GigabitEthernet0/2
```

R1 weiss also, dass es das *192.168.2.0/24*-Netzwerk erreichen kann, und das der *next hop* die IP-Adresse *192.168.12.2* ist. 
R1 schaut nun erneut nach, ob die IP 192.168.12.2 kennt; dies wird als *rekursives Routing* bezeichnet. 
Diese Adresse ist über das Netzwerk *192.168.12.0/24* und das Interface *GigabitEthernet0/2* erreichbar.

Als letztes wird noch die TTL des IP-Paketes verringert. Dadurch muss auch eine neue Header-Checksum berechnet werden.

Anschliessend überprüft R1 seine Arp-Tabelle, ob es einen Eintrag für *192.168.12.2* findet.
Falls dieser Eintrag nicht gefunden wird, versendet R1 einen ARP-Request. 
Das IP-Paket wird nun in ein neuen Ethernet-Frame verpackt:

```
| Source:        | Destination:   | Source:       | Destination:  |
| fa16.3e02.83a1 | fa16.3e01.0c98 | 192.168.1.1   | 192.168.2.2   |
```

Dieser Frame wird nun an R2 verschickt.

---

### R2

R2 wird nun wie R1 folgende Schritte durchführen:

- Die FCS des Frames überprüfen
- IP-Paket entkapseln, Frame verwerfen
- Die Checksum des IP-Headers überprüfen
- Die Ziel-IP überprüfen

In der Routingtabelle finden wir folgende Einträge:

```
R2#show ip route
Codes:  L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
        D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area 
        N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
        E1 - OSPF external type 1, E2 - OSPF external type 2
        i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2
        ia - IS-IS inter area, * - candidate default, U - per-user static route
        o - ODR, P - periodic downloaded static route, H - NHRP, l - LISP
        a - application route
        + - replicated route, % - next hop override, p - overrides from PfR

Gateway of last resort is not set

S       192.168.1.0/24 [1/0] via 192.168.12.1
        192.168.2.0/24 is variably subnetted, 2 subnets, 2 masks
C       192.168.2.0/24 is directly connected, GigabitEthernet0/1
L       192.168.2.254/32 is directly connected, GigabitEthernet0/1
        192.168.12.0/24 is variably subnetted, 2 subnets, 2 masks
C       192.168.12.0/24 is directly connected, GigabitEthernet0/2
L       192.168.12.2/32 is directly connected, GigabitEthernet0/2
```

Das Netzwerk *192.168.2.0/24* ist direkt mit R2 über das GigabitEthernet0/1-Interface verbunden. R2 verringert nun die TTL des IP Paketes, errechnet erneut die IP-Header-Checksum, und überprüft die ARP-Tabelle. Nun wird wieder falls nötig ein ARP-Request versendet, oder das Paket wird direkt in einen neuen Frame verkapselt:

```
| Source:        | Destination:   | Source:       | Destination:  |
| fa16.3e3c.7da4 | fa16.3e4a.f598 | 192.168.1.1   | 192.168.2.2   |
```

Der Frame wird nun an H2 verschickt.

---

### H2

H2 erhält nun den Frame und führt folgende Schritte aus:

- FCS überprüfen
- Überprüft, ob die Ziel-MAC mit der eigenen MAC übereinstimmt
- Entkapselt das IP-Paket
- Überprüft, ob die Ziel-IP mit der eigenen IP übereinstimmt

Anschliessend schaut sich H2 das Protokoll-Feld an, um festzustellen, mit welchem *transport layer protocol* wir arbeiten. Basierend darauf wird das Paket weiter verarbeitet.

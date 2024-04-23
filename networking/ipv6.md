# IPv6 Addressing

## Subnet Mask

IPv6 nutzt CIDR-Notation für Subnet-Masken.

## Kürzen von IPv6-Adressen

- Hextets, die nur aus 0 bestehen, können ausgelassen werden: 

2001:0db8:0000:0000:afff:b222:0000:abcd/64

-> 2001:0db8::afff:b222:0000:abcd/64

Dies kann nur *einmal* pro Adresse geschehen; es können mehrere Hextets, die nur aus 0 bestehen, ausgelassen werden. Es muss immer der grösste Block an Nullen ausgelassen werden.

- Führende Nullen können in jedem Hextet ausgelassen werden:

-> 2001:db8::afff:b222:0:abcd/64

Falls dies in einem Hextet geschieht, in dem nur Nullen vorkommen, allerdings bereits an anderer Stelle Hextets komplett gekürzt wurden, muss eine Null übrig bleiben.

## Globaler Prefix

Der globale Prefix (Mind. 48 Bits lang -> 3 Hextets) wird vom ISP vorgegeben. Da IPv6 einen gigantischen Adressbereich hat, muss nicht mehr mit privaten Adressen gearbeitet werden. Daher kann jeder Host eine global routbare Adresse bekommen.
Bei einem globalen Prefix von 48 Bit und der gängigen Subnetzmaske von /64 können die nächsten 16 Bit für die Subnet-ID genutzt werden. 
Dadurch bleiben 64 Bit für Host- bzw. Interface-ID's übrig.

## Adressbereiche

### Global Unicast

Global Unicast Adressen haben den gegebenen Adressbereich 2000::/3. Sie sind im Internet routbar und beginnen immer mit einer 2 oder einer 3.

### Unique Local

Unique Local Adressen sind das IPv6-Äquivalent vom privaten Adressbereich - FC00::/7. Sie sind im LAN routbar. Sie beginnen immer mit FC oder FD.

### Link Local 

Link Local Adressen haben den Adressbereich FE80::/10 und sind nicht Routbar. Es handelt sich um automatische, lokale IP-Adressen. Es ist das IPv6-Äquivalent von 169.254.x.x-Adressen, welche normalerweise auf fehlerhafte Netzwerkkonfiguration hindeuten.

### Multicast 

Multicast-Adressen haben den Adressbereich FF00::/8. Es handelt sich um Adressen für Gruppen, das IPv6-Äquivalent von der Broadcast-Adresse in IPv4.

### Anycast

Anycast-Adressen haben ebenfalls den Adressbereich 2000::/3. Es handelt sich um geteilte Adressen. Mit IPv6 kann die selbe Adresse an mehrere Geräte vergeben werden; Anycast-Adressen sprechen das am schnellsten erreichbare Gerät mit der Adresse an. Es gibt keinen dedizierten Adressbereich, stattdessen werden normale Global Unicast-Adressen benutzt.

## Subnetting

Zum Subnetting sollten am besten die Hextets in Binär umgerechnet werden.

Beispiel:

```
2019:abcd:0123:1200::/64

-> 2019:abcd:0123:1200::/58 -> also halbes Hextet ( 8 Bit ) *vom Netzanteil* für Subnetze;

2^8 = 256 mögliche Subnetze

Hextet: 1200 -> 12 0000 0000 

12 0000 0000 -> 1200::/64 -> 1. Subnetz
12 0000 0001 -> 1201::/64 -> 2. Subnetz 
12 0000 0010 -> 1202::/64 -> 3. Subnetz 
12 0000 0011 -> 1203::/64 -> 4. Subnetz

...

12 1111 1110 -> 12FE::/64 -> vorletztes Subnetz 
12 1111 1111 -> 12FF::/64 -> letztes Subnetz
```



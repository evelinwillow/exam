# DMZ

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



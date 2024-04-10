# Common ports

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



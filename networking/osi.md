# OSI Model

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

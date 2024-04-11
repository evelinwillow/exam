# Digitale Zertifikate

Ein digitales Zertifikat stellt Informationen über die *Identität von Personen, Objekten oder Unternehmen* zur Verfügung. Es wird von *Zertifizierungsstellen* (*Certificate Authority*) ausgestellt.

Technisch beruhen digitale Zertifikate auf einem Verschlüsselungsverfahren (auch *Public-Key-Verfahren*). 

Es wird hier ein Schlüsselpaar erstellt. 

Der *private Schlüssel* ist nur dem Ersteller selbst bekannt. 
Er wird unter anderem dazu verwendet, um digitale Unterschriften zu erstellen. 
Der öffentliche Schlüssel ist für jeden einsehbar und dient dazu, die digitale Unterschrift zu verifizieren. 

## Inhalt eines digitalen Zertifikats

Es beinhaltet die folgenden Informationen:

- Version
- Seriennummer
- Verwendeter Algorithmus
- Zertifikataussteller
- Zertifikatinhaber
- Zertifikatinhaber-Schlüsselinformationen
    - Public-Key-Algorithmus
    - Public Key des Inhabers
- Gültigkeitsdauer
- digitale Signatur der Zertifizierungsstelle

Aussteller und Inhaber werden jeweils durch eine Reihe von Attributen characterisiert:

- Gebräuchlicher Name
- Organisation
- Organisationseinheit
- Land/Region
- Bundesstaat
- Ort 

## Prüfungsprozess

```
---------------------
| ROOT CERTIFICATE  |
| Digital Signature |
| Public Key        |
---------------------
        |               ----------------------------
        \-------------->| INTERMEDIATE CERTIFICATE |
            decrypts    | Digital Signature        |
                        | Public Key               |
                        ----------------------------
                                    |                  ------------------------
                                    \----------------->| IDENTITY CERTIFICATE |
                                        decrypts       | Digital Signature    |
                                                       | Public Key           |
                                                       ------------------------
```

Ablauf:
- Client erhält Zertifikat vom Server
- Solange weitere Intermediate-Zertifikate benötigt werden: 
    - Intermediate vom Server nutzen oder ggf. herunterladen
    - Client prüft vorheriges Zertifikat mit Intermediate 
    - Client prüft letztes Intermediate mit installiertem Root-Certificate

## Ablauf eines HTTPS-Requests

```
Client            Verbindungsaufbau (Client Hello)              Server
| -----------------------------------------------------------------> |
|                                                                    |
|              Server-Authentifizierung (Server Hello)               |
| <----------------------------------------------------------------- |
|                                                                    |
Zertifikat prüfen                                                    |
Symmetrischen Sitzungsschlüssel erzeugen                             |
|                                                                    |
|       Mit öffentlichem Schlüssel des Servers verschlüsselten       |
|   Sitzungsschlüssel an den Server senden (Client Key Exchange)     |
| -----------------------------------------------------------------> |
|                                                                    |
|                                Verschlüsselten Sitzungsschlüssel mit
|                                     privatem Schlüssel entschlüsseln
|                                                                    |
|           Server bestätigt den geheimen Sitzungsschlüssel          |
| <----------------------------------------------------------------- |
|                                                                    |
|              Verschlüsselte HTTP-Response und -Request             |
| <----------------------------------------------------------------> |
```

- Der Verbindungsaufbau erfolgt über einen HTTPS-Request vom Client zum Server. Beim Client handelt es sich hier meistens um einen Webbrowser oder z.B. curl. Der Server ist demnach ein Webserver.
- Der Client kontaktiert den Server über ein Protokoll mit Verschlüsselungsverfahren. 
- Der Server nimmt die Verbindung an und schickt sein Zertifikat mit dem öffentlichen Schlüssel seines Schlüsselpaares zur Authentifizierung an den Client. 
- Der Client überprüft das Server-Zertifikat und dessen Gültigkeit. 
- Erkennt der Client das Zertifikat als ungültig, wird die Verbindung an dieser Stelle abgebrochen.
- Erkennt der Client das Zertifikat als Gültig, erzeugt der Client den symmetrischen Sitzungsschlüssel.
- Mit dem öffentlichen Schlüssel des Servers verschlüsselt der Client den Sitzungsschlüssel und schickt ihn an den Server, der ihn mit seinem privaten Schlüssel entschlüsseln kann.
- Anschliessend bestätigt der Server den Sitzungsschlüssel. Danach kann eine verschlüsselte Verbindung aufgebaut werden.

## Root-CAs

Root-CAs sind Certificate Authorities, denen der User bedingungslos vertraut. Dazu gehört z.B. GeoTrust oder der Staat der Niederlande. 
Von Ihnen erstellte Zertifikate sind entweder im Betriebssystem oder in der Applikation verankert. Sollte eines dieser Zertifikate nicht mehr aktuell sein, besteht die Gefahr, dass neuere Zertifikate nicht anerkannt werden oder sogar noch CAs vertraut werden, die bereits unsicher sind. 
Somit ist es nicht mehr möglich, eine sichere Verbindung herzustellen.




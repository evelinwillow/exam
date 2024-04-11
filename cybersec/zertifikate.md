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



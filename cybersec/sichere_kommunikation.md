# Sichere Kommunikation

## Schutzziele der Informationssicherheit

Die drei primären Schutzziele der Informationssicherheit sind Vertraulichkeit, Integrität und Verfügbarkeit von Informationen.

- **Vertraulichkeit**: Nur der berechtigte Empfänger kann die Nachricht auch lesen. Diese Anforderung kann durch Verschlüsselung sichergestellt werden.

- **Integrität**: Es muss sichergestellt werden, dass die Nachricht auf dem Übermittlungsweg nicht verändert wurde.

- **Verfügbarkeit**: Informationen sind zu dem gewünschten Zeitpunkt verfügbar.

Je nach Unternehmen sind diese Ziele unterschiedlich zu gewichten. Grundsätzlich steht damit immer der Schutz vor Manipulation, Offenlegung, Datenverlust oder Diebstahl von Informationen im Vordergrund. 

## Erweiterte Schutzziele

- **Authentizität**: Es muss sichergestellt werden, dass die Nachricht wirklich vom angegebenen Absender kommt.

- **Nichtabstreitbarkeit**: Eine Kommunikation kann verbindlich einem Absender zugeordnet werden.

- **Verlässlichkeit**: Ein System übt seine Funktionsweise konsistent aus.

Diese erweiterten Schutzziele spielen nur in bestimmtem Kontext eine wichtige Rolle, wie z.B. Authentizität beim B3S-Standard für Krankenhäuser.

## Schutzbedarfskategorien und Absicherung

Die genannten Schutzziele bilden die Grundlage, um den Schutzbedarf der Assets in der Informationstechnik (z.B. Daten, Anwendungen und Infrastruktur) mit Massnahmen der Sicherheit zu versehen. Bei genauer Betrachtung der einzelnen Themen kann dann eine Schutzbedarfsfeststellung erreicht werden. Die folgenden Kategorien können dabei berücksichtigt werden:

- **Normal**: Die Auswirkungen eines Schadens sind begrenzt und überschaubar.
- **Hoch**: Die Auswirkungen eines Schadens könnwn beträchtlich sein.
- **Sehr hoch**: Die Auswirkungen eines Schadens sind schwerwiegend oder existenzbedrohend.

Nachdem man die Anforderungen an die Assets in eine Kategorie eingeteilt hat, kann eine dedizierte Absicherung erfolgen. 

## Schadensszenarien und ihre Auswirkungen

Die Szenarien sollten auf ihre Auswirkungen hin getestet werden. 
Oft ist dies in der Praxis nur schwer zu realisieren und bedarf dem Zusammenspiel mehrerer interner und externer Experten.
Mache Auswirkung, wie z.B. finanzieller Schaden durch nichterfüllung eines Auftrages, sind oberflächlich betrachtet relativ simpel zu bewerten.
Andere Auswirkungen, wie z.B. Imageverlust durch einen Schaden, sind deutlich schwerer zu beurteilen. So ist hier unter anderem relevant, ob ein Vertrauensverlust sich nur auf eine beschränkte zeitliche Periode bezieht, oder er sich nachhaltig verfestigt. Solch ein Imageverlust bei Kunden kann direkt existenzbedrohend sein und in die Insolvenz führen.

Letztlich sind auch Wechselwirkungen zwischen finanziellem Schaden und Imageverlust zu betrachten.

## Verschlüsselungstechniken

Es soll verhindert werden, dass Unbefugte die Nachricht lesen können.

### Cäsar-Encryption

Verschiebung um 1 Buchstaben

### Symmetrische Verschlüsselung

Absender und Empfänger nutzen den selben Schlüssel. Dieser muss vor der Kommunikation ausgetauscht werden. 
Zur Entschlüsselung wird der selbe schlüssel benutzt; daher muss dieser auf beiden Seiten vorhanden sein. Hierzu muss eine Übertragung des Schlüssels stattfinden. 
Je mehr Teilnehmer an der Kommunikation beteiligt sind, desto höher ist das Risiko, dass der Schlüssel kompromittiert wird. Der Schlüssel kann beim Austausch abgefangen werden.

### Asymmetrische Verschlüsselung

### Hash

### WLAN Sicherheit

#### RADIUS

### IPSEC





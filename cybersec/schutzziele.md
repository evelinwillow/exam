# Schutzziele der Informationssicherheit

Die drei primären Schutzziele der Informationssicherheit sind Vertraulichkeit, Integrität und Verfügbarkeit von Informationen.

- **Vertraulichkeit**: Nur der berechtigte Empfänger kann die Nachricht auch lesen. Diese Anforderung kann durch Verschlüsselung sichergestellt werden.
- **Integrität**: Es muss sichergestellt werden, dass die Nachricht auf dem Übermittlungsweg nicht verändert wurde.
- **Verfügbarkeit**: Informationen sind zu dem gewünschten Zeitpunkt verfügbar.

Je nach Unternehmen sind diese Ziele unterschiedlich zu gewichten. Grundsätzlich steht damit immer der Schutz vor Manipulation, Offenlegung, Datenverlust oder Diebstahl von Informationen im Vordergrund. 
Allerdings kristallisiert sich unter den drei primären Grundwerten die Vertraulichkeit als verletztlichstes Schutzziel heraus.

## Vertraulichkeit

Jeder kommt täglich im beruflichen sowie privaten Umfeld mit vertraulichen Informationen in Berührung. Unter vertraulichen Informationen werden Daten verstanden, die vor Offenlegung gegenüber unberechtigten Parteien zu schützen und deren Zugang zur Verarbeitung nur restriktiv zu genehmigen sind. Je nach Anwendungs- und Bedarfsfall kann es sinnvoll sein, weitere Schutzziele in Betracht zu ziehen. 

### Klassifizierung von Informationen in der IT-Security

Der Prozess in der IT-Security zum Schutz der Vertraulichkeit sieht zunächst vor, Informationen in Kategorien in Bezug auf Schutzbedarf einzuteilen. 
Diese Kategorien werden Klassifizierungen genannt, aus denen sich Sicherungsmassnahmen ableiten lassen. Einige Beispiele für Klassifizierungen sind z.B. "öffentlich", "intern", "vertraulich" oder "streng vertraulich". Je nach Anwendungsfall und Anzahl an beteiligten Parteien (z.B. auch externe Parteien) kann es hilfreich sein, mit weniger als diesen 4 Kategorien zu arbeiten. Daher sollte also schon bereits bei der Definition auf klare Abgrenzung der Klassen zueinander geachtet werden.

### Vorgaben der DSGVO

Während die Informationssicherheit den Prozess selbst in den Vordergrund stellt, formuliert die Datenschutz-Grundverordnung die Forderung nach Vertraulichkeit in Hinblick auf die zu schützenden Daten und die beteiligten Parteien.

> "Personenbezogene Daten müssen in einer Weise verarbeitet werden, die eine angemessene Sicherheit der personenbezogenen Daten gewährleistet, einschließlich Schutz vor unbefugter oder unrechtmäßiger Verarbeitung und vor unbeabsichtigtem Verlust, unbeabsichtigter Zerstörung oder unbeabsichtigter Schädigung durch geeignete technische und organisatorische Maßnahmen ("Integrität und Vertraulichkeit")."

Das Hauptziel der DSGVO ist hier die Verhinderung der Einsichtnahme personenbezogener Daten durch unbefugte Personen. Hier werden sowohl interne (z.B. abteilungsfremde Personen), nicht explizit mit der Verarbeitung gewisser Daten beaufragte Personen einer Abteilung, oder auch externe Personen wie z.B. Dienstleister benannt.

In Abgrenzung zur Informationssicherheit ergeben sich für die nach der DSGVO verarbeiteten personenbezogenen Daten für einige Bereiche sogar rechtliche Pflichten zur Wahrung ver Vertraulichkeit, welche aus der gesetzlichen Pflicht zur Verschwiegenheit abgeleitet werden kann.

### Bedrohungen für die Vertraulichkeit

Zwei typische Beispiele sind z.B. ein achtlos im Papierkorb entsorgtes Dokument, oder eine fälschlich verschickte Email. Diese zeigen auf, wie leicht ein Bruch der Vertraulichkeit von Informationen passieren kann.

Typische Gefahren, welche allerdings auch teilweise in anderen Kategorien auftauchen können, sind:

#### Grundlegende Szenarien durch Fehler und Unachtsamkeit

- **Einsichtnahme in Dokumente ohne Befugnis**: Person A fertigt am Abend noch schnell ein Dokument für den nächsten Tag an und lässt ihn dann zur weiteren Bearbeitung auf dem Schreibtisch offen liegen. Da der Zutritt zum Büro nicht beschränkt ist, und da Person A aufgrund der langen Anwesenheit am Vortag später zur Arbeit erscheint, kann Person B das Dokument am Morgen in einem unbemerkten Moment aus Neugierde oder Böswillen durchlesen.
- **Unbeabsichtigter Abfluss von Informationen**: Monatlich wird ein Newsletter versendet. Bisher wurden Emails individuell an die einzelnen Adressen verschickt. Da die Zahl der Empfänger allerdings stark anstieg, wurde eine Softwarelösung implementiert. Fälschlicherweise wurden die Emails beim ersten Durchlauf allerdings in CC statt BCC verschickt; dadurch ist die Empfängerliste nun als öffentliche Information für jeden sichtbar.
- **Mangelhafte Entsorgung von Datenträgern**: Eine Festplatte wird nach dem Ausbau aus einem Notebook nur formatiert, und anschliessend auf dem Gebrauchtmarkt verkauft. Der Käufer untersucht den Zustand der Festplatte vor der weiteren Verwendung, findet Spuren der flüchtigen Löschung der Daten, und kann sämtliche Dokumente wiederherstellen.

#### Szenarien geleitet durch kriminelle Energie

- **Diebstahl von Daten oder Systemen**: Über das Wochenende ist das Bürogebäude unbewacht und am Sonntagnachmittag bricht ein Einbrecher in ein Büro ein und entwendet den Desktop-Rechner, er aufgrund seines stationären Betriebs über keinerlei Absicherung wie z.B. Datenträgerverschlüsselung verfügt.
- **Infiltration von IT-Systemen zur Erlangung oder Vernichtung von Informationen**: Administrator A bekommt in einer Email einen Hinweis auf eine neue Software. Zum Testen installiert er sich die Software, welche sich als Ransomware herausstellt und sich in der Folge über weitere Systeme, auf die der Administrator durch erhöhte Rechte zugreifen kann, ausbreitet.
- **Abhörung analoger oder digitaler Kommunikation**: Unternehmen A versendet Mails ohne Verschlüsselung. Dadurch können Angreifer Mails im Netzwerkverkehr direkt mitlesen.

### Schutzmassnahmen 

Um Folgen vorzubeugen, sollten Schutzmassnahmen nicht erst implementiert werden, wenn es schon zu spät ist. Dazu sollten für jeden Informationstyp nach der Klassifizierung in Bezug auf die Vertraulichkeit mögliche Risiken und Folgen unter Beachtung der jeweiligen Eintrittswahrscheinlichkeit erfasst werden.

Im Bereich des Datenschutzes spricht man hier von *technischen und organisatorischen Massnahmen*, die klassisch in *Zutritts-*, *Zugangs-*, *Zugriffs-* und *Trennungskontrolle* unterschieden werden.

#### Zutrittskontrolle

- Eingezäuntes Grundstück 
- Alarmanlagen
- Schliessanlagen
- Videoüberwachung 
- Besucherregelungen

#### Zugangskontrolle

- Passwordkomplexität 
- Biometrie
- Datenträgerverschlüsselung
- Firewall
- Bildschirmsperre

#### Zugriffskontrolle

- Abschliessbare Schränke 
- Berechtigungskonzept
- Zugriffsprotokollierung 
- Datenträgerentsorgung
- Sperrung von Anschlüssen 
- Prüfung von Email-Anhängen

#### Trennungskontrolle

- Mandatentrennung
- Datenspeichertrennung
- Zweckbindung
- Getrennte Nutzerkonten
- Getrennte verarbeitende Systeme

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

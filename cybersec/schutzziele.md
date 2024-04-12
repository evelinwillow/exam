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

## Integrität

Der Begriff *Integrität* bedeutet in der IT unter anderem die korrekte Funktionsweise von Systemen oder die Unversehrtheit von Daten. In Bezug auf Daten bedeutet er weiterhin, dass die Daten vollständig sind. Damit ist nicht nur deren Inhalt gemeint, sondern auch die Metadaten.
Für Unternehmen ist es unerlässlich, dass die Datenverarbeitung zuverlässig funktioniert, da dies für den laufenden Geschäftsbetrieb unverzichtbar ist. Das Schutzziel der Integrität sollte daher eine hohe Priorität haben.

Die Integrität ist nicht nur im Sinne der DSGVO wichtig; so ist sie z.B. auch bei der Aufklärung von IT-Sicherheitsvorfällen durch IT-Forensiker wichtig. Hier sind häufig besonders nicht auf den ersten Blick als wichtig erkennbare Daten (bzw. nicht sensible Daten) wie Log-Dateien und Protokolldaten relevant. Angreifer könnten durch Manipulation dieser Daten so Sicherheitsvorfälle bewusst verschleiern. Weiterhin könnten diese Daten die interne Struktur eines Informationsverbundes verraten.

### Vorgaben der DSGVO

Die DSGVO listet Integrität als einen der Grundsätze für die Verarbeitung von personenbezogenen:

> "Personenbezogene Daten müssen:
in einer Weise verarbeitet werden, die eine angemessene Sicherheit der personenbezogenen Daten gewährleistet, einschliesslich Schutz vor unbefugter oder unrechtmässiger Verarbeitung und vor unbeabsichtigtem Verlust, unbeabsichtigter Zerstörung oder unbeabsichtigter Schädigung durch geeignete technische und organisatorische Massnahmen ("Integrität und Vertraulichkeit")"

Hier wird darauf eingegangen, dass Veränderungen sowie Entfernung von Daten durch Unbefugte zu verhindern ist - allerdings bezieht sich das Entfernen hier in diesem Kontext eher auf das Schutzziel der Vertraulichkeit. 
Bei der Integrität der Daten geht es primär darum, Veränderungen, sollten diese denn auftreten, erkennbar zu machen. Dies dient dazu, dass sie korrigiert werden können. 
Dadurch schliesst die Integrität auch an den Grundsatz der Richtigkeit an.

Verantwortliche müssen unter Berücksichtigung einer Reihe von Umständen technische und organisatorische Massnahmen treffen, um die Integrität und Belastbarkeit von Systemen und Diensten zu garantieren, die personenbezogene Daten verarbeiten.

Das Standard-Datenschutzmodell ordnet der Integrität weiterhin einige weitere Anforderungen aus der DSGVO zu:
- Behebung und Abmilderung von Datenschutzverletzungen
- Angemessense Überwachung der Verarbeitung
- Fehler- und Diskriminierungsfreiheit beim Profiling

### Bedrohungen für die Integrität 

Neben der bereits genannten Manipulation durch dritte oder auch Schadprogramme gibt es weitere, nicht böswillige Faktoren wie Fehlverhalten von Personen oder Fehlfunktionen von Software oder Übermittlungsfehler:

- **Alte Datenträger**: Wenn Medien längere Zeiten nicht gewartet oder gepflegt werden, können Daten auf dem Medium beschädigt werden oder verloren gehen. Mit fortgeschrittenem Alter steigt auch die Wahrscheinlichkeit, dass Datenträger kaputt gehen oder Daten korruptiert werden. 
- **Übertragungsfehler**: Falls es bei der Datenübertragung zu Verbindungsabbrüchen kommt und die Verbindung dann wieder hergestellt wird, kann nicht garantiert werden, dass Daten nicht unvollständig oder fehlerhaft übertragen wurden. Besonders bei grösseren Datenmengen ist dies nicht unwahrscheinlich.
- **Fehlerhafte Eingaben**: Beispielsweise kann ein fehlerbehaftetes Script Daten überschreiben, falsch umwandeln, oder inkorreket schreiben. 

### Mögliche resultierende Schäden

Aus der Verletzung der Unversehrtheit resultieren Probleme, die in manchen Fällen ebenfalls zu immensen Schäden führen können:

- **Informationen können nicht mehr gelesen werden**: Ein einzelnes inkorrektes Bit in z.B. kryptographischen Schlüsseln kann dazu führen, dass diese nicht mehr gelesen werden können oder verschlüsselte Daten nicht mehr entschlüsselt werden. Weiterhin kann das Schutzziel der Authentizität eventuell nicht mehr überprüft werden. Im schlimmsten Fall sind die darin enthaltenen Informationen damit verloren.
- **Inkorrekt archivierte Daten**: Viele Unternehmen archivieren grosse Mengen an Daten. Treten dabei Fehler auf und bleiben diese über im schlimmsten Fall mehrere Jahre unbemerkt, kann der Schaden immens sein. Diese Daten sind z.B. nicht mehr vor Gericht verwendbar, da ihre Integrität nicht mehr gewährleistet ist.
- **Manipulation**: Angaben in z.B. Emails könnten manipuliert sein. Dadurch kann bespielsweise bezweckt werden, dass Überweisungen in falscher Höhe oder an den falschen Empfänger geschickt werden.

### Schutzmassnahmen

Häufig lässt sich der Schutz der Integrität von Daten mit wenig Aufwand realisieren. Hier spricht man von Umsetzungen, die das System zusätzlich härten, um die Angriffsfläche zu minimieren.

- Einschränkung von Änderungs- und Schreibrechten auf bestimmten Daten, um versehentliche oder böswillige Änderungen zu verhindern. 
- Digitale Signaturen, Siegel und Prüfsummen sollten eingesetzt werden, um zu überprüfen, ob Daten manipuliert wurden.
- Authentifizierung und Indentifizierung von Personen, die auf bestimmte Daten zugreifen wollen
- Systeme immer auf aktuellstem Stand halten, um korrekte Datenübertragung zu gewährleisten

#### Verwandtheit mit dem Schutzziel Vertraulichkeit

Die Vertraulichkeit ist eng verwandt mit der Integrität. Viele Vorkehrungen zum Schutz des einen gewährleisten auch den Schutz des anderen Zieles:

- Erforderlichkeitsprinzip im Rollen- und Berechtigungskonzept 
- ordnungsgemässe Authentifizierungsverfahren (z.B. 2FA)
- Kontrollierte Nutzung von Kommunikationskanälen
- Einschränkung von Zugriff und Zutritt

## Verfügbarkeit 

Das Schutzziel Verfügbarkeit steht für die Garantie, dass Dienstleistungen, Funktionen eines Systems, Anwendungen, Netzwerke oder Informationen von den Anwendern stehts wie vorgesehen genutzt werden können.
Zwischen Anbietern von IT-Systemen oder -Dienstleistungen und deren Kunden kann eine solche Garantie in Service Level Agreements (SLA) vertraglich festgehalten werden. Diese schreiben dann vor, dass z.B. pro Jahr ein Server nur 8 Stunden ausfallen darf. Werden SLAs vom Anbieter verletzt, muss der Anbieter i.d.R. vorher definierte Strafen zahlen oder den vertraglich festgehaltenen Verlust wiedergutmachen.

Geplante Ausfallzeiten, wie z.B. zum Einspielen von notwendigen Patches oder Wartungsarbeiten werden ebenso berücksichtigt. Das bedeutet, dass nur die nicht geplante Ausfallzeit relevant ist. Diese müssen jedoch in der Regel vorher abgestimmt werden.

### Berechnung von Verfügbarkeit

Oft wird Verfügbarkeit in Prozent angegeben. Sie wird berechnet, indem der Zeitraum, in dem das System oder die Ressource zur Verfügung steht, durch den Gesamtzeitraum eines Jahres geteilt wird. Anschliessend wird mit 100 multipliziert. 
Heutzutage gilt 99% Verfügbarkeit bei qualitativ hochwertigen Geräten als Minimalanforderung.

Das BSI hat das sogenannte 9er-System zur Klassifizierung von Verfügbarkeit definiert. Diese sind in 5 Klassen aufgeteilt, wobei bei Klasse 0 keine "zugesicherte Verfügbarkeit" besteht, und Klasse 5 eine absolute Ausfalltoleranz verspricht. Die Verfügbarkeitsklassen unterscheiden sich in den berechnenten Verfügbarkeiten um je eine Nachkommastelle. Während Klasse 1 bereits 99.0% als Maximum angibt, garantiert Klasse 2 bereits 99.9% und somit nur rund 9 Stunden Ausfallzeit im Jahr.

Weiterhin gibt es die Klassifizierung der Harvard Research Group, welches Verfügbarkeit in 6 Klassen oder AEC (Availability Environment Classification) einteilt. Es kommt weitestgehend ohne Berechnungen aus.

### Hochverfügbarkeit

Besonders im Cloud-Umfeld redet man gerne von Hochverfügbarkeit. Kein Anbieter kommt darum herum, High Availability als grossen Vorteil der Cloud zu nennen. Die Definition ist aber eher schwammig und weicht von Quelle zu Quelle ab. In einigen Fällen wird von Hochverfügbarkeit gesprochen, wenn zusätzlich zur garantierten Verfügbarkeit des Systems auch noch eine "Notlösung" für den Fall existiert, dass der garantierten Verfügbarkeit doch ein Fehler unterläuft. In einer Cloud-Umgebung kann dies z.B. durch ein sogenanntes Failover-Cluster erreicht werden. 

Andere Definitionen beziehen sich explizit auf Zahlen und bezeichnen Verfügbarkeiten ab 99.99% als Hochverfügbarkeit. 

### Vorgaben der DSGVO

Die DSGVO fordert für das Schutzziel der Verfügbarkeit von personenbezogenen Daten als technisch und organisatiorische Massnahme ausdrücklich 

> "die Fähigkeit, die Vertraulichkeit, Integrität, Verfügbarkeit und Belastbarkeit der Systeme und Dienste im Zusammenhang mit der Verarbeitung auf Dauer sicherzustellen."

#### Unterscheidung des Verfügbarkeitszieles der DSGVO von der IT-Security

Das Gewährleistungsziel der Verfügbarkeit seitens DSGVO bezieht sich zwar ebenso auf Systeme und Dienste, allerdings stehen nicht das Unternehmen und dessen Assets, sondern der Mensch im Vordergrund. Es geht nicht darum, eine Website möglichst lange online zu halten, um z.B. Umsatzeinbrüche zu verhindern, sondern um die Garantie, dass personenbezogene Daten wie erwartet und vereinbart verarbeitet werden und er auf die Verarbeitung mit seinen Rechten einwirken kann. Daher kann im direkten Kontrast zur IT-Security eine Nichtverfügbarkeit durchaus im Sinne des Datenschutzes sein, z.B. wenn der Betroffene sein Recht auf Löschung ausübt oder der erforderliche Zweck für die Datenverarbeitung ausfällt.

#### Vorgaben zur Wiederherstellung der Verfügbarkeit

TODO fertig schreiben Q_Q

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

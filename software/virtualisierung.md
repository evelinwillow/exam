# Virtualisierung

## Arten der Virtualisierung 

### Anwendungsvirtualisierung

Bei der Anwendungsvirtualisierung werden Anwendungen virtualisiert und von einem Server auf das Gerät des Endbenutzers übertragen. Dadurch wird die Anwendung vom Betriebssystem getrennt, denkt aber, dass sie mit dem Betriebssystem zusammen arbeitet. 
Allerdings arbeitet sie in Wirklichkeit mit einer Software-Abstraktionsschicht, die Hypervisor genannt wird. Für den Nutzer verhält sich eine virtualisierte Anwendung wie eine Anwendung, die direkt auf dem Gerät installiert ist.
Die gängigste Art, Anwendungen zu virtualisieren, ist auf einem zentralen Server im Unternehmensrechenzentrum oder einem Cloud-basierten Dienst. Diese werden den Nutzern über Unternehmensnetzwerk oder Internet bereitgestellt.

#### Vorteile 

- Erleichtert Remote-Arbeit
- Verlängert die Lebensdauer von Anwendungen (Legacy-Anwendungen, welche auf nicht mehr unterstützte Hardware angewiesen sind)
- Vermeidung von Anwendungskonflikten (ermöglicht Ausführung von inkompatibler Software oder verschiedenen Versionen derselben Software)
- Verlängert Lebensdauer von Endgeräten (Ältere OS auf Legacy-Hardware mit neuer Software)
- Unterstützung von Endgeräten, die normalerweise nicht unterstützt werden (z.B. Handy)
- Vermeidung von Betriebssystemkonflikten
- Einfache Verwaltung (Da die Anwendung nur einmal installiert ist, werden Updates und Wartung nur auf Serverebene durchgeführt, und nicht für jedes Endgerät)
- Einhaltung von Vorschriften (Vorschriften wie HIPAA und PCI DSS sowie Schutzziele können leichter gewährleistet werden)

#### Nachteile

- Internetverbindung zwingend erforderlich und beeinflusst direkt die Reaktivität der App
- Grafikintensive Anwendung sind weniger performant/reaktiv 
- Antivirenprogramme könnten virtuelle Anwendungen als Virus erkennen
- Drucker funktieren oft nicht korrekt/nur schwer mit virtualisierten Apps 



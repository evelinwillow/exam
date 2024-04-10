# USV

USV werden in 3 Arten unterteilt:

- VFD (Voltage Frequency Dependent), auch bekannt als Offline-USV
- VI (Voltage Independent), auch bekannt als Line Interactive-USV
- VFI (Voltage and Frequency Independent), auch bekannt als Online-USV

Basierend auf der Art kann eine USV gegen verschiedene Arten von Netzstörung schützen:

```
Störungstyp             Dauer               Definition

Netzausfall             mehr als 10ms       Netzausfall wird als Nullspannungsbedingung definiert
Spannungsschwankung     weniger als 16ms    Einbrüche, die kurz unter dem Normalwert liegen. Kann beim Einschalten grosser Anlagen auftreten.
Spannungsspitzen        4ms bis 16ms        Oft durch statische Entladungen verursacht
Spannungsstösse         weniger als 4ms     Plötzliche und kurzfristige Spitzen. Treten z.B. bei Blitzeinschlag auf.
Unterspannungen         forlaufend          Spannung fällt unter zulässigen Grenzwert
Überspannung            fortlaufend         Wenn z.B. grosse Anlagen aktiviert werden, kann der Normalbetrieb auf über 100% steigen.
Frequenzschwankungen    sporadisch          Frequenz weicht von normalerweise konstanten Netzfrequenz ab
Spannungsverzerrung     periodisch          Wird auch als Störspannung bezeichnet.
```

## VFD/Offline-USV

Diese Art von USV ist die einfachste USV und schützt lediglich vor einem kompletten Netzausfall. Andere Störungen können nicht ausgeglichen werden.
Bei einem Netzausfall übernimmt ein Akku die Energieversorgung, auch bei Unter- oder Überspannung wird auf Batteriebetrieb umgeschaltet.
Schaltzeiten liegen dabei bei wenigen Millisekunden. Dies reicht für die meisten Systeme aus. Der Akku wird bei Normalbetrieb dann wieder über einen Ladegleichrichter aufgeladen.

Der Wirkungsgrad liegt bei ca. 95%.

## VI/Line-Interactive-USV

Diese USV schützt auch gegen Schwankungen der Netzspannung. Dies wird durch einen zwischen Netzeingang und Verbraucher geschalteten Spannungsregler erreicht. 
Diese Art von USV eignet sich gut für Anwendungsgebiete, wo häufige Netzspannungen auftreten. Dadurch können einzelne Geräte, Netzwerke, oder grössere Anlagen abgesichert werden.

Der Wirkungsgrad liegt zwischen 95% und 98%.

## VFI/Online-USV

Diese Art von USV schützt vor jeder Art von Netzstörung. Der Verbraucher wird selbst im Normalbetrieb ständig über den Akku versorgt. 
Da bei dieser Art von USV bei einem Netzausfall oder bei Störungen nicht erst auf Batteriebetrieb geschaltet werden muss, liegen hier keine Schaltzeiten vor. 
Diese USV arbeitet mit einem "Dauerwandlerprinzip", hierbei ist die Wandlung von Wechsel- in Gleichstrom und von Gleich- in Wechselstrom gemeint.
Da hier stetig der Strom gewandelt wird, treten dadurch Verluste und Wärme auf. Diese Art von USV eignet sich zum Absichern von hochsensiblen Systemen. Sie ist oft in der Server- und Datenkommunikation zu finden, und durch die Dauerbelastung ist die Lebensdauer der Akkus kurz.

Der Wirkungsgrad liegt bei ca. 90%.

## Berechnung der Kapazität und Autonomiezeit

Zur Berechnung der Autonomiezeit sind folgende Werte wichtig:

- Leistung in Watt (W)
- Scheinleistung in Voltampere (VA)
- Wirkleistung in Watt (W)

Die folgenden Formeln können zur Umwandlung von Schein- in Blindleistung und zurück benutzt werden:

```
Wirkleistung (in W) = Scheinleistung (in VA) * 0.65
Scheinleistung (in VA) = Wirkleistung (in W) * 1.55
```

Zur Berechnung der Autonomiezeit kann die Formel `Autonomiezeit = Kapazität / Leistung` benutzt werden. 

### Beispielrechnung

Folgende Verbraucher sollen an eine USV angeschlossen werden:

- 2 Computer mit je 300 W
- 1 Server mit 500 W
- 1 Router mit 0.5 A und 230 V

Berechnung der Wirkleistung:

```
P(USV) = ( 2 * 300 W ) + ( 500 W ) + ( 0.5 A * 230 V * 0.65 )
P(USV) = 1173.75 W
```

Berechnung der Scheinleistung:

```
S(USV) = 1175.75 W * 1.55
S(USV) = 1724.38 VA
```

Leistungsreserve von 20%:

```
P(USV) = 1174.75 W * 1.2
P(USV) = 1409.70 W
```

oder

```
S(USV) = 1724.38 VA * 1.2
S(USV) = 2069.26 VA
```

Die USV sollte also mindestens eine Leistung von 1409.70 W oder 2069.26 VA haben.

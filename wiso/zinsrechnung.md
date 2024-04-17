# Zinsrechnung

## Tilgung

Die Tilgung bei Ratenkrediten mit fester Laufzeit lässt sich recht einfach berechnen:

```math
Kreditsumme / Anzahl_Jahre = Tilgung_Jährlich
```

Um die jährliche Rate zu berechnen, kommt noch die Zinslast dazu:

```math
( Kreditsumme * Zinssatz ) / 100 = Zinsen
```

Addiert man dies nun zur jährlichen Tilgung, ergibt sich die Annuität:

```math
Zinsen_Jährlich + Tilgung = Annuität im ersten Jahr 
```

Die Berechnung der Restschuld ist etwas komplexer: 

```math
Restschuld = Tilgungsrate * ( Tilgungsdauer - Jahr des zu berechnenden Restschuld ) 
```

### Beispielrechnung

Gegeben: 
- Gesamtschuld: 240.000 Euro
- Zinssatz: 5% p.a.
- feste Tilgungsraten über 4 Jahre

```
Jahr        Schuld      Zinsen      Tilgung     Rate        Restschuld
--------#-----------#-----------#-----------#-----------#-------------
1       |   240.000 |   12.000  |   60.000  |   72.000  |   180.000 
2       |   180.000 |   9.000   |   60.000  |   69.000  |   120.000
3       |   120.000 |   6.000   |   60.000  |   66.000  |   60.000
4       |   60.000  |   3.000   |   60.000  |   63.000  |   0 
--------#-----------#-----------#-----------#-----------#-------------
gesamt: |   240.000 |   30.000  |   240.000 |   270.000 |   
```

Die Zinsen werden hier also nicht auf die Restschuld addiert, sondern auf die Rate.
Tilgung und Restschuld sind somit komplett unabhängig vom Zinssatz, welcher nur die zu zahlende Rate beeinflusst.

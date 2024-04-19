# GA 1 

## Aufgabe 1 

### a)

OnPrem:

- Schnelleres Netzwerk
- Verfügbarkeit bei Netzausfall
- Erfordert etwas weniger Fachkenntnis

Cloud:

- Niedrigere laufende Kosten
- Niedrigere Anschaffungskosten
- Verfügbarkeit von überall (Anbindung von Standorten)

**5/6 PUNKTE**

### b)

#### ba)

Ping (Verzögerung bzw Transportzeit); Grosse physische Entfernung, Hoher Datendurchsatz

**4/4 PUNKTE**

#### ba)

Echtzeitanwendungen (Computerspiele online hehe)

**2/2 PUNKTE**

### c)

#### ca)

Failover-Clusterung  |   Erhöhung der Verfügbarkeit durch Vermeidung eines Serviceausfalles bei Serverausfall
Headless OS | Einsparung von Ressourcen, erhöht Geschwindigkeit
Redundante Netzanbindung | Vermeidung eines Serviceausfalles bei Netzausfall (Kabel kaputt) -> Relevant bei Clusterung 

**4/6 PUNKTE**

#### cb) 

Gegeben: 

- 5 TiB Datenbank 
- 3 TiB Nutzdaten 
- 5 TiB Puffer 

- Zwei Arrays mit je 8 Platten zu 2 TiB -> 16 TiB gesamt 

Gesucht: 
 
- Anzahl Festplatten

Daten_gesamt = 5 TiB + 3 TiB + 5 TiB Puffer = 13 TiB 
Platten_Ohne_Raid = 13 TiB / 2 TiB = 7 Platten 
Platten_Raid = Platten_Ohne_Raid + 2 Platten 
Platten_Raid = 9 Platten 

**4/5 PUNKTE**

### d) 

#### da)

Gegeben: 

- 30 GiB Daten pro Monat 
- 60% Komprimierung 
- 10 Jahre Speicherdauer

MAX 1 TiB! 

Gesucht: 

- Datenmenge 

Datenmenge = ( 10 * 12 ) * ( 30 GiB * 0.4 ) 
Datenmenge = 120 * 12 GiB
Datenmenge = 1,440 GiB / 1024 = 1.4 TiB -> Speicher reicht nicht!

**2/2 PUNKTE**

#### db) 

Datenmenge_Jahr = 12 * 12 GiB = 144 GiB / 1024 = 0.14 TiB/j 

Jahre = 1 TiB / 0.14 TiB/j = 7.1 =~ 7 Jahre 

**2/2 PUNKTE**

**23/27 PUNKTE**

## Aufgabe 2 

### a)

#### aa)

int 
boolean 
int -> char(5)
char(11) -> 16
date
char(22)

**2/3 PUNKTE**

#### ab) 

```sql
SELECT COUNT(Kunde.Kunde_Aktiv) 
FROM Kunde 
WHERE Kunde.Ort = "Augsburg"
```

**2/4 PUNKTE**

#### ac)

```sql
Werbepartner varchar(), 
Werbung_verschickt date,
WerbungsID, -> WerbungsID NOT NULL,
KundenNr -> KundenNR int,
-> PRIMARY KEY (WerbungID),
-> FOREIGN KEY (KundenNr) REFERENCES Kunde(KundenNr)
```

**2/6 PUNKTE**

#### ad)

SELECT COUNT(Werbeaktion_verschickt)
FROM Kunde JOIN Werbeaktion
WHERE Kunde.PLZ LIKE 8%
AND Werbung.Werbung_verschickt < 31.12.2021

**0/6 PUNKTE**

### b)

Redis (Cache) 

**2/4 PUNKTE**

**8/23 PUNKTE**

## Aufgabe 3 

LTO wird vermutlich jahrelang wesentlich günstiger als Festplattenplatz bleibe. LTFS ermöglicht ausserdem, Daten mit traditionellem Festplattenspeicher ensprechenden Geschwindigkeiten zu lesen und schreiben.

**4/4 PUNKTE**

### b)

alle daten, archivbit zurückgesetzt
alle seit letztem vollbackup, archivbit nicht zurückgesetzt
alle seit letztem inkrement, archivbit zurückgesetzt
alle daten, archivbit ignoriert

**10/10 PUNKTE**

### c)

V2 - D2 - D3 - D5 

**4/6 PUNKTE**

### d)

x 
x
    x
x     ->    x
    x -> x  x

**3/5 PUNKTE**

**21/25 PUNKTE**

## Aufgabe 4 

### a)

```c 
int counter;

for ( counter = 0; counter < 24; counter++ )
{
    sum = sum + usedRAM[counter];
}

average = sum / 24;

if ( sum > 75% )
{
    MessageBox.Show("RAMn't","uh oh");
}

```

**16/16 PUNKTE**

### b)

Datenkapselung bedeutet, dass Daten innerhalb von Klassen/Objekten gespeichert werden, anstatt lose im Arbeitsspeicher herumzufliegen und von jedem gelesen/geschrieben werden zu können. Dadurch müssen sie durch definierte getter/setter-Funktionen ausgelesen oder geschrieben werden.

Vererbung bedeutet, dass Klassen, die von anderen Erben, dessen Methoden und Daten (wort vergessen) übernehmen. Dadurch müssen häufig geschriebene oder allgemeingültige Funktionen bei ähnlichen oder derivativen Klassen nicht jedes mal neu definiert werden.

**6/6 PUNKTE**

### c)

3200
?
16

**3/3 PUNKTE**

**25/25 PUNKTE**

**GESAMTPUNKTE: 77**

# GA 2 

## Aufgabe 1 

**/25 PUNKTE**

## Aufgabe 2 

**/25 PUNKTE**

## Aufgabe 3 

**/25 PUNKTE**

## Aufgabe 4 

**/25 PUNKTE**

## Aufgabe 5 

**/25 PUNKTE**

**GESAMTPUNKTE:**

# WiSO 

## Aufgabe 1 

**/3.3 PUNKTE**

## Aufgabe 2 

**/3.3 PUNKTE**

## Aufgabe 3 

**/3.3 PUNKTE**

## Aufgabe 4 

**/3.3 PUNKTE**

## Aufgabe 5 

**/3.3 PUNKTE**

## Aufgabe 6 

**/3.3 PUNKTE**

## Aufgabe 7 

**/3.3 PUNKTE**

## Aufgabe 8 

**/3.3 PUNKTE**

## Aufgabe 9 

**/3.3 PUNKTE**

## Aufgabe 10 

**/3.3 PUNKTE**

## Aufgabe 11 

**/3.3 PUNKTE**

## Aufgabe 12 

**/3.3 PUNKTE**

## Aufgabe 13 

**/3.3 PUNKTE**

## Aufgabe 14 

**/3.3 PUNKTE**

## Aufgabe 15 

**/3.3 PUNKTE**

## Aufgabe 16 

**/3.3 PUNKTE**

## Aufgabe 17 

**/3.3 PUNKTE**

## Aufgabe 18 

**/3.3 PUNKTE**

## Aufgabe 19 

**/3.3 PUNKTE**

## Aufgabe 20 

**/3.3 PUNKTE**

## Aufgabe 21 

**/3.3 PUNKTE**

## Aufgabe 22 

**/3.3 PUNKTE**

## Aufgabe 23 

**/3.3 PUNKTE**

## Aufgabe 24 

**/3.3 PUNKTE**

## Aufgabe 25 

**/3.3 PUNKTE**

## Aufgabe 26 

**/3.3 PUNKTE**

## Aufgabe 27 

**/3.3 PUNKTE**

## Aufgabe 28 

**/3.3 PUNKTE**

## Aufgabe 29 

**/3.3 PUNKTE**

## Aufgabe 30 

**/3.3 PUNKTE**

**GESAMTPUNKTE:**

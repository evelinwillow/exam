# SQL 

SQL steht für "*Structured Query Language*" und ist eine Datenbanksprache zur Erstellung, Bearbeitung und Abfrage von Datenbankstrukturen in relationalen Datenbanken.
Sie basiert auf *relationaler Algebra*.

## Abfragen

### SELECT

Der *SELECT*-Befehl ist der Grundstein für zahlreiche SQL-Abfragen. Mithilfe dieses Befehls ist es möglich, Daten aus einer oder mehreren Tabellen über ein *JOIN*-Befehl abzufragen. 
SQL-Abfragen sollten niemals mit einer *Wildcard*, also *SELECT \* FROM Tabelle* ausgeführt werden, da dann alle Spalten der SQL SELECT Abfrage zurückgeliefert werden.
Ergebnismengen sollten immer eingegrenzt werden, wie z.B. *SELECT TOP 10 \* FROM Tabelle*.

#### Syntax

Der Syntax einer SELECT-Abfrage ist wie folgt aufgebaut:

```sql 
SELECT Spaltenname, Spaltenname+n FROM Tabellenname;
```

Mithilfe des SELECT-Befehls wird definiert, welche Spalten einer Tabelle nach der Ausführung der Abfrage zurückgegeben werden sollen.

### DISTINCT 

Der *DISTINCT*-Befehl wird in einer Abfrage direkt hinter dem SELECT platziert. Damit werden Redundanzen, die eventuell in einer Tabelle auftreten können, eliminiert. Er kommt weniger in transaktionalen Datenbanken vor, und wird eher in Data Warehouses und bei der Report-Erstellung benutzt. 

#### Syntax 

```sql 
SELECT DISTINCT Spaltenname FROM Tabellenname;
```

Mithilfe des DISTINCT-Befehls werden Spalten auf Redundanz geprüft und diese eliminiert.

### WHERE 

Mit dem *WHERE*-Befehl werden in einer Abfrage nur bestimmte Datensätze ausgewählt. Damit funktionert er wie ein Filter, der es ermöglicht, nur Datensätze anzuzeigen, die bestimmte Kriterien erfüllen.

#### Syntax 

```sql 
SELECT Spaltenname FROM Tabellenname WHERE Spaltenname = Wert
```

Mit dem WHERE-Befehl wird definiert, welche Bedingung positiv erfüllt werden muss, damit die richtige Ergebnismenge geliefert wird. 

#### Mögliche Vergleichsoperatoren

- Gleich (=) oder ungleich (<>), auch als ungleich (!=) bekannt
- Grösser als (>) und kleiner als (<)
- Grösser oder gleich (>=) und kleiner oder gleich (<=)

### AND/OR 

Mit den *AND* & *OR*-Operatoren werden mehrere *WHERE*-Conditions miteinander verknüpft. 

#### Syntax

```sql 
SELECT Spaltenname 
FROM Tabellenname 
WHERE Spaltenname1 = Wert1 
AND Spaltenname2 = Wert2; 
```

### IN 

Der *IN*-Operator wird in WHERE-Bedingungen eingebaut, um mehrere Abfrageergebnisse in einer Anweisung zu bündeln. Damit kann der IN-Operator leicht mehrere OR-Operatoren ersetzen.

**WICHTIG**: In einer SELECT-Abfrage kann der IN-Operator nicht mit Wildcards gefüllt werden wie beim LIKE-Operator!

#### Syntax 

```sql 
SELECT Spaltenname 
FROM Tabellenname 
WHERE Spaltenname IN ('Wert1','Wert2');
```

### BETWEEN

Der *BETWEEN*-Befehl wird in WHERE-Bedingungen eingebaut, um einen bestimmten Bereich eines Abfrageergebnisses in einer Anweisung zu bündeln.
Dieser Befehl wird oft benutzt, um alle Informationen zwischen zwei Datumsangaben zu ermitteln.

#### Syntax 

```sql 
SELECT Spaltenname 
FROM Tabellenname
WHERE Spaltenname
BETWEEN 'Wert1' AND 'Wert2';
```

### LIKE 

Der *LIKE*-Befehl ermöglicht eine Suche auf Grundlage eines vorher definierten regulären Musters anstelle eines festen Begriffs oder Bereiches. Oft wird dieser Befehl verwendet, um mit regulären Mustern Ergebnisse in Zeichenketten oder Texten zu finden.

#### Syntax 

```sql 
SELECT Spaltenname
FROM Tabellenname
WHERE Spaltenname
LIKE 'Muster';
```

#### Verfügbare Strukturen

- 'L_S': Alle Zeichenketten, die mit einem L beginnen inklusive eines Folgezeichen, und die mit einem 'S' enden.
- 'BEST%': Alle Zeichenketten, die mit einem 'BEST' beginnen.
- '%UNG': Alle Zeichenketten, die mit einem 'UNG' enden.
- '%ST%': Alle Zeichenketten, die irgendwo das Muster 'ST' enthalten.

### ORDER BY 

Mit dem *ORDER BY*-Befehl werden Ergebnisse basierend auf einer vorher definierten Sortierungsreihenfolge sortiert.

#### Syntax 

```sql 
SELECT Spaltenname
FROM Tabellenname
ORDER BY Spaltenname Sortierungsparameter;
```

#### Parameter

- ASC: Ergebnisse werden aufsteigend sortiert.
- DESC: Ergebnisse werden absteigend sortiert. 

### GROUP BY 

Mit dem *GROUP BY*-Statement können Ergebnisse gruppiert werden. Dieser Befehl wird oft mit Aggregatsfunktionen kombiniert. Zu diesen gehören *AVG*, *COUNT*, *MAX*, *MIN*, *SUM*.

#### Syntax 

```sql 
SELECT Spaltenname
FROM Tabellenname
[ WHERE Bedingung ] 
GROUP BY Spaltenname;
```

### HAVING

Das *HAVING*-Statement ist das WHERE in einem GROUP BY-Statement. Er ermöglicht, eine gruppierte Ergebnismenge einzuschränken. Mit HAVING kann die Ergebnismenge auf Basis der Aggregatfunktionen eingeschränkt und ausgegeben werden.

#### Syntax 

```sql 
SELECT Spaltenname
FROM Tabellenname
[ WHERE Bedingung ]
GROUP BY Spaltenname
HAVING Ausdruck;
```

## Joins

In relationalen Datenbanken werden Informationen aus einem oder mehreren Anwendungssystemen gespeichert. Die Zusammengehörigkeit der Daten ergibt sich aus dem logischen Datenbankdesign, meist ein Entity-Relationship-Modell. Die Struktur der Datenbank leitet sich aus den einzelnen Typen dieses Modells ab.

Um Redundanzen beim Speichern zu vermeiden, werden Informationen auf verschiedene Tabellen verteilt. Zur Erhaltung der logischen Zusammengehörigkeit werden Fremdschlüssel-Beziehungen zwischen den Tabellen aufgebaut. 

Muss die Datenbank eine Anfrage verarbeiten, bei der Informationen aus mehreren Tabellen benötigt werden, ist es erforderlich, die einzelnen Datensätze wieder zusammenzuführen. Dadurch werden die ursprünglichen Informationen wiederhergestellt. 

Die Verbindung der Tabellen erfolt mit speziellen Schlüsselwörtern. Neben den Namen des anzuwendenden Joins muss zusätzlich eine *ON*-Bedingung angegeben werden. Einzige Ausnahmen sind *CROSS JOIN* und *NATURAL JOIN*. In der ON-Bedingung werden die zu vergleichenden Spalten der beiden Tabellen angegeben.

Ein **Vergleich** erfolgt durch die normalen **Vergleichsoperatoren**. Dabei können die Namen der Spalten ungleich sein, allerdings müssen sie die logische Verbindung zwischen den Datensätzen widerspiegeln. Zusätzlich kann noch die *WHERE*-Klausel verwendet werden, um die Ergebnismenge einzuschränken.

### Arten von Joins 

- Cross-Join
- Inner Join 
- Natural Join 
- Left Join 
- Right Join 
- Full Outer Join 

#### Cross Join

Der *CROSS JOIN* gibt alle Informationen aus beiden Tabellen zurück. CROSS JOIN kann sehr grosse Datenmengen zurückgeben, daher sollte mit Filterklauseln gearbeitet werden.
Es werden alle Daten zurückgegeben, selbst, wenn Spalten kein Match in der anderen Tabelle haben. Wenn eine WHERE-Klausel hinzugefügt wird, welche auf Matches der Schlüssel überprüft, erzeugt CROSS JOIN die selben Resultate wie INNER JOIN

##### Syntax 

```sql 
SELECT Spaltenname
FROM Tabelle1
CROSS JOIN Tabelle2;
```

#### Inner Join

Der *INNER JOIN* gibt nur Datensätze oder Zeilen zurück, die übereinstimmende Werte haben. Er wird verwendet, um Daten abzurufen, die in beiden Tabellen enthalten sind. 

##### Syntax 

```sql
SELECT Spaltenname 
FROM Tabelle1 
INNER JOIN Tabelle2 
ON Tabelle1.ID = Tabelle2.ID
```

#### Natural Join 

Ein *NATURAL JOIN* ist eine Kombination von Tabellen, in deren Spalten gleichen Namens existieren. Die Werte in diesen Spalten werden auf Übereinstimmung geprüft.

##### Syntax 

```sql 
SELECT Spaltenname 
FROM Tabelle1 
NATURAL JOIN Tabelle2 
```

### LEFT JOIN 

Der *LEFT JOIN* listet alle Elemente auf, die in beiden Tabellen gemeinsam sind, aber auch alle Elemente aus der linken Tabelle, die nicht gleich sind. 

#### Syntax 

```sql 
SELECT Spaltenname 
FROM Tabelle1 
LEFT JOIN Tabelle2 
ON Tabelle1.ID = Tabelle2.ID 
```

### RIGHT JOIN 

Wie LEFT JOIN, nur rechts.

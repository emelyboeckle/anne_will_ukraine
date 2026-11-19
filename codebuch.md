# Datensatz Anne Will 2022: Ukraine (Folgen 500 bis 503)
Codebuch, Stand November 2026, erstellt von Emely Böckle im Kurs 226305 Soziale Netzwerkanalyse an der Hochschule der Medien Stuttgart

## Inhalt
- anne_will_edges.csv (Edgelist)
- anne_will_nodes.csv (Nodelist)
- codebuch.md (Codierung der Datensätze)

## Ursprung und Datenerhebung
Erhoben wurden alle Gäste der Talkshow Anne Will (Das Erste) aus den vier Folgen 500 bis 503. Die Folgen liefen zwischen dem 20.02.2022 und dem 13.03.2022 und behandeln den Konflikt mit Russland und den Krieg gegen die Ukraine.

| Folge | Sendedatum |
|---|---|
| 500 | 20.02.2022 |
| 501 | 27.02.2022 |
| 502 | 06.03.2022 |
| 503 | 13.03.2022 |

Quelle ist der Episodenguide auf fernsehserien.de (https://www.fernsehserien.de/anne-will/episodenguide), abgerufen im November 2026. Erfasst wurden alle dort genannten Gäste. Die Moderatorin wird nicht erfasst, weil nur die Gäste untersucht werden.

Das Netzwerk ist ein *gerichtetes two-mode Netzwerk*. Es enthält drei Arten von Knoten: Gäste, Folgen und Parteien. Alle Kanten gehen von einem Gast aus.

## Umgang mit fehlenden Werten
Fehlende Werte bleiben leer. Gäste ohne Parteizugehörigkeit erhalten keine Kante zu einer Partei.

# EDGE-Attribute

**Grundregel** 
Die Edgelist darf pro Spalte immer nur einen Wert enthalten. Bis auf die ID idealerweise numerisch codiert (als Zahl).

**from**  
ID des Gastes (Sender der Kante)

Definiert den Sender in gerichteten Netzwerken. 
Entspricht ID in der Nodelist. 
Keine Sonderzeichen, nur ein Wort.

**to**  
ID der Folge oder der Partei (Empfänger der Kante)

Definiert den Empfänger in ungerichteten Netzwerken.
Entspricht ID in der Nodelist. 
Keine Sonderzeichen, etc. 

**relationship**  
Art der Beziehung  
1 = Gast war in dieser Folge zu Gast  
2 = Gast gehört dieser Partei an  

Jede Person erhält höchstens eine Kante zu einer Partei, auch wenn sie in mehreren Folgen zu Gast war.

# NODE-Attribute

**id**  
Eindeutige ID des Knotens  
Gäste: Initialen von Vor- und Nachname in Kleinbuchstaben. Namenszusätze und Adelstitel wie von der oder Graf werden weggelassen, zum Beispiel ul für Ursula von der Leyen. Haben zwei Personen dieselben Initialen, wird ein weiterer Buchstabe ergänzt.  
Folgen: Folgennummer (500, 501, 502, 503)  
Parteien: übliches Kürzel ohne Sonderzeichen (CDU, SPD, FDP, Gruene, Linke)

**name**  
Voller Name des Gastes. Bei Folgen: Folge 500 und so weiter. Bei Parteien: Name der Partei.

**party**  
Parteikürzel wie bei id, laut fernsehserien.de zum Zeitpunkt der Sendung. Leer bei Parteilosen, bei Folgen und bei Parteien.

**type**  
Seite des two-mode Netzwerks  
FALSE = Gast  
TRUE = Folge oder Partei  

**sector**  
Bereich, in dem der Gast tätig ist. Es zählt die Rolle, in der die Person eingeladen wurde. Leer bei Folgen und Parteien.  
Politik = Abgeordnete, Regierungsmitglieder, Parteivorsitzende, EU-Kommission, Staatsoberhäupter  
Wissenschaft = Hochschulen, Forschungsinstitute und Think Tanks  
Medien = Journalistinnen und Journalisten  
Militaer = Soldaten, auch im Ruhestand  
Diplomatie = Botschafterinnen und Botschafter  
Kultur = Schriftstellerinnen, Schriftsteller, Künstlerinnen und Künstler  

**country**  
Staatsangehörigkeit des Gastes. Bei mehreren zählt die zuerst genannte. Steht sie nicht auf fernsehserien.de, wurde sie nachgeschlagen. Leer bei Folgen und Parteien.

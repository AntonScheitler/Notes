## Praedikate auf Mengen
#### Existenz
- Das **exists** Schluesselwort dient als Existenzquantor in SQL
- In vielen Szenarien kann **exists** auch durch **in** ersetzt werden
###### Beispiel
```sql
select p.Name
from professoren p
where not exists (select * from 
				 vorlesungen v
				 where v.gelesenVon = p.PersNr)
```
```sql
select p.Name
from professoren p
where p.PerNr not in (select v.gelesenVon from 
					 vorlesungen v)
```
- Gibt alle Professoren zurueck, die keine Vorlesungen halten
#### Mengenvergleich
- Mithilfe von **all** kann ein Element mit einer Menge von Elementen verglichen werden
###### Beispiel
```sql
select s1.Name
from studenten s1
where s1.Semester >= (select s2.Semester
					from studenten s2)
```
- Gibt die Studenten zurueck, die die groesste Anzahl an Semestern haben
## Aggregation
- Bei einer Aggregation wird eine SQL Query an einigen Stellen erweitert
#### Select
- Sollen Summen oder Durchschnitte von Attributen ausgegeben werden, so wird dies ueber Funktionen wie **sum** oder **avg** erreicht
#### Group By
- Mithilfe von **group by** wird angegeben, nach welchen Attributen gruppiert wird
- Generell muss nach jedem Attribut gruppiert werden, welches nicht bereits durch Funktionen wie **sum** oder **avg** aggregiert wird
#### Having
- Muessen fuer die Aggregationen von Attributen bestimmte Praedikate gelten, so werden diese hier angegeben
#### Beispiel
```sql
select gelesenVon, sum(SWS)
from vorlesungen
group by gelesenVon
having avg(SWS) >= 3
```
- Gibt Professoren aus und summiert die SWS ihrer Vorlesungen
- Hierbei werden nur Professoren betrachtet, deren Vorlesungen im Durchschnitt 3 SWS haben
## Unteranfragen
- In vielen Szenarien kann es helfen, eine Unteranfrage in die SQL Anfrage einzubauen
#### Praedikate
- Praedikate koennen mithilfe von Unteranfragen formuliert werden
###### Beispiel
```sql
select s.Name
from studenten s
where s.GebDat < (select max(p.GebDat)
				 from professoren p)
```
- Gibt alle Studenten aus, die aelter sind als jeder Professor
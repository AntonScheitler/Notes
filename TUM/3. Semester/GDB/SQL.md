## Praedikate auf Mengen
#### Existenzquantor
- Das **exists** Schluesselwort dient als Existenzquantor in SQL
- In vielen Szenarien kann **exists** auch durch **in** ersetzt werden
###### Beispiel
```sql
select p.Name
from professoren p
where p.PerNr not in (select v.gelesenVon from 
					 vorlesungen v)
```
- Gibt alle Professoren zurueck, die keine Vorlesungen halten
#### Allquantor
- Es gibt keinen expliziten Allquantor in SQL
- Um das Verhalten eines Allquantors zu imitieren, kann ein **not exists** mit negiertem Praedikat verwendet werden
###### Beispiel
```sql
select p.Name
from professoren p
where not exists (select * from 
				 vorlesungen v
				 where v.gelesenVon = p.PersNr)
```
- Gibt alle Professoren zurueck, die keine Vorlesungen halten
#### Mengenvergleich
- Mithilfe von **all** kann ein Element mit einer Menge von Elementen verglichen werden
###### Beispiel
```sql
select s1.Name
from studenten s1
where s1.Semester >= all (select s2.Semester
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
## Common Table Expression
- Die Ergebnisse von Anfragen koennen als Tabelle abgespeichert und weiterverwendet werden
#### Beispiel
```sql
with h as (select VorlNr, count(*) as anzahlProVorl from hoeren group by VorlNr),
	 g as (select count(*) as gesamtAnzahl from Studenten)

select h.VorlNr, h.anzahlProVorl/g.gesamtAnzahl as Marktanteil from g, h
```
- Gibt den Marktanteil an Studenten jeder Vorlesung aus
## Rekursion
- Um transitive Beziehungen zu erfassen, koennen Tabellen rekursiv generiert werden
#### Beispiel
```sql
with recursive TransVorl(Vorg, Nachf) as (
	select Vorgaenger, Nachfolger from voraussetzen
	union all
	select t.Vorg, v.Nachfolger
	from TransVorl t, voraussetzen v
	where t.Nachf = v.Vorgaenger
)

select Titel from Vorlesungen
where VorlNr in (
	select Vorg from TransVorl
	where Nachf in (
		select VorlNr from Vorlesungen where Titel='Der Wiener Kreis'
	)
)
```
- Gibt alle Vorgaengervorlesungen der Vorlesung "Der Wiener Kreis" aus
## Sichten
- Aehnlich zu Common Table Expressions, koennen mit Sichten, Anfragen als Tabellen abgespeichert werden
- Diese werden jedoch in den Speicher geschrieben und sind ueber mehrere Anfragen verfuegbar
#### Beispiel
```sql
create view PruefGuete(Name, GueteGrad) as (
	select prof.Name, avg(pruef.note)
	from Professoren prof join pruefen pruef on prof.PersNr = pruef.PersNr
	group by prof.Name, prof.PersNr
	having count(*) > 50
)
```
- Erstellt eine Sicht von Professoren und ihren durchschnittlichen Noten
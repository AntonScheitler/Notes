## Referentielle Integritaet
- Fremdschluessel einer Relation muessen auf existierende Tupel verweisen, oder null sein 
- Die Intigritaet muss erhalten bleiben, falls sich das referenzierte Tupel aendert oder geloescht wird
- Hierfuer gibt es unterschiedliche Herangehensweisen
#### Cascade
- Mithilfe des **cascade** Schluesselworts werden die Aenderungen kaskadiert
- Wird das referenzierte Tupel beispielsweise geloescht, so wird auch das referenzierende Tupel geloescht
#### Set Null
- Mithilfe des **set null** Schluesselworts wird der Fremdschluessel bei Aenderungen auf null gesetzt
## Statische Integritaetsbedingungen
- Mithilfe von statischen Integritaetsbedingungen wird festgelegt, welche Werte ein Attribut annehmen kann
- Diese Integritaetsbedingungen werden mithilfe von **check** definiert
###### Beispiel
```sql
create table Users(
	name varchar(30),
	...
	age integer check(age > 0)	
);
```
- Es wird sichergestellt, dass das Alter eines Nutzers positiv ist
```sql
create table Likes(
	id integer,
	tweet_id integer,
	...
	creation_date date check(not exists(
			select * from Tweet t
			where t.id = tweet_id
			and creation_date < t.creation_date
		)
	)
	foreign key (tweet_id) references Tweet(id)
)
```
- Es wird sichergestellt, dass ein Like nicht vor seinem entsprechenden Tweet erstellt werden kann
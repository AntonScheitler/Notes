## Relation
- Relationen sind Teilmengen aus Kreuzprodukten unterschiedlicher Werte, die ihre Attribute annehmen koennen
- Tupel sind Elemente einer Relation
- Mithilfe eines Schemas wird das Format einer Relation definiert
#### Schluessel
- Ein Schluesselkandidat ist eine minimale Menge an Attributen, die jedes Tupel eindeutig identifiziert
- Einer der Schluesselkandidaten wird als Primaerschluessel der Relation ausgewaehlt
#### Ableitung aus Entities
- Relationen koennen mithilfe der Entities eines [[Konzeptuelle Modellierung|Entity-Relationship-Modells]] hergeleitet werden
- Hierbei koennen die Attribute des Entities einfach als Attribute der Relation verwendet werden
###### Beispiel
![[Pasted image 20231025112648.png]]
![[Pasted image 20231025112658.png]]
#### Beispiel
![[Pasted image 20231025111701.png]]
## Beziehungen
- Unterschiedliche Beziehungsarten werden auf unterschiedliche Weisen in ein relationales Datenmodell uebersetzt
#### N:M Beziehungen
- Eine zusaetzliche Relation wird erstellt, welche die Schluessel der beiden Relationen speichert, die in einer Beziehung zueinander stehen
- Der Primaerschluessel der Relation setzt sich aus den gespeicherten Schluesseln zusammen
#### 1:N Beziehungen
- Die Relation auf der "N" Seite der Beziehung referenziert die jeweils andere Relation mithilfe eines Fremdschluessels
#### 1:1 Beziehungen
- Eine beliebige Relation referenziert die jeweils andere mithilfe eines Fremdschluessels
#### Beispiel
![[Pasted image 20231025131848.png]]
![[Pasted image 20231025131909.png]]
## Relationale Algebra
- Unterschiedliche Operationen koennen auf Relationen angewandt werden
#### Selektion
- Mithilfe einer Selektion $\sigma$ kann auf einzelne Tupel einer Relation zugegriffen werden
###### Beispiel
![[Pasted image 20231025132134.png]]
#### Projektion
- Mithilfe einer Projektion $\Pi$ kann auf einzelne Attribute einer Relation zugegriffen werden
###### Beispiel
![[Pasted image 20231025132226.png]]
#### Joins
- Zwei Relationen koennen ueber einen join verknuepft werden
- Hierfuer wird mithilfe eines kartesischen Produkts jedes Tupel einer Relation mit jedem Tupel der Anderen verknuepft
- Ueber ein Praedikat wird das Ergebnis gefiltert
###### Outer Joins
- Bei einem outer join werden auch Zeilen inkludiert, die das Praedikat nicht erfuellen
- Dort werden fehlende Werte mit null aufgefuellt
###### Beispiel
![[Pasted image 20231025133039.png]]
![[Pasted image 20231025133222.png]]
## Division
- Es seien $R, S$ Relationen mit den Attributen $\beta, \gamma$, wobei $\gamma \subset \beta$ ist
- Es sei $\overline{R} = \Pi_{\beta \setminus \gamma}(R)$
- Es werden genau die Zeilen aus $\overline{R}$ ausgegeben, deren Gegenstuecke in $R$, $S$ enthalten
#### Beispiel
![[Pasted image 20231025193644.png]]
## Aggregation und Gruppierung
- Tupel einer Relation koennen ausgehend von ihren Attributwerten gruppiert werden
- Bei einer Gruppierung koennen Attribute aggregiert, beispielsweise summiert werden
#### Beispiel
![[Pasted image 20231025192743.png]]
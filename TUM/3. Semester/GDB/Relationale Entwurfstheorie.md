## Funktionale Abhaengigkeiten
- Es sei $R = \{A, B, C, D\}$ ein beliebiges Schema mit $a, b \subseteq R$
- $b$ ist genau dann funktional abhaengig von $a$, falls gilt:
$$\forall r, s \in R: \space r.a = s.a \Rightarrow r.b = s.b$$
#### Beispiel
![[Pasted image 20231201154232.png]]
#### Schluessel
- $a$ ist ein Superschluessel, falls $a \rightarrow R$
- $b$ ist voll funktional abhaengig von  $a$, falls $a \rightarrow b$ gilt und $a$ nicht verkleinert werden kann
- $a$ ist genau dann ein Kandidaten-Schluessel, falls $R$ voll funktional abhaengig von $a$ ist
#### Anomalien
- Liegen redundante Daten in einem Schema vor, so kann es zu verschiedenen Anomalien kommen
###### Einfuege-Anomalie
- Wird ein neues Tupel eingefuegt, so koennen viele Informationen fehlen
![[Pasted image 20231201161614.png]]
###### Update-Anomalie
- Inkonsistente Daten koennen auftreten, falls nicht alle Vorkommen eines Wertes geaendert werden
![[Pasted image 20231201161744.png]]
###### Loesch-Anomalie
- Wird ein Tupel geloescht, so werden brauchbare Informationen mitgeloescht
![[Pasted image 20231201161831.png]]
#### Dekomposition
- Um Anomalien zu verhindern, werden Relationen aufgeteilt
- Hierbei muss sichergestellt werden, dass keine Informationen verloren gehen und funktionale Abhaengigkeiten erhalten bleiben
## Normalformen
- Mithilfe von Normalformen werden Schemaformate definiert
#### 1. Normalform
- Eine Relation ist in der 1. Normalform, falls alle Attribute atomar sind
###### Beispiel
![[Pasted image 20231201163407.png]]
#### 2. Normalform
- Eine Relation ist in der 2. Normalform, falls jedes Nichtschluessel-Attribut voll funktional abhaengig von jedem Kandidatenschluessel ist
- Um die 2. Normalform zu garantieren kann eine Aufteilung der Relation noetig sein
![[Pasted image 20231201164535.png]]
#### 3. Normalform
- Eine Relation ist in der 3. Normalform, falls keine funtionalen Abhaengigkeiten zwischen den Nichtschluessel-Attributen bestehen
![[Pasted image 20231201165436.png]]
![[Pasted image 20231201165449.png]]
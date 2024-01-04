## Funktionale Abhaengigkeiten
- Es sei $R = \{A, B, C, D\}$ ein beliebiges Schema mit $a, b \subseteq R$
- $b$ ist genau dann funktional abhaengig von $a$, falls jedem $a$ genau ein $b$ zugeordnet werden kann
#### Beispiel
![[Pasted image 20231201154232.png]]
#### Schluessel
- $a$ ist ein Superschluessel, falls $a \rightarrow R$
- $b$ ist voll funktional abhaengig von  $a$, falls $a \rightarrow b$ gilt und $a$ nicht verkleinert werden kann
- $a$ ist genau dann ein Kandidaten-Schluessel, falls $R$ voll funktional abhaengig von $a$ ist
#### Mehrwertige Abhaengigkeiten
- $\beta$ und $\gamma$ sind mehrwertig abhaengig von $\alpha$ falls die Tupel $t1, t2, t3, t4$ so gewaehlt werden koennen, dass gilt:
$$t1.\alpha = t2.\alpha = t3.\alpha = t4.\alpha$$
$$t1.\beta = t3.\beta, \space \space t2.\beta = t4.\beta$$
$$t1.\gamma = t4.\gamma, \space \space t2.\gamma = t3.\gamma$$
- Da $t1 = t2 = t3 = t4$ moeglich ist, sind $\beta$ und $\gamma$ mehrwertig abhaengig von $\alpha$, falls $a \rightarrow \beta\gamma$ 
###### Beispiel
![[Pasted image 20231214105825.png]]
#### Attributhuelle
- Die Huelle eines Attributes $\alpha$ ist die Menge an funktional abhaengigen Attributen, ausgehend von $\alpha$
###### Beipsiel
![[Pasted image 20231214110204.png]]
#### Kanonische Ueberdeckung
- Die kanonische Ueberdeckung einer Menge von funktionalen Abhaengigkeiten wird ueber mehrere Schritte bestimmt :
	1. Linksreduktion: Die linken Seiten der funktionalen Abhaengigkeiten duerfen keine ueberfluessigen Attribute enthalten
	2. Rechtsreduktion: Die rechten Seiten der funktionalen Abhaengigkeiten duerfen keine Attribute enthalten, die von einem anderen Attribut auf der rechten Seite funktional abhaengig sind
	3. Entfernen funktionaler Abhaengigkeiten der Form $a \rightarrow \emptyset$
	4. Vereinigungsregel: Funktionale Abhaengigkeiten, deren linke Seiten gleich sind, werden zusammengefasst
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
- Bis zur 3. Normalformen ist die Normalisierung von Relationen abhaengigkeitserhaltend
![[Pasted image 20231201165436.png]]
![[Pasted image 20231201165449.png]]
###### Synthese
1. Die kanonische Ueberdeckung wird ermittelt
2. Fuer jede funktionale Abhaengigkeit wird eine Relation erstellt
3. Relationen, die in anderen enthalten sind, werden eliminiert
4. Eine der Relationen muss einen Kandidatenschluessel enthalten
###### Beispiel
![[Pasted image 20231207205911.png]]
#### Boyce-Codd Normalform
- Eine Relation ist in Boyce-Codd Normalform, falls jedes Attribut nur von dem Superschluessel funktional abhaengt
###### Dekomposition
- Alle funktionalen Abhaengigkeiten, die die Boyce-Codd Normalform verletzen, bilden eine neue Relation
###### Beispiel
![[Pasted image 20231207213921.png]]
#### 4. Normalform
- Eine Relation ist in der 4. Normalform, falls jede mehrwertige Abhaengigkeit von einem Kandidatenschluessel abhaengt
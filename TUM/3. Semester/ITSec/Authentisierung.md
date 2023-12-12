## Authentisierungsklassen
- Die Authentizitaet einer Entitaet kann auf unterschiedliche Weisen bewiesen werden
#### Authentisierung durch Wissen
- Die Authentizitaet kann durch das Wissen bewiesen werden, das nur die Entitaet besitzt
- Dies kann mithilfe von Passwoertern oder OTPs realisiert werden
#### Authentisierung durch Besitz
- Die Authentizitaet kann mithilfe eines Gegenstands bewiesen werden, den nur die Entitaet besitzt
###### Hardware-basierte OTPs
- Jedes Geraet besitzt einen Token und einen Seed, die dem Server bekannt sind
- Nach einem Zeitintervall wird ein OTP neu ermittelt durch:
$$OTP = AES(Token||s||Zeit)$$
- Das Geraet und der Server erzeugen jeweils das OTP und vergleichen es miteinander
#### Authentisierung durch Biometrie
- Die Authentizitaet kann mithilfe von biometrischen Merkmalen bewiesen werden, die nur die Entitaet besitzt
###### Vorgehen
- Die Merkmale muessen vorab erfasst und gespeichert werden
- Anschliessend koennen sie erneut erfasst und mit den gespeicherten Merkmalen verglichen werden
#### Multi-Faktor Authentisierung
- Authentisierungsklassen koennen beliebig miteinander kombiniert werden, um die Sicherheit weiter zu steigern
## Challenge-Response Verfahren
- Der Server sendet eine Challenge an einen Nutzer
- Der Nutzer beweist seine Authentizitaet durch das Loesen der Challenge und senden einer Response
#### Symmetrisches CR
- Ein symmetrisches CR setzt einen geteilten Schluessel vorraus
- Die pruefende Instanz $B$ schickt eine Zufallszahl an die Entitaet $A$
- $A$ verschluesselt die Zufallszahl mit dem geteilten Schluessel und sendet sie an $B$
- $B$ kann die Nachricht nun entschluesseln und mit der Zufallszahl vergleichen
###### Beispiel
![[Pasted image 20231205113022.png]]
#### Asymmetrisches CR
- TODO
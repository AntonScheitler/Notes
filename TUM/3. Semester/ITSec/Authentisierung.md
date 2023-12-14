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
- Diese Merkmale muessen universell, eindeutig und bestaendig sein
###### Vorgehen
- Die Merkmale muessen ueber das Enrollment vorab erfasst und gespeichert werden
- Anschliessend koennen sie erneut erfasst und mit den gespeicherten Merkmalen verglichen werden
###### Metriken
- Ein False Positive entsteht, falls einer unautorisierten Entitaet Zugang gewaehrt wird
- Ein False Negative entsteht, falls einer autorisierten Entitaet Zugang verweigert wird
- Die False Acceptance Rate gibt die Haeufigkeit von False Positives an
- Die False Rejection Rate gibt die Haeufigkeit von False Negatives an
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
- Die pruefende Instanz $B$ verifiziert das [[Public Key Infrastructure|Zertifikat]] der Entitaet $A$ und verschickt eine Zufallszahl an sie
- $A$ verschluesselt die Zufallszahl mit ihrem Private Key und schickt das Ergebnis an $B$
- $B$ entschluesselt die Nachricht mit dem Public Key von $A$ und vergleicht das Ergebnis mit der Zufallszahl
###### Beispiel
![[Pasted image 20231214095259.png]]
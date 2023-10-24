## Angriffsklassen
- Angriffe auf Systeme koennen unterschiedliche Formen annehmen
#### Ungenuegende Eingabevalidierung
- Mithilfe besonderer Eingaben koennen Angreifer das Fehlverhalten eines Systems ausnutzen
###### Bufferoverflow
- Ein lesender oder schreibender Zugriff auf ein Datum geht ueber die Speichergrenzen dieses Datums hinaus
- Hierdurch koennen Daten anderer Programmteile, wie Ruecksprungadressen ueberschrieben werden
###### Code Injection
- Befehle werden in eine Eingabe integriert, sodass das System diese mit seinen Privilegien ausfuehrt
- Somit koennen beispielsweise Datenbankeintraege ausgelesen oder geloescht werden
###### Cross-Site-Scripting
- Ueber eine Eingabe kann JavaScript Code in eine Website eingebracht werden, welcher von anderen Nutzern ausgefuehrt wird
- Hierdurch koennen die Passwoerter von Nutzern ausgelesen werden
![[Pasted image 20231024103547.png]]
#### Identitiaetsdiebstahl
- Angreifer sind in der Lage, in ein System unter einer fremden Identitaet einzudringen
###### Man-in-the Middle
- Zwei Nutzer tauschen Daten aus, wobei Nachrichten ueber einen Dritten weitergeleitet werden
- Der Angreifer gibt sich hierbei als Gateway zum Kommunikationsservice aus
- Die Kommunikation kann hierdurch abgehoert, oder manipuliert werden
![[Pasted image 20231024103533.png]]
#### Angriffe auf die Verfuegbarkeit
- Angreifer sind in der Lage, die Verfuegbarkeit eines Systems zu beeintraechtigen
###### Distributed Denial of Service
- Eine grosse Menge verteilter Maschinen sendet Anfragen an ein System
- Das System wird hierdurch ueberlastet und kann auf Anfragen anderer Nutzer nicht mehr antworten
## Klassen von Schadcode
- Code, der darauf abzielt, Systemen zu schaden kann auf unterschiedliche Weisen in diese eindringen
#### Viren
- Viren muessen von dem Wirtssystem ausgefuehrt werden, um agieren zu koennen
#### Trojaner
- Trojaner bieten nuetzliche Funktionen, enthalten jedoch auch Schadcode, der bei der Ausfuehrung den Nutzer befaellt
## Schutzziele
- Grundsaetzlich muss ein System stets die Vertraulichkeit, Integritaet und Verfuegbarkeit wahren
#### Informationsvertraulichkeit
- Informationen muessen vor unautorisierten Zugriffen geschuetzt werden
- Dies kann durch Datenverschluesselung, sowie Zugriffskontrollen gewaehrt werden
#### Datenintegritaet
- Systeme duerfen nicht mit unautorisiert modifizierten Daten arbeiten
- Hierfuer koennen Zugriffe kontrolliert und neue Daten mit Backups verglichen werden
#### Systemverfuegbarkeit
- Die Funktionalitaet und Verfuegbarkeit eines Systems darf nicht beeintraechtigt werden
- Firewalls koennen die Verfuegbarkeit schuetzen
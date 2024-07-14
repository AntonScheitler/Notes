## Sitzungsschicht
- Eine Session zwischen Kommunikationspartnern kann aufgebaut werden, die ueber einzelne Datentransfers bestehen bleibt 
- Beispielsweise werden bei HTTP ueber Cookies, oder bei TLS ueber Session-IDs, Sessions ermoeglicht
## Darstellungsschicht
- In der Darstellungsschicht werden Daten komprimiert und verschluesselt, sowie einheitlich dargestellt
#### Huffman Code
- Die Kodierung von Daten erfolgt entweder ueber fix-length Codes, wie unicode, oder variable-length Codes, wie der Huffman Code
###### Konstruktion
- Bei dem Huffman Code, wird jedes Symbol als Teilbaum interpretiert
- In jedem Schritt werden die Teilbaeume, mit der geringsten Wahrscheinlichkeit zu einem groesseren Teilbaum zusammengefasst
- Wurden alle Teilbaeume gruppiert, so werden linke Kanten stets mit $0$ und rechte mit $1$ beschriftet, sodass das Codewort eines Symbols anhand des Pfades von der Wurzel abgelesen werden kann
###### Eigenschaften
- Der Huffman Code ist ein optimaler, praefixfreier Code
- Somit ist kein Codewort, Praefix eines anderen und die mittlere Codewortlaenge $\sum_{i \in A} p(i) \cdot |c(i)|$ ist minimal
###### Beispiel
![[Pasted image 20240714100808.png]]
## Anwendungsschicht
- Die Protokolle der Anwendungsschicht stellen Nutzeranwendungen, Dienste des Netzes bereit
- Diese Protokolle erfuellen somit unterschiedliche Zwecke
#### Domain Name System
- Um Hosts ueber meschlich lesbare Namen adressieren zu koennen, muessen diese Namen in IP Adressen uebersetzt werden
- Diese Uebersetzung wird durch das Domain Name System gehandhabt, welches aus dem Domain Namespace, Nameservern, sowie Resolvern besteht
###### Domain Namespace
- Der Domain Namespace wird als Baum dargestellt, wobei jeder Knoten ein Label repraesentiert, die dann zu Domain Names zusammengesetzt werden koennen
- Ein Domain Name ist Fully Qualified, falls er aus einem Pfad von Knoten bis Wurzel entsteht und somit auf einem . endet
- Die Schichten des Baums werden hierbei als Root, Top Level Domain, Second Level Domain, sowie Subdomain bezeichnet
![[Pasted image 20240714102418.png]]
###### Nameserver
- Der Domain Namespace wird in Form einer verteilten Datenbank ueber mehrere Nameserver hinweg gespeichert
- Jeder Nameserver ist hierbei fuer eine Zone, des Namespaces zustaendig, beziehungsweise autoritativ
- Jede Zone besitzt einen primaeren Nameserver, der Veraenderungen daran vornehmnen kann, sowie beliebig viele sekundaere Nameserver, welche nur eine Kopie der Zone enthalten
###### Resolver
- Um einen Domain Name ueber den verteilten Domain Namespace aufzuloesen, werden Resolver verwendet
- Ein Resolver schickt iterativ Anfragen an die Nameserver, die fuer das naechste Label im Domain Name autoritativ sind, angefangen bei einem Nameserver fuer die Root Zone
- Die initiale Anfrage an den Resolver wird als rekursive Namensaufloesung bezeichnet, wobei es sich bei den Anfragen des Resolvers um eine iterative Namensaufloesung handelt
- Um die Authentizitaet der Nameserver zu garantieren, muss den Root Servern vertraut werden
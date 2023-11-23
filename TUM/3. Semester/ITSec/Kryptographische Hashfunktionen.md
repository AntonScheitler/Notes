## Allgemeines
- Mithilfe von Hashfunktionen koennen Daten digital signiert werden, um die [[Schwachtellen und Angriffe|Datenintegritaet]] zu wahren
- Die Ausgabe einer Hashfunktion hat stets eine feste Laenge
#### Kompressionsfunktionen
- Um eine Nachricht auf die korrekte Laenge zu reduzieren, wird diese in Bloecke unterteilt und komprimiert
- Die komprimierte Nachricht wird in einen Hashwert umgewandelt
###### Beispiel
![[Pasted image 20231114103420.png]]
#### Kollisionen
- Da Hashfunktionen nicht injektiv sind, koennen zwei unterschiedliche Nachrichten denselben Hashwert besitzen
#### Eigenschaften
- Die Eingabe einer Hashfunktion soll nicht anhand der Ausgabe bestimmt werden koennen
- Eine Nachricht $m'$ zu bestimmen, welche denselben Hashwert hat wie eine Nachricht $m$ soll schwer sein
## Klassen von Hashfunktionen
- Hashfunktionen koennen auf unterschiedliche Weisen realisiert werden
#### Blockchiffre
- Ein Klartext wird mithilfe einer [[Kryptographie|Blockchiffre]] verschluesselt
- Der letzte Cipherblock wird als Hashwert verwendet
###### Beispiel
![[Pasted image 20231114105523.png]]
#### Dedizierte Hashfunktionen
- Eine Bitreihe wird stueckweise mit den Klartext verxodert und durch Funktionen permutiert
- Die Ausgabe setzt sich aus beliebig vielen, permutierten Bitreihen zusammen
###### Beispiel
![[Pasted image 20231114111610.png]]
#### Passworthashfunktionen
- Passwoerter werden gehasht abgespeichert
- Um sich zu authentifizieren, wird die Eingabe gehasht und mit dem Passworthash verglichen
- Um Sicherheit zu gewaehren, werden die Hashfunktionen abgebremst
#### Message Authentication Code
- Kommunikation mit einem mac erfordert einen Schluessel der vorab beiden Entitaeten bekannt ist
- Ein mac wird erstellt, indem der Schluessel in die Nachricht eingebaut und das Ergebnis gehasht wird
- Der Empfaenger ueberprueft die Authentizitaet des Senders, indem er den mac nachbaut und mit dem empfangenen mac vergleicht
###### Beispiel
![[Pasted image 20231114112644.png]]
###### Length Extension Angriff
- Ein Angreifer kann eine Nachricht mit mac $N$ und den Hashwert $h$ abfangen
- Fuer manche Hashverfahren $f$ gilt:
$$f(x||y) = f(f(x)||y)$$
- Der Angreifer kann somit $N' = N||M$, sowie $h' = f(h||N') = f(f(key||N)||M) = f(key||N||M)$ erzeugen und an den Empfaenger weiterschicken
- Rekonstruiert der Empfaenger nun $h'$ ueber $h' = f(key||N') = f(key||N||M)$, bleibt die Manipulation unbemerkt
#### Digitale Signatur
- TODO
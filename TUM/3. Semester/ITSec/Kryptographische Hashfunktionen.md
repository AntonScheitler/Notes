## Allgemeines
- Mithilfe von Hashfunktionen koennen Daten digital signiert werden, um die [[Schwachtellen und Angriffe|Datenintegritaet]] zu wahren
- Die Ausgabe einer Hashfunktion hat stets eine feste Laenge
#### Merkle-Damgard Konstruktion
- Um eine Nachricht auf die korrekte Laenge zu reduzieren, wird diese in Bloecke unterteilt und komprimiert
- Die komprimierte Nachricht wird in einen Hashwert umgewandelt
###### Beispiel
![[Pasted image 20231114103420.png]]
#### Kollisionen
- Da Hashfunktionen nicht injektiv sind, koennen zwei unterschiedliche Nachrichten denselben Hashwert besitzen
#### Eigenschaften
- Hashfunktionen sind effizient berechenbar
- Die Eingabe einer Hashfunktion soll nicht anhand der Ausgabe bestimmt werden koennen
- Die Kollisionsresitenz ist schwach, falls es schwer ist, eine Nachricht $m'$ zu bestimmen, welche denselben Hashwert hat wie eine gegebene Nachricht $m$ hat
- Die Kollisionsresitenz ist stark, falls es schwer ist, ein Nachrichtenpaar $m', m$ zu bestimmen, deren Elemente denselben Hashwert haben
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
- Generell sollte das Prinzip "Encrypt then mac" befolgt werden
###### Beispiel
![[Pasted image 20231114112644.png]]
###### Length Extension Angriff
- Length Extension Angriffe sind bei Hashfunktionen moeglich, die nach dem Merkle-Damgard Prinzip arbeiten
- Hierbei kann mit einem gegebenen Hash weitergehasht werden
- Ein Angreifer kann eine Nachricht mit mac $N$ und den Hashwert $h$ abfangen
- Der Angreifer kann somit $N' = N||M$, sowie $h' = f_h(M) = f(key||N||M)$ erzeugen und an den Empfaenger weiterschicken
- Rekonstruiert der Empfaenger nun $h'$ ueber $h' = f(key||N') = f(key||N||M)$, bleibt die Manipulation unbemerkt
#### Digitale Signatur
- Um die Urheberschaft von Daten zu beweisen, werden asymmetrische Verfahren, wie RSA verwendet
- Eine Nachricht wird hierbei gehasht und das Ergebnis durch den privaten Schluessel einer Entitaet verschluesselt
- Der Empfaenger ueberprueft die Urheberschaft, indem er die Signatur durch den public key entschluesselt, den Hash nachbaut und vergleicht
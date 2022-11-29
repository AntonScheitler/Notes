## Allgemeines
- Speicherbausteine basieren auf dem Konzept der Rueckkopplung
- Indem der Ausgang einer Schaltung als Eingang wiederverwendet wird, wird Speicherverhalten simuliert
#### Beispiel
![[Pasted image 20221129161417.png]]
## RS-Flipflop
- Indem zwei OR Gatter parallel rueckgekoppelt werden, kann mithilfe eines SET und eines RESET Signals ein Bit gespeichert werden
#### Beispiel
![[Pasted image 20221129162651.png]]
![[Pasted image 20221129162707.png]]
## D-Latch
- Anstelle eines RS-Latches koennen sowohl SET, als auch RESET von einem Eingangssignal abgeleitet werden
- Um das Latch anzusteuern, wird ein ENABLE Signal mit dem Eingangssignal verundet
#### Taktgesteuerte D-Flipflops
- Ueber OR Gatter kann das Signal des Takts verzoegert werden, sodass ein Speicherbaustein nur zum Zeitpunkt der aufsteigenden Flanke angesteuert werden kann
#### Beispiel
![[Pasted image 20221129163006.png]]
![[Pasted image 20221129165727.png]]
## Mehrstellige Speicher
- Mehrstellige Binaezahlen koennen mithilfe einer Kombination aus Adressbits, sowie D-Latches und Multiplexern ueberschrieben und ausgelesen werden
#### Beispiel
![[Pasted image 20221129164144.png]]
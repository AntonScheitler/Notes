## Allgemeines
- Die Sicht auf dem System haengt allein von seinen Software-Schnittstellen ab
- Virtuelle Laufzeitumgebungen koennen diese Software-Schnittstellen emulieren und virtuelle Ressourcen auf Physische abbilden
#### Schnittstellen
- Software-Schnittstellen koennen unterschiedlich Klassifiziert werden
###### Instruction Set Architecture
- Die Instruction Set Architecture beschreibt das Interface zwischen der Hardware und dem Betriebssystem
- Man unterscheidet hierbei eine System-ISA und eine User-ISA
###### Application Binary Interface
- Das Application Binary Interface beschreibt das Interface zwischen Anwendungen und dem Betriebssytem
- Die ABI umschliesst zudem die User-ISA
- In der Regel wird durch virtuelle Maschinen ein Application Binary Interface emuliert
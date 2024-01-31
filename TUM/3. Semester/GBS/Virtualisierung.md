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
## System Virtual Machines
- System Virtual Machines virtualisieren eine gesamte physische Maschine
#### Hypervisor
- System Virtual Machines werden von einem Hypervisor verwaltet
- Der Hypervisor bietet virtuelle Source ISAs, auf die die Gast Betriebssysteme aufbauen
- Die tatsaechlichen Hardwareressourcen werden somit nur durch den Hypervisor kontrolliert, der sie fuer die Gast-Systeme verwaltet
###### Beispiel
![[Pasted image 20240131101653.png]]
#### CPU Virtualisierung
- Die Instruktionen der virtuellen ISA muessen durch den Hypervisor ueber binary translation in die Target ISA uebersetzt werden
- Dies wird mithilfe von Caching und Just-In-Time Compilation beschleunigt
###### Arbeitsmodi
- Die Gast-Systeme werden im User Mode und der Hypervisor im Kernel Mode ausgefuehrt
- Fuehrt ein Gast-System sensitive Instruktionen aus, so wird eine Trap im Hypervisor ausgefuehrt
- Die Instruktionen werden dann ueberprueft und emuliert
- Der Hypervisor behaelt somit stets die Kontrolle ueber die virtuellen Maschinen
#### Speicher Virtualisierung
- Der Hypervisor muss den physischen Speicher zwischen mehreren Gast Systemen aufteilen und verwalten
###### Second Level Address Translation
- Eine zusaetzliche Ebene zur Adressuebersetzung wird eingefuehrt, um die Page Table eines Gast Systems auf physische Adressen abzubilden
![[Pasted image 20240131133731.png]]
###### Ballooning
- Ein balloon driver in einem Gast System kommuniziert mit dem Hypervisor
- Seiten, die durch den balloon driver alloziert wurden, koennen von dem Hypervisor genutzt werden
- Benoetigt der Hypervisor somit Speicher, so alloziert der driver Speicher und das Gast Betriebssytem entscheidet selbst, welche Seiten ausgelagert werden
## Container
- Container virtualisieren eine isolierte Umgebung fuer Benutzerprozesse und Teilen sich das Betriebssytem des Hosts mit anderen Containern
- Um Prozesse voneinander zu isolieren, werden Namespaces und Control Groups verwendet
#### Namespaces
- Mithilfe von Namespaces koennen Prozesse in bestimmten Aspekten voneinander isoliert werden
###### UTS Namespace
- Prozesse in unterschiedlichen UTS Namespaces koennen unterschiedliche Host- und Domainnamen haben
###### PID Namespace
- Prozesse in unterschiedlichen PID Namespaces koennen dieselben PIDs haben
- Es kann zudem eine Hierarchie von Namespaces angelegt werden
###### IPC Namespace
- Jeder IPC Namespace verwaltet eine Menge von IPC Identifiern und Message Queues
###### Mount Namespace
- Jedes Mount Namespace hat eine eigene Liste von Mount Points
#### Control Groups
- Prozesse koennen in einer Control Group zusammengefasst werden
- Fuer jede Control Group werden Ressourcen wie CPU-Cores und Speicher allokiert werden
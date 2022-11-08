## Aufgaben des Betriebssystems
- Ueber das Betriebssystem werden Datein, Prozesse und Speicher verwaltet ([[Speicherverwaltung]])
- Um alle Rechnerkomponenten verwalten zu koennen, verfuegt das Betriebssystem ueber einen priviligierten Modus
#### Moduswechsel
- Um vom Benutzer- zum Systemmodus zu wechseln, kann ein System Call ausgefuehrt werden
	- Bei einem System Call wird an eine vordefinierte Adresse im Betriebssystem gesprungen, eine Routine ausgefuehrt und anschliessend in dem Benutzermodus zurueckgekehrt
#### Interrupts
- Der Prozessor kann ueber Interrupts auf externe, asynchrone Ereignisse reagieren
- Die Ruecksprungadresse und Registerinhalte werden gesichert, bevor der Interrupt-Handler des Betriebssystems ausgefuehrt wird
#### Exceptions
- Beim Auftreten einer Exception wird das Programm mithilfe des Exception-Handlers des Betriebssystems korrigiert oder abgebrochen
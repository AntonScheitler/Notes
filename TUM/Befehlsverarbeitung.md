## Phasen der Befehlsverarbeitung
- Die Ausführung von Befehlen lässt sich in die Interpretations- und Ausführungsphase einteilen
### Interpretationsphase
- Die Adresse des auszuführenden Befehls wird im Befehlszähler gespeichert
- Über MAR und MDR wird der Befehl in das Instruktionsregister geladen und anschließend dekodiert und ausgeführt
- Nach dem Ausführen wird der Befehlszähler inkrementiert
### Ausführungsphase
- Die, im Befehl enthaltenen, Daten werden über MAR und MDR aus dem [[Hauptspeicher]] geholt und in Register geladen
- Über die ALU werden die Operanden verrechnet und das Ergebnis im Akkumulator abgespeichert
- Mithilfe von weiteren Befehlen kann das Ergebnis in den [[Hauptspeicher]] zurückgeschrieben werden
### Beispiel
![[Pasted image 20221024164610.png]]
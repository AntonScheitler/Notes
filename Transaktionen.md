## Allgemeines
- Transaktionen sind Datenuebertragungen mit bestimmten Eigenschaften
#### Eigenschaften
- Transaktionen werden atomar behandelt
- Transaktionen muessen valide sein und duerfen die Konsistenz der Datenbank nicht verletzen
- Transaktionen sind von anderen Transaktionen isoliert
- Aenderungen, die von Transaktionen herbeigefuehrt werden, sind dauerhaft
#### Ausfuehrung
- Eine Transaktion wird mit begin-of-transaction eingeleitet
- War die Transaktion erfolgreich, so werden die Aenderungen ueber commit zurueckgeschrieben
- War sie es nicht, so werden die Aenderungen durch abort zurueckgesetzt
## Fehlerbehandlung
- Die Atomaritaet und Dauerhaftigkeit von Transaktionen muss auch nach Abstuerzen garantiert werden
#### Logs
- Mithilfe von Logs werden Transaktionen und ihre Auswirkungen protokolliert
- Anhand der Logs kann der Zustand der Datenbank wiederhergestellt werden
###### Before-Image
- Das before-image ist der Zustand vor der Ausfuehrung einer gegebenen Transaktion
- Das before-image kann somit durch das after-image und den Undo der Tranaktion generiert werden
###### After-Image
- Das after-image ist der Zustand nach der Ausfuehrung einer gegebenen Transaktion
- Das after-image kann somit durch das before-image und den Redo der Transaktion generiert werden 
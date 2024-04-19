## Allgemeines
- Ein diskreter Wahrscheinlichkeitsraum wird durch eine Menge $\Omega = \{\omega_1, \omega2, ... \}$ von Elementarereignissen und ihren Wahrscheinlichkeiten festgelegt
- Fuer die Wahrscheinlichkeit der Elementarereignisse gilt:
$$\sum_{\omega \in \Omega} Pr[\omega] = 1$$
#### Ereignis
- Ein Ereignis ist eine Menge $E \subseteq \Omega$
- Fuer die Wahrscheinlichkeit $Pr[E]$ eines Ereignisses gilt:
$$Pr[E] = \sum_{\omega \in E} Pr[\omega]$$
###### Siebformel
- Um die Wahrscheinlichkeit der Vereinigung mehrerer Ereignisse zu berechnen, wird die Siebformel verwendet
$$Pr[A \cup B] = Pr[A] + Pr[B] - Pr[A \cap B]$$
- Fuer drei Ereignisse $A, B$ und $C$ gilt insbesondere:
$$Pr[A \cup B \cup C] = Pr[A] + Pr[B] + Pr[C] - Pr[A \cap B] - Pr[A \cap C] - Pr[B \cap C] + Pr [A \cap B \cap C]$$
## Bedingte Wahrscheinlichkeit
- Bei zwei Ereignissen $A$ und $B$ wird die bedingte Wahrscheinlichkeit $Pr[A|B]$ vom Eintreten von $A$, falls $B$ gegeben ist, definiert durch:
$$Pr[A|B] = \frac{Pr[A \cap B]}{Pr[B]}$$
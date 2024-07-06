## Statistische Verfahren
- Um den Wahrscheinlichkeitsraum zu bestimmen, der eine Phaenomen zugrunde liegt, werden Versuchsergebnisse genutzt
#### Schaetzvariablen
- Es sei $X$ eine Zufallsvariable mit der Dichte $f(x, \theta)$
- Eine Schaetzvariable $\overline{X}$ fuer $\theta$ wird aus mehreren Stichproben von $X$, beispielsweise durch das arithmetische Mittel, zusammengesetzt
- $\overline{X}$ ist erwartungstreu, falls gilt:
$$\mathbb{E}[\overline{X}] = \theta$$
- Die Groesse $\mathbb{E}[\overline{X} - \theta]$ wird als Bias der Schaetzvariable bezeichnet
###### Mean Squared Error
- Die Guete einer Schaetzvariable, wird durch den mean squared error gemessen:
$$MSE(\overline{X}) = \mathbb{E}[(\overline{X} - \theta)^2]$$
- Ist $\overline{X}$ erwartungstreu, so ist $MSE(\overline{X}) = Var[\overline{X}]$
- Somit folgt:
$$MSE(\overline{X}) = Var[\overline{X}] = \frac{1}{n}Var[X]$$
- Eine Schaetzvariable ist konsistent im quadratischen Mittel, falls $MSE \to 0$, fuer $n \to \infty$
###### Stichprobenmittel und -Varianz
- Die folgenden Zufallszahlen werden als Stichprobenmittel, beziehungsweise Stichprobenvarianz bezeichnet:
$$\overline{X} = \frac{1}{n} \sum_{i = 1}^n X_i, \; \; S^2 = \frac{1}{n - 1}\sum_{i = 1}^n(X_i - \overline{X})^2$$
- $\overline{X}$ ist hierbei ein erwartungstreuer Schaetzer fuer den Erwartungswert und $S^2$ einer, fuer die Varianz
#### Maximum Likelihood
- Es seien $X_1, ..., X_n$ eine Reihe von Kopien der Zufallsvariable $X$ und es sei $x_1, ..., x_n$ eine daraus resultierende Stichprobe
- Es sei $f(x; \theta) = Pr_{\theta}[X_i = x_i]$ die Dichtefunktion von $X_i$ in Abhaengigkeit von einem Parameter $\theta$
- Es kann somit eine Likelihood Funktion definiert werden, die beschreibt, wie wahrscheinlich eine beobachtete Stichprobe ist fuer einen gegeben Parameter $\theta$ ist:
$$L((x_1, ..., x_n), \theta) = L(\vec{x}, \theta)= Pr_{\theta}[X_1 = x_1, ..., X_n = x_n]$$
- Ein Schaetzwert $\hat{\theta}$ fuer den Parameter $\theta$ heisst Maximum Likelihood Schaetzwert, falls gilt:
$$L(\vec{x}, \theta) \leq L(\vec{x}, \hat{\theta}), \; \forall \theta$$
#### Konfidenzintervalle
- Um die Genauigkeit von Schaetzern zu quantisieren, wird nicht nur eine Schaetzvariable verwendet, sondern zwei Schaetzer $U_1$, $U_2$ gewaehlt, sodass gilt:
$$Pr[U_1 \leq \theta \leq U_2] = 1 - \alpha$$
- Hierdurch wird ausgesagt, dass mit einer Wahrscheinlichkeit von $\alpha$ der tatsaechliche Parameter $\theta$ ausserhalb des Intervalls $[U_1, U_2]$ liegt
- Der Term $1 - \alpha$ wird als Konfidenzniveau bezeichnet, $[U_1, U_2]$ als Konfidenzintervall
###### Berechnung
- Um das Konfidenzintervall fuer ein Stichprobenmittel $\overline{X}$ zu bestimmen, es zunaechst normiert werden: 
$$Z = \sqrt{n} \cdot \frac{\overline{X} - \mu}{\sigma}$$
- Bei einer standardnormalverteilten Zufallsvariable $Z$ kann das Konfidenzintervall bestimmt werden durch:
$$Pr[-c \leq Z \leq c] = 1 - \alpha$$
- Aufloesen nach $\overline{X}$ gibt:
$$Pr \left [\overline{X} - \frac{c \sigma}{\sqrt{n}} \leq \mu \leq \overline{X} + \frac{c \sigma}{\sqrt{n}} \right ] = 1 - \alpha$$
- Fuer $c$ gilt hierbei:
$$c = \Phi^{-1} \left(1 - \frac{\alpha}{2} \right )$$
## Testen von Hypothesen
- Das Testen von Hypothesen besteht darin zu ueberpruefen, ob eine Stichprobe die Bedingung einer Hypothese erfuellt
- Hierfuer wird eine Stichprobe in einer Testgroesse zusammengefasst
- Es werden Bereiche fuer die Testgroesse definiert, die entweder zur Ablehnung oder Akzeptanz der Hypothese fuehren
- Die zu ueberpruefende Hypothese wird in der Regel als Nullhypothese $H_0$ bezeichnet
#### Fehler
- Mit einer gewissen Wahrscheinlichkeit koennen durch Tests falsche Schluesse gezogen werden
- Bei einem Fehler 1. Art, wird $H_0$ abgelehnt, obwohl sie korrekt ist
- Bei einem Fehler 2. Art, wird $H_0$ akzeptiert, obwohl sie falsch ist
###### Fehlervermeidung
 - Das Reduzieren der Wahrscheinlichkeiten von Fehlern 1. und 2. Art sind gegenlaeufige Ziele, sie gegeneinander balanciert werden muessen
 - Die Wahrscheinlichkeit, dass es zu einem Fehler 1. Art kommt, wird durch das Signifikanzniveau $\alpha$ beschrieben 
#### Testkonstruktion
- Es sei $X$ eine bernoulliverteilte Zufallsvariable und die Hypothesen seien
$$H_0: p \geq p_0, \; H_1: p < p_0$$
- Die Testgroesse $T$ wird zudem festgelegt durch $T = X_1 + ... + X_n$ 
- Es wird ein Ablehnungsbereich $K = [0, k]$ definiert, sodass $H_0$ abgeleht werden kann, falls $T \in K$
- Das Signifikanzniveau kann nun bestimmt werden durch:
$$\alpha = Pr_{p = p_0}[T \leq k] \approx \Phi \left ( \frac{k - np_0}{\sqrt{np_0(1 - p_0)}}\right )$$
- Ist $\alpha$ gegeben, so kann das korrekte $k$ bestimmt werden durch:
$$k = z_{\alpha} \cdot \sqrt{np_0(1 - p_0)} + np_0$$
###### Guetefunktion
- Mithilfe einer Guetefunktion $g$ wird die Wahrscheinlichkeit angegeben, dass ein Test die Nullhypothese verwirft:
$$g(n, p) = Pr[T \leq k] \approx \Phi \left( \frac{k - np}{\sqrt{np(1 - p)}}\right)$$
#### Testkategorien
- Abhaengig von der zugrundeliegenden Verteilung der Zufallsvariablen und der verfuegbaren Menge an Informationen eignen sich unterschiedliche Tests 
###### Approximativer Binomialtest
- Sind $X_1, ..., X_n$ bernoulliverteilt mit Parameter $p$, so sei $\overline{X} = X_1 + ... + X_n$ die Haeufigkeit, mit der die Ereignisse $X_i = 1$ eingetreten sind
- Die normalverteilte Testgroesse wird in diesem Fall definiert durch:
$$Z = \frac{\overline{X} - np_0}{\sqrt{np_0(1-p_0)}}$$
- Hierdurch kann bestimmt werden, mit welcher Wahrscheinlichkeit $X$ mit dem geschaetzten Parameter $p_0$ im Ablehnungsbereich liegt
###### Gausstest
- Sind $X_1, ..., X_n$ normalverteilt mit den Parametern $\mu$ und $\sigma$, so sei $\overline{X} = \frac{1}{n} (X_1 + ... + X_n)$ der Durchschnitt einer Stichprobe 
- Die normalverteilte Testgroesse wird in diesem Fall definiert durch:
$$Z = \sqrt{n} \cdot \frac{\overline{X} - \mu_0}{\sigma}$$
- Hierdurch kann bestimmt werden, mit welcher Wahrscheinlichkeit $X$ mit dem geschaetzten Parameter $\mu_0$ im Ablehnungsbereich liegt
- Hierfuer muss jedoch die Standardabweichung von $X$ bekannt sein
###### t-Test
- Ein t-Test entspricht einem Gausstest, mit dem Unterschied, dass ein Schaetzer fuer die Standardabweichung, anstelle der Standardabweichung selbst verwendet wird 
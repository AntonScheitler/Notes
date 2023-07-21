## Allgemeines
- Es sei $A \in \mathbb{R}^{n \times n}$ symmetrisch
- $A$ ist definit, falls sie unterschiedliche Eigenschaften erfuellt
- Dies kann anhand der [[Eigenwerte und Eigenvektoren|Eigenwerte]] von $A$ ermittelt werden
#### Positiv Definit
- $A$ ist positiv definit, falls gilt:
$$\forall \space v \in \mathbb{R}^n \setminus \{0\}: v^TAv > 0$$
- Dies ist erfuellt, falls fuer die Eigenwerte $\lambda_i$ von $A$ gilt:
$$\lambda_i > 0$$
#### Negativ Definit
- $A$ ist negativ definit, falls gilt:
$$\forall \space v \in \mathbb{R}^n \setminus \{0\}: v^TAv < 0$$
- Dies ist erfuellt, falls fuer die Eigenwerte $\lambda_i$ von $A$ gilt:
$$\lambda_i < 0$$
#### Semi Positiv Definit
- $A$ ist semi positiv definit, falls gilt:
$$\forall \space v \in \mathbb{R}^n \setminus \{0\}: v^TAv \geq 0$$
- Dies ist erfuellt, falls fuer die Eigenwerte $\lambda_i$ von $A$ gilt:
$$\lambda_i \geq 0$$
#### Semi Negativ Definit
- $A$ ist semi negativ definit, falls gilt:
$$\forall \space v \in \mathbb{R}^n \setminus \{0\}: v^TAv \leq 0$$
- Dies ist erfuellt, falls fuer die Eigenwerte $\lambda_i$ von $A$ gilt:
$$\lambda_i \leq 0$$
#### Indefinit
- $A$ ist indefinit, falls gilt:
$$\exists \space v, w \in \mathbb{R}^n: v^TAv > 0, \space w^TAw < 0$$
- Dies ist erfuellt, falls fuer die Eigenwerte $\lambda_1, ..., \lambda_n$ von $A$ gilt:
$$\exists \space \lambda_i, \lambda_j \in \{\lambda_1, ..., \lambda_n\}: \lambda_i > 0, \space \lambda_j < 0$$
## Two-Player Zero-Sum Game
- In a two-player zero-sum game, there is a win player $S_1$ and a loss player $S_2$, which each choose a strategy $i$ and $j$, resulting in a payoff $a_{ij}$, which $S_2$ has to pay to $S_1$
- Therefore, $S_2$ chooses a strategy $j$ to in order to minimize $a_{ij}$, whereas $S_1$ pick a strategy $i$, in order to maximize $a_{ij}$
- Those strategies can take different forms
#### Acting with Caution
- If both players act with caution, $S_1$ will assume, that no matter what action it will take, $S_2$ will take the action, which would minimize the resulting payoff
- This can be expressed like so:
$$a_{\hat{i}j} = \max_i \min_j a_{ij}$$
- Similarly, $S_2$ will assume, that no matter what action it will take, $S_1$ will take the action, which would maximize the resulting payoff
- The payoff can then be described like this:
$$a_{i \hat{j}} = \min_j \max_i a_{ij}$$
###### Equilibrium
- An equilibrium is reached, if the following holds:
$$\max_i \min_j a_{ij} = a_{\hat{i}\hat{j}} = \min_j \max_i a_{ij}$$
#### Representation
- The possible payoffs are usually described by a matrix:
$$A = \begin{pmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22} \\
\end{pmatrix}$$
- The win player usually picks a row $i$ and the loss player a column $j$
## Elections
- In an election, there is a set of candidates $A$ and a number of voters, who each have a ballot consisting of rankings for the candidates $P_A$
- A ranking is a preference relation $\varrho$ which defines, which candidate is preferred over which
- It is the task of an election, to determine a final ranking, based on all ballots
#### Collective Choice Function
- A function which determines the result of an election is a collective choice function $K$
- In order for a system to be considered democratic, $K$ needs to fulfill several criteria
###### Rules
- $K$ must be defined for all possible ballots
- The result of $K$ must be again be a set of rankings of all candidates
- Any desired ranking can be achieved if all voters unanimously include the ranking in their ballots
- Ballots with an identical ranking with respect to two candidates $x$ and $y$ must yield the same collective ranking with respect to $x$ and $y$
- No voter can always decide the outcome of the election
###### Arrow's theorem
- Any system with more than two candidates and more than one voter cannot fulfill all democratic rules
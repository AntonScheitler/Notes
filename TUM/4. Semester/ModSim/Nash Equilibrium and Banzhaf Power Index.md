## Nash Equilibrium
- A Nash equilibrium is reached, if every player's strategy is optimal given the strategies of all other players
- As such, a player would have no interest in changing strategies, since it would only result in a worse result for themselves
## Banzhaf Power Index
- The Banzhaf power index is used to describe the influence of a party in a political system
- In this system, all parties have a weight $ and can either vote yes, or no
- A vote is passed, if the weights of the parties voting yes exceeds a specific quorum $q$
#### Computing the Index
- The Banzhaf power index of a party is the number of scenarios, in which it would sway the vote
- More specifically given a set of parties $\{S_1, ..., S_n\}$ with weights $w_1, ..., w_n$, the Banzhaf power index of $S_i$ is defined as
$$|T|, \; \; T \subseteq S \setminus \{S_i\}: \sum_{k \in T} w_k < q \leq \sum_{k \in T \cup \{S_i\}} w_k$$
###### Relative Index
- The relative Banzhaf power index of a party is it's absolute index, divided by the sum of power indices of all parties
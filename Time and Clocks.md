## Time Measurements in Computers
- Computers measure time based on a multiple of a periodically created microtick
- The granularity of a clock describes the size of the intervals between microticks
![[Pasted image 20241031162537.png]]
#### Measurement Errors
- Assuming there is a perfect clock $z$, and all other clocks are compared against it
- Given a clock $k$ with a granularity of $g^k$ which is equal to $10$ microticks of $z$, or $n^k$
- The drift of this clock is described by:
$$\text{drift}_i^k = \frac{z (\text{microtick}^k_{i + 1}) - z(\text{microtick}^k_i)}{n^k}$$
- The drift is thereforce the relation of the microticks performed by $k$ to the microticks it is supposed to perform
- From this, the drift rate $\rho$ can be computed:
$$\rho_i^k = | \text{drift}_i^k - 1|$$
- A perfect clock therefore has a drift rate of $0$
###### Example
![[Pasted image 20241031163456.png]]
![[Pasted image 20241031163504.png]]
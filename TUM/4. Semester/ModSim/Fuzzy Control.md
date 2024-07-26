## Control Systems
- In a system, one distinguishes environmental variables and control variables
- Environmental variables are measured and can be changed, by adjusting control variables
- In order to determine the optimal values for control variables, control systems can be used
#### Fuzzy Logic
- When building a control system with fuzzy logic, environmental variables are fuzzyly classified, in order to achieve a certain sense of what a control variable should look like
- This process includes multiple steps 
###### Fuzzification
- For every environmental variable, fuzzy sets need to be defined, which are often linguistic variables, such as "hot", "cold", "positive" or "negative"
- Since fuzzy sets aren't defined precisely, the membership of a variable in a fuzzy set isn't defined precisely either
- Instead, a membership function $\mu_A(x)$ describes, to what degree a variable $x$ is contained in a fuzzy set $A$
###### Rule Base
- In order to define the behavior of control variables in response to environmental ones, a series of if-then statements can be used
- This way, a control variable may be set to "increase temperature" if the measured temperature is in the fuzzy set "cold"
![[Pasted image 20240724182350.png]]
###### Inference
- Based on the degree, to which environmental variables are contained in fuzzy sets and the rules of the control system, the behavior of the control variables can be inferred
- If an the degree of membership of an environmental variable $\phi$ in a fuzzy set $A$ is $0.75$ and the degree of membership of $\dot{\phi}$ in $B$ is $0.4$, then the degree of membership of a control variable $u$ in $C$ is set to $\min(0.75, 0.4)$, if there is a rule such as $\text{IF } \phi = a \text{ AND } \dot{\phi} = B \text{ THEN } u = C$
![[Pasted image 20240611101639.png]]
###### Defuzzification
- After all degrees of membership of all control variables have been inferred and unified, the actual crisp control values need to be determined
- This can be achieved by calculating the centroid of the union of all fuzzy sets, the control variable is a part of
![[Pasted image 20240611102730.png]]
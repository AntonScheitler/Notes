## Design
- In a layered architecture, [[Modularity|modularity]] is achieved by deviding the system into layers
- Each layer depends only on its underlying layers and provides functionality to higher layers
#### Variants
###### Open layered architecture
- A layer can access functionality from all layers below
- This approach offers higher performance
###### Closed layered architecture
- A layer can only access functionality from the layer directly below
- This approach offers higher maintainability
## Best Practices
#### Layer Functionality
- Each layer should offer a higher level of abstraction and different functionality than the one before
![[Pasted image 20230531220231.png]]
#### Complexity Management
- Each layer should hide the complexity of its implementation
![[Pasted image 20230531220552.png]]
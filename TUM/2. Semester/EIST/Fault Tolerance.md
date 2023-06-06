## Reliability
- There are different methods of ensuring the reliability of a system
#### Write-ahead Logging
- Whenever there are changes in data, the changes are logged, before the data is updated
- In the event of a system failure, the logs can be replayed in order to restore the state of the application before the failure
- This approach however is vulnerable to permanent hardware failure
![[Pasted image 20230601095734.png]]
## Replicated Systems
- In order to ensure a system remains available, even in the event of a failure, it can be replicated
#### Replicated Stateless Systems
- In a stateless application, mutliple instsances can be deployed with a load balancer
- The instances can operate independent of each other
- If one instances failes, the service remains available due to the remaining running instances
![[Pasted image 20230601095705.png]]
#### Replicated Stateful Systems
- In a stateful application, state needs to be synchronized across multiple instances
- As such, each instance stores a copy of the entire state
- There are different approaches to handle changes in state
###### Primary-backup Replication
- A primary replica handles all client requests and updates its state accordingly
- All other instances copy the primary replica's state
- If the primary replica fails, another instance is selected to be the new primary replica
![[Pasted image 20230601100909.png]]
###### State Machine Replication
- TODO
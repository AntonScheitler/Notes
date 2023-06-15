- TODO
## Scaling Up
- Scaling up is the practice of using resources of a single processor as efficiently as possible
#### Parallelism and Threads
- A CPU consists of multiple cores
- Each of those cores can execute tasks idependently of each other
- Threads are units of execution, that need to be scheduled on a core
![[Pasted image 20230615090406.png]]
###### Scheduling
- Schedulers choose which thread to execute on a given core
- Different election algorithms choose threads sequentially or divide CPU time fairly
###### Thread Management
- Threads are organized in pools and need to be synchronized
- Synchronization can be achieved via locks, semaphores and barriers
![[Pasted image 20230615090500.png]]
#### Accelerated Computing Systems
###### GPU
- GPUs offer a large number of cores
- Using the SIMD pattern, single instructions can be executed on multiple cores in parallel
![[Pasted image 20230615094608.png]]
###### FPGA
- The behavior of an FPGA can be defined using hardware description languages
- FPGAs can thus execute specific programs very efficiently
## Scale Out
- Since the resources of a single machine are limited, multiple ones need to be used to maximze performance
- Those machines communicate using network protocols
#### Scalable Storage
- For stateful servers, databases need to be sharded and replicated
###### Replication
- All write requests are sent to a leader database, which saves copies of itself in follower databases
- Read requests are handled by the followers
###### Sharding
- Data is hashed and put into a shard according to its key
- This insures a uniform distribution of data in shards
- A seperate service keeps track of which piece of data is stored in which shard and routes the client
#### Scalable Computation
- Batch processing is achieved using a map-reduce framework
- A map function is applied to all shards, the results are sorted and reduced using a seperate function, before being returned
![[Pasted image 20230615101903.png]]
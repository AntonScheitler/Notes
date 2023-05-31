## General
- In a transaction process, work is divided into individual, indivisible steps
#### Properties
###### Atomicity
- All data operations are executed, as if they were one
- If a single data operation does not succeed, all of them are rolled back
###### Consistency
- Data before and after the execution of a transaction is consistent
###### Isolation
- Transaction are performed independent of one another
###### Durability
- Changes made by a transaction are persited, even in the case of a system failure
---
Title: DBS101 Flipped Class 10
categories: [DBS101, Flipped_Class]
tags: [DBS101]
---
### Topic: Transaction

### Learning outcomes
1. Explain database transactions.
2. Understand the transaction model.
3. Implement transactions in databases.
4. Understand ACID transactions.

### Transaction
`Transaction` refers to a collection of operations that form a single logical unit of work.
Transaction is started with the command `begin transaction` and ended with `end transaction`. All operations performed between these two statements are part of the transaction.

### Transaction Properties
What are the properties a transaction should possess?


### A Simple Transaction Model
Consider a transaction Ti that transfers $50 from account A to account B.

```
Initial values: A = $1000, B = $2000
Transaction Ti
Ti: read(A);
A := A - 50;
write(A); read(B);
B := B + 50;
write(B);
```

### Atomicity Example
Database system logs old values and restores them
on failure

### Ensuring Durability
- Write updates to disk before transaction completes.
- Log information to reconstruct updates after failure.

### Isolation Example
Execute transactions serially or use
concurrency control.

We did this transaction in postgresql.

### Storage Structure

It is categorized based on speed, capacity, and resilience:
**Volatile storage**: Access is fast, allows direct access to data items but it doesn't survive system crashes.
example- main memory and cache memory 

**Non-volatile storage**: Survives system crashes but it is slower and susceptible to failures leading to data loss.
example- magnetic disk, flash storage, optical media, magnetic tapes.

**Stable storage**: Information is never lost even in the event of hardware failures and power outages.

For a transaction to be durable and atomic,changes and log records must be written to stable storage.

- Committed transaction alters database into a new
consistent state, persisting despite system failures.
- Committed transactions cannot be undone by aborting;
compensating transactions may be necessary.

### A simple abstract transaction model:


- Active: Initial state, transaction executing.

- Partially committed: After final statement execution.

- Failed: Normal execution can't proceed.

- Aborted: Rolled back, database restored to pre-transaction state.


- Committed: Successfully completed.


### Transaction States and Handling Failures

- **Failed State**: A transaction enters the failed state when it can no longer proceed normally.
- **Aborted State**: A failed transaction must be rolled back and then enters the aborted state.

### System Options for Aborted Transactions

1. **Restart the Transaction**:
   - Restart only if the failure was due to a non-logical hardware or software error.
   - A restarted transaction is treated as a new transaction.

2. **Terminate the Transaction**:
   - Terminate if the failure was due to the transaction's internal logic error.

### Concurrency in Transaction-Processing Systems

- **Challenges**: Concurrent updates can complicate data consistency.
- **Serial Execution**: Easier but less efficient than concurrency.
- **Advantages of Concurrency**:
  1. Improved throughput and resource utilization.
  2. Reduced waiting time.

### Ensuring Consistency with Concurrency

- **Risk**: Concurrent transactions may violate the isolation property, risking database consistency.
- **Solution**: Use schedules to guarantee isolation and consistency.
- **Concurrency-Control Schemes**: Ensure correct concurrent execution by controlling interactions.

### Transaction Schedules and Serial Execution

### Example: Banking System Transactions

- **T1**: Transfers $50 from account A to B.
- **T2**: Transfers 10% of the balance from A to B.

### Serial Schedules

- **Schedule 1**: T1 → T2
- **Schedule 2**: T2 → T1

### Concurrent Execution and Schedules

- **Concurrent Execution**: Unpredictable interleaving of instructions.
- **Risk**: Can lead to inconsistent states without proper control.
- **Concurrency-Control**: Necessary to ensure correct and consistent execution.


### Importance
Serializability ensures the isolation property of transactions, resulting in a consistent state even with concurrent execution.

### Conflicting Instructions
Two instructions conflict if they belong to different transactions, access the same data item, and at least one is a write operation.

### Conflict Equivalence
Two schedules are conflict equivalent if non-conflicting instructions can be swapped to obtain one from the other.

### Conflict Serializability
A schedule is conflict serializable if it is conflict equivalent to some serial schedule.

### Precedence Graph
- A directed graph used to test conflict serializability.
- Nodes represent transactions, and edges indicate conflicts.

### Checking Serializability
1. Construct the precedence graph.
2. Use a cycle-detection algorithm.
3. If there's a cycle, the schedule is not conflict serializable; otherwise, it is.

### Recoverable Schedules
For each pair of transactions where one reads data written by the other, the commit operation of the writer must appear before that of the reader.

### Cascadeless Schedules
Transactions reading data written by others must rollback if the writing transaction fails.

### Transaction Isolation Levels
- Serializable: Ensures serializable execution.
- Repeatable Read: Only committed data can be read, but not necessarily serializable.
- Read Committed: Only committed data can be read, allowing non-repeatable reads.
- Read Uncommitted: Allows reading uncommitted data.

### Implementing Isolation Levels
Methods include locking, timestamps, and maintaining multiple versions of data items.

### Snapshot Isolation
Allows transactions to see a consistent snapshot of the database, even if other transactions are modifying data.

### Ensuring Serializability
Different database systems offer mechanisms like Serializable Snapshot Isolation (PostgreSQL 9.1+), Serializable isolation level (Oracle, SQL Server), etc.

### Conclusion

In conclusion, transactions play a crucial role in maintaining the integrity and consistency of databases. They encapsulate a set of operations into a single logical unit of work, ensuring properties like atomicity, consistency, isolation, and durability (ACID). Through proper management of transaction states and handling of failures, databases can maintain data integrity even in the face of concurrent execution and system failures. Various techniques such as concurrency control, conflict resolution, and isolation levels are employed to ensure serializability and prevent data anomalies. Implementing these practices ensures that database systems operate reliably and consistently, meeting the needs of modern applications and users.
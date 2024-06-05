---
Title: DBS101 Flipped Class 12
categories: [DBS101, Flipped_Class]
tags: [DBS101]
---

### Topic: Recovery System

### Learning outcomes
1. Understand recovery mechanisms.
2. Analyse database recovery algorithms.
3. Explain the importance of database logging in recovery.

### Why are recovery systems are crucial in Database Management Systems (DBMS):

**Data protection**:  Even with the best precautions, unexpected events like hardware failures, software bugs, power outages, or human errors can occur. Recovery systems provide a way to restore lost or corrupted data, minimizing the impact of these events.

**Data integrity**: Transactions in a DBMS are expected to follow the ACID properties (Atomicity, Consistency, Isolation, Durability). Recovery mechanisms ensure that even if a system crashes during a transaction, the database remains in a consistent state. In simpler terms, they prevent the database from being left in a partially updated or corrupt state.

**Compliance**: Many organizations are subject to regulations that mandate data retention for specific periods. Recovery systems ensure data remains available to meet these compliance requirements even in case of accidental deletion or loss.

**Minimized downtime**:  System failures are inevitable, but recovery systems help get the DBMS back online quickly. This reduces downtime and ensures applications that rely on the database can resume operation as soon as possible.

- Transactions must be atomic and we ensure that by the technique called Log Based Recovery.

### Log records

Log records are essentially entries within a log file, which is a computer-generated record of events, activities, and usage patterns. These files are created by various software applications, operating systems, and devices to provide a historical record of what's happening within the system.

**Details of events**: Log records capture what happened, when it happened, and why (where possible) within a system.

**Troubleshooting**: They help pinpoint issues by providing a history of activity.

**Security & Performance**: They are crucial for monitoring security and system performance.

### Database Modification 

### Transaction Types:
- Deferred Modification: Changes are written to the database only after commit (safer but slower).
- Immediate Modification: Changes are written during the transaction (faster but requires recovery logic).

### Recovery Algorithm Considerations:
- Uncommitted changes in memory: Need to handle situations where a crash happens before changes are written to disk.
- Active transaction modifications: Need to undo or redo changes based on transaction state at crash.

### Database Log:
- Created before modifications for "undo/redo" operations.
- Stores both old and new values for data items.

### Recovery Operations:
- Undo (Rollback): Reverts changes made by a transaction using log records.
- Redo: Applies the intended changes of a transaction based on log records.

### System Crashes and Recovery:
- Log Analysis: Identifies transactions needing undo/redo based on log entries.
- Checkpoints: Periodic snapshots to reduce the log data scanned during recovery.
- Fuzzy Checkpoints: Allow ongoing transactions during checkpointing (more complex).

### Log Management:
- Write-Ahead Logging (WAL): Ensures changes are logged before actual updates.
- Log Buffering: Improves efficiency by temporarily storing log records in memory.
- Database Buffering: Deals with writing modified data blocks to disk.

### High Availability Techniques:
- Remote Backups: Maintain a replica database for disaster recovery.
- Distributed Databases: Replicate data across multiple sites for higher availability.

### Recovery Algorithms (ARIES):
Three Phases: Analysis, Redo (replaying history), and Undo (rollback).

- ARIES employs a three-phase approach to ensure data consistency after a system crash:

1. Analysis Pass:

- Identifies incomplete transactions needing an undo (rollback) based on log entries.
- Locates "dirty pages" (modified data in memory not yet written to disk).
- Determines the exact point in the log (LSN - Log Sequence Number) from where the redo pass should begin.

2. Redo Pass:
- Starts from the LSN identified in the analysis pass.
Replays the logged actions, essentially redoing the history of committed transactions.
- Brings the database to a consistent state it was in before the crash.

3. Undo Pass:
- Focuses on incomplete transactions at the time of the crash.
- Uses undo log records to revert any changes made by these transactions.
- Ensures the database reflects only the actions of successfully committed transactions.

### Key Concepts in ARIES

- Write-Ahead Logging (WAL): A fundamental principle in ARIES. It guarantees that all database modifications are written to the transaction log on stable storage (like disk) before the actual changes are applied to the database itself. This ensures recoverability even if a crash occurs during the modification process.

- Logging Changes During Undo: When an undo operation is performed, ARIES logs this action as well. This ensures that if another crash happens before the database fully recovers, the undo operation won't be repeated unnecessarily.

- Repeating History During Redo: During the redo pass, ARIES meticulously replays the logged actions, essentially reconstructing the exact state of the database before the crash. This ensures data consistency and adherence to the ACID properties (Atomicity, Consistency, Isolation, Durability).

### Benefits of ARIES recovery algorithm

- Flexibility: ARIES can be adapted to work with various concurrency control protocols.
- Efficiency: Checkpointing minimizes the amount of log data that needs to be analyzed during recovery, speeding up the process.
- Durability: Write-Ahead Logging ensures data changes are persisted before updates, guaranteeing data integrity even in case of crashes.

### Recovery in Main-Memory Databases:
- Optimized Recovery: Can skip redo logging for indexes and reduce undo logging overhead.
- Fast Restart: Crucial due to loading the entire database into memory during recovery.
- Parallel Recovery: Utilizes multiple CPU cores to speed up recovery.

### Dblogging
Dblogging refers to the process of writing detailed logs within a database system.

- Why is Dblogging Important?

1. Troubleshooting: If something goes wrong, dblogs provide a historical record to pinpoint the cause of the problem.
2. Security: They track user activity, helping to identify suspicious attempts to access or modify data.
3. Performance Monitoring: Dblogs reveal bottlenecks or areas for improvement within the system. 

- Benefits of Dblogging
1. Data Integrity: Ensures data remains consistent and accurate.
2. Compliance: Helps meet regulations that require data retention for specific periods.
3. Faster Recovery: Dblogs can streamline the process of restoring the database in case of a system crash.

### Recovery algorithm(Shadow Paging)

Shadow Paging is a recovery algorithm that focuses on maintaining a "shadow copy" of the database to ensure data consistency after a system crash.

### How it works:

**1. Normal Operation:**

- Transactions modify data in a designated "active" page.
- Any changes are not immediately written to the original database page on disk.
- Instead, a copy of the original page is created and stored as the "shadow page."
- The transaction's modifications are applied to the active page in memory.

**2. Transaction Commit**:

- If a transaction commits successfully, the active page with the changes becomes the new official page.
- The original, unmodified shadow page is discarded.

**3. Transaction Abort**:

- If a transaction needs to be rolled back (aborted), the unmodified shadow page is simply restored as the official page.
- The changes in the active page are discarded.

**4. System Crash**:
- In case of a crash, the system can determine which transactions were committed based on transaction logs.
- For committed transactions, the active page (with the changes) becomes the official page.
- For uncommitted transactions, the original shadow pages are restored, effectively rolling back any uncommitted changes.

### Benefits of Shadow Paging:

- Fast Commits: Transactions commit quickly because changes are written to memory first, not disk.
- Simplified Rollback: Uncommitted transactions can be easily rolled back by restoring the shadow page.
- Reduced Disk Writes: Less frequent writes to the original database page improve performance.

Shadow Paging offers a trade-off between performance and resource consumption. It prioritizes faster commits and simplifies rollbacks at the expense of increased memory usage.


### Conclusion

Today's flipped class dove deep into  database recovery systems. It hit me just how important they are in safeguarding data ensuring our data stays safe and consistent even if the system crashes. We learned about recovery algorithms like ARIES, which analyze logs to undo or redo transactions, and  I wrote one more algorithm `Shadow Paging`, which utilizes shadow copies to streamline the process. Dblogging, the detailed logging within the database itself, provides a historical record for troubleshooting and monitoring. Overall, these recovery mechanisms guarantee data integrity, minimize downtime, and make databases truly reliable.
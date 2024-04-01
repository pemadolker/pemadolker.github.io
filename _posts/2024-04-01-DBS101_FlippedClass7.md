---
Title: DBS101 Flipped Class 7
categories: [DBS101, Flipped_Class7]
tags: [DBS101]
---

### Topic: Storage and buffer management

### Let's get started
For today's flipped class, we didnt do any group work instead we did practical work in the class and wrote a report on it. We were supposed to submit the report on vle within 2 hour and was graded shortly after the submission. In this practical, like any other practical it contained a guided session and one exercise. For the guided session, we just need to follow the procedures and for exercise, we were asked to read relevant materials and outline the important procedures to be followed when building a relational database from scractch and list data structures to be used and explain the importance of each outlined procedure.

### Guided Session 
Task 1: Disk Block Implementation

the outcome of the task looked like this:

![alt text](<../img/DBS/Screenshot from 2024-04-01 14-24-11.png>)

Task 2: RAID configurations

the outcome :

![alt text](<../img/DBS/Screenshot from 2024-04-01 14-26-42.png>)

Task 3: Buffer pool management

the outcome looked like this:

![alt text](<../img/DBS/Screenshot from 2024-04-01 14-29-29.png>)

### Exercise
Building a simple relational database from scractch.

important procedures to be followed when building a relational database from scractch:

1. Designing the data structures:

- File Format: Define the structure of the database file like how data will be stored, organized and accessed. Data integrity, data potability and compatibility with other systems all depends on how well-defined a file format is. 

- B-trees for tables and indexes:  B-trees are balanced tree structures commonly used in databases for efficient searching, insertion, and deletion operations. They are appropriate for disk-based storage systems and ensure fast access to data.

2. Implementing Database Machine:

- Registers and Instructions: Design a virtual machine tailored for database operations, including low-level instructions for data manipulation, query execution, and control flow.

- Cursors: Use cursor methods to efficiently navigate across B-trees and other data structures. Cursors facilitate tasks such as scanning, searching, and updating records and allow sequential access to data.

3. Developing SQL Compiler:

- Parsing SQL Queries: Build a parser that will examine, comprehend, and convert SQL statements into instructions that the database machine can execute. Accurate query interpretation and validation are ensured via a strong parser.

- Generating Query Plans: Create efficient query plans from parsed SQL queries by taking the available indexes, data distribution, and query complexity into account. Query optimization improves resource usage and query performance.

4. Building APIs and Shell:

- API for Database Operations: Provide an interface that allows users to communicate with the database system. This interface should have features for opening, closing, querying, and editing databases. The creation of applications and their integration with other software components are made easier by a well-designed API.

- Command-Line Shell:Provide an intuitive user interface so that users can test queries, explore database features, and execute SQL commands interactively. Database management, debugging, and experimenting are made easier with a shell.

5. Testing and Optimization:

- Unit Testing: To verify the accuracy and resilience of database components, such as data structures, query execution, and error handling, create thorough test suites.

- Performance Tuning: To improve the throughput, scalability, and efficiency of the system, profile and optimize database processes. Resource management, query rewriting, and index selection are examples of optimization strategies.

### Conclusion 
I have gained knowledge on storage and buffer management through tasks such as handling allocations, reads, writes, and deallocations, investigating RAID configurations, and understanding buffer pool administration in a database system. These tasks provided practical knowledge for effective storage and buffer management, ensuring data integrity, performance, and efficiency in various computing environments.

### Experience
It is the first time we did flipped class on practical work. It wasnt bad but I enjoyed moreworking and learning as a group. 
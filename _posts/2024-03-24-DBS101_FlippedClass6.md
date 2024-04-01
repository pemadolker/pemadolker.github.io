---
Title: DBS101 Flipped Class 6
categories: [DBS101, Flipped_Class6]
tags: [DBS101]
---

### Topic: Nonrelational Databases

### Let's get started

For this flipped class, we had two groups: the expert group and the home group. As for the expert group, students were divided into group of 4 students forming 6 groups and divided into groups of 6 for the home group. The 6 expert groups were supposed to explore the type of non-relational databases, understand the advantages, disadvantages and applications of the type of non-relational databases given to the group and be able to explain it to their home group. The flipped class session was an hour long where students were given 20 minutes for group discussion, 25 minutes to present what they have discuused with the expert group to the home group and 15 minutes for the Q&A session.


### Expected Outcomes
1. Explore different types of non-relational databases.
2. Understand the advantages and disadvantages of different types of non-relational databases.

### What is NoSQL ?
It is a non-relational database that is used to store the data in the non-tabular form. 
NoSQL stands for Not only SQL.

### Types of NoSQL Databases

#### Document-based databases

A document-based database is a type of database that uses document to store data, which are usually in formats like JSON,BSON,or XML rather than storing data in tabular form like relational databases.

- Advantage:
1. Schema flexibility: Documents can have varying structures without a predefined schema.
2. Horizontal scalability: Easily distribute data across multiple servers for high scalability.
3. Improved performance: Faster read/write operations, especially for complex data.
4. Native support for hierarchical data: Simplifies storage of nested data structures.
5. Developer-friendly APIs: Intuitive APIs for seamless integration with applications.

- Disadvantage:
1. Lack of ACID transactions: Sacrifices strict transactional guarantees for performance.
2. Limited support for complex queries: May struggle with complex queries involving multiple documents.
3. Potential for data duplication: Denormalization can lead to redundancy and inconsistency.
4. Learning curve: Requires adaptation for developers accustomed to relational databases.

- Application:

  These databases are designed to handle semi-structured or unstructured data, making them well-suited for various applications, including content management systems, blogging platforms, e-commerce websites, and more.

#### Key-Value based databases or key-value store

It is the simplest form of NoSQL database where data is stored as pairs of keys and values. Each element within the database is uniquely identified by its key, allowing retrieval of data by specifying the corresponding key and values can range from simple data types like strings and numbers to more complex objects.

- Advantage

1. Simplicity: Easy data management with only key and value columns.
2. Scalability: Seamless expansion to handle increasing data and workload.
3. Speed: Fast read and write operations due to efficient indexing.

- Disadvantage

1. Limited Query Capabilities: Difficulty in complex data analysis and retrieval.
2. Data Structure Constraints: Not ideal for complex data relationships.
3. Data Consistency: Challenges in maintaining consistency, especially in distributed setups.

- Application

1. Caching Systems: Improve application performance by storing frequently accessed data.
2. Session Management: Efficiently handle user session data for web applications.
3. Distributed Systems: Serve as a foundational storage layer for distributed setups.
4. Content Delivery Networks (CDNs): Store and retrieve cached content across edge servers.
5. Real-time Analytics: Support real-time data processing and analysis for insights generation.

#### Column oriented Databases

A columnar database is a type of database management system (DBMS) that stores data in columns rather than rows, optimizing performance for analytical queries. In a columnar database, each column is stored separately on disk, allowing for efficient retrieval and processing of specific columns relevant to a query. 

- Advantage:
1. Optimized for Analytics: Columnar storage facilitates efficient analytical queries, especially when dealing with a large number of columns.
2. Compression: Data is often compressed within each column, reducing storage requirements and improving query performance.
3. Scalability: Column-oriented databases can scale horizontally to handle large datasets and high query loads by distributing data across multiple nodes.
4. Aggregation Performance: Well-suited for operations like aggregations, filtering, and complex analytical queries due to the structure of columnar data storage.
5. Data Retrieval Efficiency: Read operations are faster, especially when accessing only specific columns, reducing disk I/O and improving overall performance.

- Disadvantage:
1. Suboptimal for transactional data: Less efficient for transactional operations with frequent updates.
2. Complexity: Requires specialized knowledge for optimization and management.
3. Higher costs: May involve higher upfront costs compared to traditional relational databases.

- Applications:
1. Data warehousing: Storing and analyzing vast amounts of historical data.
2. Business intelligence: Powering analytics and reporting for data-driven decision-making.
3. OLAP systems: Supporting multidimensional analysis for complex queries.
4. Log analytics: Efficiently analyzing large volumes of timestamped data.
5. Time series data analysis: Handling time-based data for monitoring and performance analysis.

#### Graph Databases

Graph databases are a type of NoSQL database that uses graph structures with nodes, edges, and properties to represent and store data. The connections between the nodes are called links or relationships.

- Advantage:
1. Flexible data modeling with a graph structure.
2. Optimized query performance for highly connected data.
3. Scalability to handle large and growing datasets.
4. Rich query language optimized for graph operations.

- Disadvantage:
1. Complexity of queries not aligned with graph traversal.
2. Scalability challenges with dense graphs.
3. Learning curve associated with graph data modeling.

- Application:
1. Social networks for modeling user relationships.
2. Recommendation engines for personalized suggestions.
3. Network and IT operations management.
4. Fraud detection for identifying suspicious patterns.
5. Knowledge graphs for semantic search and question answering.

#### Vector Databases
Vector databases, also known as vector stores or vector databases, are a specialized type of NoSQL database designed to efficiently store, query, and manipulate high-dimensional vectors. In the context of databases, a vector refers to a mathematical representation of data points in a multi-dimensional space. 

- Advantage:

1. Efficient storage and retrieval of high-dimensional vectors.
2. Fast similarity search and nearest neighbor queries.
3. Support for vector-specific operations and indexing.
4. Scalability to handle large volumes of vector data.
5. Well-suited for machine learning and recommendation systems.

- Disadvantage:

1. Limited support for non-vector data types and complex queries.
2. Higher complexity in data modeling and indexing for high-dimensional spaces.
3. Learning curve associated with vector-specific query languages and operations.

- Application:
1. Anomaly detection and pattern recognition in cybersecurity and fraud detection systems.
2. Machine learning, recommendation systems, and similarity search.

#### Time-series Databases

Time series databases are specialized databases optimized for storing, querying, and analyzing time-stamped data points. They are designed to efficiently handle large volumes of sequential data points collected at regular intervals over time.

- Advantage:
1. Efficient retrieval of time-stamped data points.
2. Scalable to handle high write throughput and large data volumes.
3. Specialized data structures and indexing for fast time-based queries.
4. Built-in data compression for storage efficiency.

- Disadvantage:
1. Limited support for complex non-time-based queries.
2. Risk of data loss with improper retention policies.
3. Learning curve for specific query languages and data modeling.

- Application:
1. IoT and sensor data monitoring.
2. Financial markets and trading analysis.
3. Infrastructure monitoring and DevOps.
4. Energy and utilities for grid monitoring.
5. Healthcare and life sciences for patient monitoring.

### Experience
I would rate this flipped class 4 on 5. I also played a part in explaining my topic to the home group and my home group friends also did a very good job in explaining it to us.

# CAP Theorem

- The **CAP theorem** (also known as Brewer’s theorem) states that in a distributed data system, you can only **guarantee two out of the following three**:
- `Consistency`: Every read receives the most recent write or an error.
- `Availability`: Every request receives a (non-error) response, without the guarantee that it contains the most recent write.
- `Partition Tolerance`: The system continues to operate despite arbitrary partitioning due to network failures.

# Relational

- Tabular format data
- Reliable in terms of data integrity
- Complaint with ACID
- Transaction levels
- Structured data / Normalization
- Less compliant with horizontal scaling
- Built from ground up for data integrity
- It is generally on a single server
	- Due to ACID compliance 
	- Complex operations like JOIN 
	- Query optimization
- Slower read write compared to NoSql 
	- Due to accessing multiple tables for common operations
	- Index management
	- And acid checks / locks
- Examples : 
	- MySql 
	- PostGreSql 
	- Oracle 
	- Sqlite 
	- Microsoft SQL 
	- IBM Db 2
- CAP : CA
	- Not P because , not supported horizontal scaling so if anything breaks , server crashes
- USECASES :
	- When we have stable and predefined data model
	- We prefer data integrity
	- Financial/Banking systems
- ### 🐘 **PostgreSQL**
	Use when: You need power, flexibility, and standards compliance.
- ### 🐬 **MySQL**
	Use when: You want speed, simplicity, and broad support.
- ### 📦 **SQLite**
	Use when: You need an embedded, lightweight database.
- ### 🏛️ **Oracle**
	Use when: You need enterprise-grade features, support, and security.


# NoSQL

- Non-tabular, flexible data models  
    (e.g., document, key-value, wide-column, graph)
- High scalability & performance
- Does **not strictly follow ACID** — often **eventual consistency**
- Designed for horizontal scaling
- Schema-less or loosely structured data
- Better for handling **unstructured or semi-structured** data
- Built for high-availability, speed, and distributed data
- Easily deployed across multiple server
    - Built-in sharding & replication
    - Distributed systems first
    - Handles high-volume real-time data
- Faster read/write in many scenario
    - No JOINs (denormalized data)
    - No strict schema enforcement
    - No locking overhead like ACID
- Examples
    - MongoDB (Document-based)
    - Cassandra (Wide-column)
    - Redis (Key-value, in-memory)
    - DynamoDB (Key-value, document)
    - Couchbase
    - Neo4j (Graph-based)
- CAP: **Usually CP or AP**
    - Prioritize **Partition Tolerance** and either **Availability** or **Consistency**
    - Example:
        - MongoDB → CP (Consistent + Partition tolerant)
        - Cassandra → AP (Available + Partition tolerant)
- USECASES:
    - When you have **large, changing, or semi-structured data**
    - Need to **scale across servers**
    - Use cases with **massive throughput requirements**
    - Real-time analytics, IoT, big data, content management
    - Flexible and evolving data models (e.g., product catalogs, social apps)
---
### 🍃 **MongoDB**
Use when: You need flexibility, JSON-like documents, and scalability.
### 🧱 **Cassandra**
Use when: You need massive write throughput and high availability across regions.
### ⚡ **Redis**
Use when: You need ultra-fast in-memory data (caching, session storage).
### ☁️ **DynamoDB**
Use when: You want a fully managed, serverless, key-value & document store on AWS.
### 🧠 **Neo4j**
Use when: Your data is highly connected and you need graph traversal (e.g., social networks, recommendation engines).
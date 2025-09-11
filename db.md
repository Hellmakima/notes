# Database

---

### **ACID Properties in Databases**

#### Definitions:
1. **Atomicity**:
   - **Definition**: Ensures that a transaction is all-or-nothing; it either completes fully or not at all.
   - **Example**: Transferring money between two accounts. If the debit from one account fails, the credit to the other must also fail.

2. **Consistency**:
   - **Definition**: Ensures that a database remains in a valid state before and after a transaction.
   - **Example**: A transaction debiting one account and crediting another should maintain the total balance in the system.

3. **Isolation**:
   - **Definition**: Ensures that transactions execute independently without interference.
   - **Example**: Two users simultaneously booking movie tickets should not overwrite each other’s selections.

4. **Durability**:
   - **Definition**: Ensures that once a transaction is committed, its changes are permanent, even in case of a system crash.
   - **Example**: After a payment is successfully processed, the record persists even if the server crashes immediately after.

---

### **RDBMS vs. NoSQL**

#### Definitions:
- **RDBMS (Relational Database Management System)**:
  Uses structured tables with predefined schemas and supports SQL.
- **NoSQL**:
  Non-relational databases designed for flexible schema and high scalability, often used for unstructured or semi-structured data.

#### Advantages:
- **RDBMS**:
  1. Strong ACID compliance.
  2. Ideal for complex queries and transactional systems.
  3. Mature ecosystem with well-established tools.
- **NoSQL**:
  1. Flexible schemas for changing data models.
  2. Horizontally scalable for large datasets.
  3. Better suited for big data and real-time analytics.

#### Disadvantages:
- **RDBMS**:
  1. Not as scalable horizontally.
  2. Schema changes can be challenging.
  3. May not perform well with very large datasets.
- **NoSQL**:
  1. Limited ACID compliance (eventual consistency).
  2. Complex queries can be harder to implement.
  3. Tooling and community support can be fragmented.

---

### **Normalization**

#### Definitions:
1. **First Normal Form (1NF)**:
   - Eliminates duplicate rows, ensures each column contains atomic values, and each row is unique.
   - **Example**: A table storing multiple phone numbers in a single column is not in 1NF.

2. **Second Normal Form (2NF)**:
   - Achieved when the table is in 1NF and all non-key attributes are fully dependent on the primary key.
   - **Example**: A student table storing course IDs that aren't dependent on the student ID violates 2NF.

3. **Third Normal Form (3NF)**:
   - Ensures no transitive dependencies; all attributes are only dependent on the primary key.
   - **Example**: A table where a non-key column like "City" depends on another column like "ZIP Code" violates 3NF.

4. **Boyce-Codd Normal Form (BCNF)**:
   - A stricter version of 3NF, ensuring no non-trivial functional dependencies exist on a superkey.
   - **Example**: A table with overlapping candidate keys may require decomposition into BCNF.

---

### **DDL, DML, and DCL**

#### Definitions and Examples:
1. **Data Definition Language (DDL)**:
   - Used to define database schema.
   - **Example**: 
     ```sql
     CREATE TABLE Employees (ID INT, Name VARCHAR(50));
     ALTER TABLE Employees ADD Salary FLOAT;
     ```

2. **Data Manipulation Language (DML)**:
   - Used for data retrieval and manipulation.
   - **Example**:
     ```sql
     INSERT INTO Employees (ID, Name) VALUES (1, 'Alice');
     SELECT * FROM Employees;
     ```

3. **Data Control Language (DCL)**:
   - Used to control access to data.
   - **Example**:
     ```sql
     GRANT SELECT ON Employees TO User1;
     REVOKE SELECT ON Employees FROM User1;
     ```

---

### **Clauses Overview**

- **WHERE**: Filters rows based on a condition.
- **GROUP BY**: Groups rows sharing a value for aggregation.
- **HAVING**: Filters grouped data.
- **ORDER BY**: Sorts result sets by specified columns.
- **LIMIT**: Restricts the number of rows returned.
- **JOIN**: Combines rows from two or more tables.

---

### **Transactions and Concurrency Control**

#### Definitions:
- **Transactions**: Units of work in a database that are treated as a single operation.
- **Concurrency Control**: Mechanisms to ensure correct transaction execution in multi-user environments.

#### Techniques:
1. **Locks**: Prevent concurrent transactions from conflicting.
2. **Optimistic Concurrency**: Validates changes only during commit.
3. **Pessimistic Concurrency**: Blocks other transactions from accessing data during updates.

---

### **2-Phase Commit Protocol**

#### Definition:
- A distributed algorithm to ensure atomicity across multiple systems.

#### Phases:
1. **Prepare Phase**:
   - Coordinators ask participants to prepare for commit.
2. **Commit Phase**:
   - If all participants agree, the coordinator commits. Otherwise, it rolls back.

---

### **Serializability**

#### Definition:
- The highest level of isolation ensuring that concurrent transactions produce the same result as serial execution.

#### Techniques:
- **Conflict Serializability**: Transactions reorder without conflicts.
- **View Serializability**: Transactions reorder but maintain read/write patterns.

---

### **Performance and Optimization Techniques**

1. **Indexing**:
   - Speeds up data retrieval by creating efficient search paths.
2. **Query Optimization**:
   - Techniques like join ordering and subquery rewriting.
3. **Partitioning**:
   - Dividing tables for better performance and manageability.
4. **Caching**:
   - Storing frequently accessed data in memory.

---

### **Types of NoSQL Database**

1. **Row-Column**:
   - Example: MySQL, PostgreSQL.
   - Data is stored row by row; great for transactional systems.
2. **Document**:
   - Example: MongoDB.
   - Stores JSON-like documents, ideal for hierarchical data.
3. **Key-Value**:
   - Example: Redis.
   - Maps unique keys to values, ideal for caching.
4. **Node-Based**:
   - Example: Neo4j.
   - Optimized for graph-based data and relationships.

---

### **Advanced Topics**

1. **Cursor**:
   - Definition: A pointer used to iterate over rows in a query result.
   - Example:
     ```sql
     DECLARE cursor_name CURSOR FOR SELECT * FROM Employees;
     ```

2. **Procedure**:
   - Definition: Stored routines for reusable logic in databases.
   - Example:
     ```sql
     CREATE PROCEDURE GetEmployeeCount() AS BEGIN SELECT COUNT(*) FROM Employees; END;
     ```

3. **Trigger**:
   - Definition: Automatically executed code in response to events.
   - Example:
     ```sql
     CREATE TRIGGER UpdateSalary AFTER UPDATE ON Employees FOR EACH ROW BEGIN UPDATE Salaries SET Updated = NOW(); END;
     ```

4. **Sequence**:
   - Definition: Generates unique numbers.
   - Example:
     ```sql
     CREATE SEQUENCE EmpIDSeq START WITH 1 INCREMENT BY 1;
     SELECT NEXTVAL(EmpIDSeq);
     ```
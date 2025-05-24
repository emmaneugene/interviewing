**ACID (atomicity, consistency, isolation, durability)** is a set properties are a set of principles that guarantee reliable processing of database transactions. They are fundamental to most traditional relational database management systems (RDBMS) like MySQL, PostgreSQL, Oracle, SQL Server, etc., ensuring data integrity even in the face of errors, system crashes, or concurrent access.

### Atomicity

*   **Concept:** "All or nothing." An atomic transaction is an indivisible unit of work. It either completes entirely (commits) or doesn't execute at all (rolls back). There's no in-between state.
*   **Analogy:** Transferring money from account A to account B. This transaction involves two steps:
    1.  Debit account A by $X.
    2.  Credit account B by $X.
    If the first step completes but the second fails (e.g., due to a system crash), atomicity ensures that the entire transaction is rolled back. Account A will not be debited, and account B will not be credited. The money is never lost or duplicated.
*   **Guarantees:** Prevents partial updates and ensures that the database remains in a consistent state if an operation fails midway.

### Consistency

*   **Concept:** A transaction brings the database from one valid state to another valid state. It must obey all predefined rules, constraints, and triggers.
*   **Analogy:** In a banking system, a rule might be "an account balance cannot be negative." If a transaction attempts to withdraw more money than available, consistency ensures that the transaction is rejected or rolled back, preventing the database from entering an invalid state (e.g., an account balance going below zero). Other examples include unique primary keys, referential integrity (foreign keys), and data types.
*   **Guarantees:** Data validity and adherence to business rules. It prevents corruption of the database based on defined schema and constraints.

### Isolation

*   **Concept:** Concurrent transactions appear to execute serially, meaning they don't interfere with each other. Even if multiple transactions are running simultaneously, each transaction's intermediate changes are not visible to other transactions until it is committed.
*   **Analogy:** Imagine multiple people at different ATMs trying to withdraw money from the same account. Without isolation, one person might see a partially updated balance from another person's ongoing withdrawal, leading to incorrect decisions. Isolation ensures that each person sees the account balance as if they were the only one accessing it at that moment.
*   **Guarantees:** Prevents common concurrency issues like:
    *   **Dirty Reads:** Reading uncommitted data from another transaction.
    *   **Non-repeatable Reads:** Reading the same data twice within a transaction and getting different values because another committed transaction modified it in between.
    *   **Phantom Reads:** A query retrieving a set of rows, then the same query later retrieving different rows (more or fewer) because another transaction inserted or deleted rows.
### Durability

*   **Concept:** Once a transaction has been committed, its changes are permanent and will survive any subsequent system failures (e.g., power outages, crashes, hardware malfunctions).
*   **Analogy:** When you save a document to your computer's hard drive and then shut down the computer, you expect the document to still be there when you power it back on. Similarly, once a bank transfer is confirmed, you expect the changes to your account balance to persist, even if the bank's server immediately crashes.
*   **Guarantees:** Persistence of committed data. This is typically achieved by writing transaction data to non-volatile storage (like hard drives or SSDs) and using transaction logs (or write-ahead logs) that can be replayed during recovery to restore the database to its last consistent state.

While traditional relational databases strongly adhere to ACID properties, some modern NoSQL databases (especially those prioritizing high availability and partition tolerance over strict consistency) might relax some of these properties, often favoring a model like **BASE** (Basically Available, Soft state, Eventually consistent) for greater scalability and performance in distributed environments.

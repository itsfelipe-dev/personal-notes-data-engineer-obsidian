### OLTP

OLTP (online transactional processing) enables the rapid, accurate data processing behind ATMs and online banking, cash registers and ecommerce, and scores of other services we interact with each day.

A database transaction is a change, insertion, deletion, or query of data in a database. OLTP systems (and the database transactions they enable) drive many of the financial transactions we make every day, including online banking and ATM transactions, e-commerce and in-store purchases, and hotel and airline bookings, to name a very few. In each of these cases, the database transaction also remains as a record of the corresponding financial transaction


## Characteristics of OLTP systems

In general, OLTP systems do the following:

-   **Process a large number of relatively simple transactions:** Usually insertions, updates, and deletions to data, as well as simple data queries (for example, a balance check at an ATM).
-   **Enable multi-user access to the same data, while ensuring data integrity:** OLTP systems rely on concurrency algorithms to ensure that no two users can change the same data at the same time and that all transactions are carried out in the proper order. This prevents people from using online reservation systems from double-booking the same room and protects holders of jointly held bank accounts from accidental overdrafts.
-   **Emphasize very rapid processing, with response times measured in milliseconds:** The effectiveness of an OLTP system is measured by the total number of transactions that can be carried out per second.
-   **Provide indexed data sets:** These are used for rapid searching, retrieval, and querying.
-   **Are available 24/7/365:** Again, OLTP systems process huge numbers of concurrent transactions, so any data loss or downtime can have significant and costly repercussions. A complete data backup must be available for any moment in time. OLTP systems require frequent regular backups and constant incremental backups.
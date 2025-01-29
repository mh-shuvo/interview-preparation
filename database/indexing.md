# Database Indexing
Datbase Indexing is the mechanism to improve the speed and efficiency of retriving and manipulating data from the database.
## How indexing works?
Indexing works by creating a separate data structure that organizes and stores a subset of the data in the database table in a way that makes data retrieval more efficient. When a query is executed, the database management system (DBMS) can use the index to quickly locate the relevant rows without scanning the entire table.

Here's how indexing works step by step:

- `Index Creation:` When you create an index on a column or set of columns, the DBMS generates an index data structure. The type of data structure used depends on the type of index (e.g., B-tree, hash, bitmap).

- `Data Mapping:` The index contains a mapping between the values in the indexed column(s) and the locations (usually row identifiers or pointers) of the corresponding rows in the actual table.

- `Index Maintenance:` As new data is added, updated, or deleted in the table, the index needs to be updated to reflect these changes. This ensures that the index remains consistent with the actual data.

- `Query Execution:`
    - `Query Parsing:` When you submit a query, the DBMS parses the query to understand what data you're requesting.
    - `Query Optimization:` The DBMS's query optimizer decides how to execute the query efficiently. It takes into account factors like available indexes, table statistics, and the query's complexity.
    - `Index Selection:` If the optimizer determines that using an index would speed up the query, it selects the appropriate index to use.
    - `Index Lookup:` The DBMS uses the index to quickly locate the relevant subset of rows. It navigates the index data structure to find the specific entries corresponding to the query's criteria.
    
    - `Row Retrieval:` Once the index points to the desired rows, the DBMS retrieves the actual data from the table based on the row identifiers or pointers stored in the index.

- `Query Results:` The DBMS presents the retrieved data as the query results.

Index Utilization: Indexes are especially effective for queries that involve filtering, sorting, and joining data. They help reduce the number of rows that need to be scanned, leading to faster query performance.


- `Balancing Act:` While indexes significantly improve query speed, they also introduce overhead during data modifications (inserts, updates, deletes) due to the need to update the index data structure. The DBMS aims to strike a balance between query performance and maintenance overhead.

- `Index Fragmentation:` Over time, as data is added, updated, and deleted, indexes can become fragmented, which means the index data structure might not be as efficient as when it was first created. Some DBMSs offer tools to manage and optimize indexes to mitigate fragmentation.

In summary, indexing involves creating a separate data structure that maps values in indexed columns to the corresponding rows in a table. This mapping allows the DBMS to quickly locate relevant data when executing queries. Proper index design and maintenance are essential for optimizing query performance in a database.
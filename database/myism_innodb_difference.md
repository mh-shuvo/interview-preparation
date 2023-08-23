# Difference Between MyISM and InnoDB

## MyISAM
MyISAM was the MySQL default storage engine prior to version 5.5.1, and it still remains a popular choice due to its simplicity and speed. Most specialists consider it to be the best option for beginners who only start mastering MySQL. Unfortunately, one of the primary factors ensuring simplicity is the absence of foreign keys support. As a result, your work won’t involve complicated configurations, but your options are limited. 

Also, this engine requires less disk space and thus is suitable in cases of limited disk space. `It provides extreme speed with the SELECT and INSERT statements, which is a valuable advantage, but it can be slow when dealing with the DELETE and UPDATE statements, as it does not support transactions with rollbacks and table-level locking. `

If you consider MyISAM for your project, note that it applies best to the data warehousing applications or web apps that won’t use transactions. 

Though MyISAM is still used by many applications, it was not surprising that it stopped being the default one and was replaced by InnoDB.

## InnoDB
If you work on applications based on MySQL now, InnoDB will most likely be your storage engine. It ensures all options that a database would require, and is the most popular choice for the absolute majority of developers. 

`InnoDB supports transactions and foreign keys constraints. Thus, it can check the INSERT, UPDATE, and DELETE statements’ consistency much better. It is less speedy than MyISAM, but it is less vulnerable to crushes either. Besides, it offers such an essential advantage as row-level locking, ensuring a more efficient multi-user performance. `

In addition, in the case with multiple storage engines configured, it would be better to disable the unused storage engines to improve server performance. For example, you have ten configured storage engines but use only one of them. In this case, nine storage engines stand idle and only consume server resources with bringing no benefit.

Therefore, MyISAM and InnoDB are the most widely used storage engines for MySQL.


| Features | MyISM  | InnoDB |
| --- | --- | --- |
| Storage limits | 256 TB | 64 TB |
| B-tree indexes | Yes | Yes |
| Backup / point-in-time recovery | Yes | Yes |
| Cluster database support | No | No |
| Clustered indexes | No | Yes |
| Compressed data | Yes | Yes |
| Data caches | No | Yes |
| Encrypted data | Yes | Yes |
| Foreign key support | No | Yes |
| Full-text search indexes | Yes | Yes |
| Geospatial data type support | Yes | Yes |
| Geospatial indexing support | Yes | Yes |
| Hash indexes | No | No |
| Index caches | Yes | Yes |
| Locking granularity | Table | Row |
| MVCC (Multiversion concurrency control) | No | Yes |
| Replication support | Yes | Yes |
| Spatial data types and functions | Yes | Yes |
| Spatial and non-spatial indexes (for spatial columns) | Yes | Yes |
| T-tree indexes | No | No |
| Transactions | No | Yes |
| Update statistics for data dictionary | Yes | Yes |
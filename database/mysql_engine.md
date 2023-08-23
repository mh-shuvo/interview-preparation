# MySQL Storage Engines
MySQL supports the following storage engines that developers can use for their specific purposes:

- `InnoDB` is the most widely used and ACID-based storage engine set as default in MySQL versions 8.0 or higher. The main difference is that it supports foreign key referential integrity constraints.
- `MyISAM` can handle non-transactional tables and support table-level locking and full-text search indexes. It is mainly used on the Web.
- Federated can create a single, local database by connecting physical MySQL servers. It stores data only on the remote server.
- `MEMORY` can create tables and store data in memory for faster performance and data access. It supports table-level locking and non-transactional tables and can be used for creating temporary tables.
- `MERGE` can logically group a set of similar MyISAM tables into one table. The storage engine can manipulate large volumes of data.
- `EXAMPL`E is used to teach developers how to create new storage engines.
Archive is used to store large volumes of unindexed data.
- `CSV` is a flexible storage engine that stores data in CSV files and can be integrated into multiple applications that support a CSV format in order to import and export data.
- `Blackhole` accepts but does not store data, and returns empty data during data retrieval.
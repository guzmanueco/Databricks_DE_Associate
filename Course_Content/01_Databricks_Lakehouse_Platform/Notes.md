# Databricks Lakehouse Platform
## Delta Lake
- Delta Lake: open source storage framework that brings reliability to data lakes.
- Delta Lake is a component which is deployed in the cluster as part of the Databricks runtime. 
- When you save a file in Delta Lake, it is stored in parquet format in one or more files. It also stores a transaction log: versions of the date (json format).
- Delta Lake Advantages:
    - Brings ACID transaction to object storage.
    - Handle scalable metadata.
    - Full audit trail of all changes.
    - Builds upon standard data formats: parquet and json.
- Advanced features of Delta Lake:
    - Time Travel: access to previous versions on the table.
    - Compacting small files and indexing: OPTIMIZE and ZORDER BY
    - VACUUM: cleans up unused data (uncommited files and files that are no longed in the latest table state)

## Relational Entities on Databricks
In Databricks, Databases are Hive Metastore Schemas, that's why we can use two syntaxes to create tables:

- `CREATE DATABASE db_name`

- `CREATE SCHEMA db_name`

A Hive Metastore is a repository of metadata that stores information of Databases, Tables and partitions.

When you create a table/database, they are stored in the default hive directory dbfe:/user/hive/warehouse unless you specify the custom path you want it to be stored, which can be outside the hive folder. This is done by using:
`CREATE SCHEMA db_name LOCATION 'dbfs:/custom/path/db_name.db'`

In Databricks there are two types of tables:

- Managed tables: created under the database hive directory dbfs:/user/hive/warehouse . When you run a DROP command, both the data and the underlying data files will be deleted. `CREATE TABLE table_name`

- External tables: created outside the database directory dbfs:/custom/path . When you run a DROP command, only the data will be deleted, but not the underlying data files (which can be restored). `CREATE TABLE table_name LOCATION 'path'`. The definition of the database will be in the Hive Metastored under the default database, while the data files will be stored in the specified external location.

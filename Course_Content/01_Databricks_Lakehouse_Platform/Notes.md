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
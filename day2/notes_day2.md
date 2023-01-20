# Table of Contents - Day2

- [Table of Contents - Day2](#table-of-contents---day2)
  - [DE 4.3 - Creating Delta Tables](#de-43---creating-delta-tables)
  - [DE 4.4 - Writing to Tables](#de-44---writing-to-tables)
    - [Homework - D.E 4](#homework---de-4)
  - [DE 6.1 - Incremental Data Ingestion with Auto Loader](#de-61---incremental-data-ingestion-with-auto-loader)
  - [DE 6.2 - Reasoning about Incremental Data](#de-62---reasoning-about-incremental-data)
    - [Homework - D.E 6](#homework---de-6)
  - [DE 7.1 - Incremental Multi-Hop in the Lakehouse](#de-71---incremental-multi-hop-in-the-lakehouse)

## DE 4.3 - Creating Delta Tables

- auto generate columns -> GENERATED ALWAYS
- deep clone copies data and medata from a soruce table to a target. this copy occurs incrementally, so executing this command again can sync change from the source to the tatget location
  - i.e., it only copies the whole data the first time
- deleting a shallow clone only removes the underlying json files, so no actual data gets deleted
- when shallow copying the parquet files are not copied in the shallow folder, but only the transactional log

## DE 4.4 - Writing to Tables

- Overwrite data tables using INSERT OVERWRITE
  - We can use overwrites to atomically replace all of the data in a table.
  - Can only overwrite an existing table, not create a new one like our CRAS statement
  - Can overwrite only with new records that match the current table schema -- and thus can be a "safer" technique for overwriting an existing table without disrupting downstream consumers
  - in the transaction log it will look like a **WRITE**
  - Can overwrite individual partitions
- Append to a table using INSERT INTO
- Append, update, and delete from a table using MERGE INTO
- Ingest data incrementally into tables using COPY INTO

### Homework - D.E 4

4.6 to 4.9

## DE 6.1 - Incremental Data Ingestion with Auto Loader

- Auto loader checks on a directory, if new data lands it is automatically picked up
- STREAMING UPDATE is the operation you get when doing DESCRIBE HISTORY of the table

## DE 6.2 - Reasoning about Incremental Data

- questions about 5 ways to stop the stream

### Homework - D.E 6

6.3

## DE 7.1 - Incremental Multi-Hop in the Lakehouse

- **Bronze** tables contain raw data ingested from various sources (JSON files, RDBMS data, IoT data, to name a few examples).
  - replaces traditional data lake
  - provides efficient storage and querying of full, unprocessed history of data
- **Silver** tables provide a more refined view of our data. We can join fields from various bronze tables to enrich streaming records, or update account statuses based on recent activity.
  - reduces data storage complexity, latency and redundancy
  - optimizes ETL throughput and alautic query performance
  - preserves grain of original data
  - eliminates duplicate record
  - production schema enforced
  - data quality checks, corrupt data quarantined
- **Gold** tables provide business level aggregates often used for reporting and dashboarding. This would include aggregations such as daily active website users, weekly sales per store, or gross revenue per quarter by department
  - Power Ml applications, reporting, dashboards, ad hoc analytics
  - refined views od data, typically with aggregation
  - reduces train on production systems
  - Optimizes query performance for business analytics

Data quality increases from Bronze to Gold
This is just a blueprint, you can have as many layers as you want in the Bronze,Silver and Gold

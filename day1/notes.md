# Table of Contents - Day1s

- [Table of Contents - Day1s](#table-of-contents---day1s)
  - [Useful links](#useful-links)
  - [Introduction](#introduction)
    - [Data Lake](#data-lake)
    - [Data Warehouse](#data-warehouse)
    - [Data Lakeouse](#data-lakeouse)
  - [Clusters](#clusters)

## Useful links

- [data-engineer-associate-info](https://www.databricks.com/learn/certification/data-engineer-associate)
- [questions](https://www.databricks.com/learn/certification/data-engineer-associate#:~:text=the%20certification%20exam.-,Questions,-There%20are%2045)
- [practice-exams](https://files.training.databricks.com/assessments/practice-exams/PracticeExam-DataEngineerAssociate.pdf)
- [Data-Engineering-with-Databricks-|-Class-9723-|-Atos](https://partner-academy.databricks.com/learn/course/809/session/1721/data-engineering-with-databricks-class-9723-atos)
- [github-reop](https://github.com/databricks-academy/data-engineering-with-databricks-english/releases/tag/v2.3.13)

## Introduction

- Lakouse architecture wants to uniform the way we collect, transform and load data. Also it uniforms data governance

### Data Lake

- pros:
  - can store raw data
  - cheap
  - easy to scale
- cons:
  - you cannot query the data because the format it is not known

### Data Warehouse

- pros:
  - fast for reading
  - allows query and analytics because the data is well described
- cons:
  - expensive
  - hard to mantain
  - hard to scale
  - can't work with unstructered data

### Data Lakeouse

combine the best of the both of the two and it is cloud agnostic.

## Clusters

![clusters](imgs/clusters.png)

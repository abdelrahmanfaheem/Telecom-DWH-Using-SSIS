# Data Storage ETL Process for Telecom Company

## Project Overview

This project involved collaborating with a telecom company as an ETL Consultant/Developer to design and implement a data storage process. The company required a system to process CSV files that are generated every 5 minutes, containing essential customer transaction data. The goal was to transform and store this data efficiently in a database, ensuring data quality and traceability.

## Table of Contents

1. [Project Description](#project-description)
2. [Data Processing Workflow](#data-processing-workflow)
3. [Data Schema](#data-schema)
4. [Data Quality Measures](#data-quality-measures)
5. [File Archiving Process](#file-archiving-process)
6. [Conclusion](#conclusion)

## Project Description

The telecom company’s system generates CSV files every 5 minutes, which contain key transaction data for customers over a specific time period. The ETL process was designed to handle the following tasks:

- **Data Extraction**: Read the CSV files and extract the necessary fields.
- **Data Transformation**: Clean and validate the data, applying the required transformations.
- **Data Loading**: Store the processed data into the database with additional quality metrics.

## Data Processing Workflow

1. **CSV File Ingestion**: The system ingests the CSV files every 5 minutes.
2. **Data Validation**: Each record is validated against predefined rules, such as checking for null values in non-nullable fields.
3. **Data Transformation**: The data is transformed to match the database schema requirements.
4. **Data Loading**: Valid records are inserted into the main database table, while rejected records are stored in a separate table along with the original CSV filename.

## Data Schema

| Column Name | Data Type | Length | Is Nullable | Sample Data         |
|-------------|-----------|--------|-------------|---------------------|
| ID          | Int       | -      | False       | 156                 |
| IMSI        | String    | 9      | False       | 310120265           |
| IMEI        | String    | 14     | True        | 490154203237518     |
| CELL        | Int       | -      | False       | 123                 |
| LAC         | Int       | -      | False       | 12                  |
| EVENT_TYPE  | String    | 1      | True        | 1                   |
| EVENT_TS    | Timestamp | -      | False       | 16/1/2020 7:45:43   |

## Data Quality Measures

During the data loading process, additional metrics are captured to ensure data quality:

- **Total Records**: The total number of records in the CSV file.
- **Successful Records**: The number of records successfully stored in the database.
- **Rejected Records**: The number of records rejected due to validation errors.
- **File Tracking**: Each stored record is linked to its original CSV file for traceability.

## File Archiving Process

After processing, the CSV files are moved to an archive folder, ensuring that the system's input directory remains clean and that processed files are stored for auditing and future reference.

## Conclusion

This ETL process ensures the efficient, accurate, and traceable storage of telecom transaction data, providing a robust solution for the company’s data management needs.

# Student Mental Health ETL Pipeline

## Project Overview
This project focuses on the **ETL (Extract, Transform, Load)** process of educational survey data. The objective was to build a transformation script that aggregates raw data to analyze the relationship between the length of stay of international students and their average mental health diagnostic scores.

## Engineering Objectives
Instead of simple analysis, this script focuses on data manipulation and schema enforcement:
* **Data Filtering:** Programmatic isolation of specific subsets (International Students) from a larger raw dataset.
* **Aggregation Logic:** Implementing `groupby` operations to calculate statistical averages across multiple metrics.
* **Schema Transformation:** Renaming and formatting columns to match strict output requirements for downstream reporting.

## Transformation Logic
The script performs the following steps to build the final output table:
1.  **Filter:** Selects only records where the student status is 'International'.
2.  **Group:** Segments data by the `stay` (length of stay) column.
3.  **Aggregate:** Calculates the mean for three distinct health metrics (PHQ-9, SCS, ASISS) and counts total records per group.
4.  **Format:** Aliases columns to standard reporting names and applies rounding logic for precision.

## Final Output Schema
The script generates a structured DataFrame (`df`) with the following columns:
* `stay`: Length of stay (Index/Key)
* `count_int`: Count of international students
* `average_phq`: Average PHQ-9 score (Float, rounded to 2 decimals)
* `average_scs`: Average SCS score (Float, rounded to 2 decimals)
* `average_as`: Average ASISS score (Float, rounded to 2 decimals)

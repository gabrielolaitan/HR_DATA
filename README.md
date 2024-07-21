# My Project

## INTRODUCTION

In today's data-driven world, leveraging data analytics to gain insights and drive decision-making is crucial for any organization. This project focuses on analyzing employee data using a combination of Excel, SQL, and Power BI, aiming to uncover valuable insights regarding demographics, tenure, and departmental distributions. By harnessing these tools, we can efficiently clean, analyze, and visualize the data, providing actionable information for the Human Resources department. This structured approach will ensure a thorough analysis, enabling the organization to make informed decisions to enhance workforce management and strategic planning.

**Disclaimer:** All datasets and reports do not represent any company, distribution, or country, but are just a dummy dataset to demonstrate the capabilities of Excel, Power BI, and SQL.

## Objectives

- Analyze employee data to understand demographics, tenure, and department distribution.
- Identify patterns and insights for HR decision-making.

## Problem Statement

- What is the total number of all staff?
- Provide the total number of staff for current, contract, and terminated statuses.
- Provide the oldest serving staff.
- Provide the newest staff.
- Provide the percentage of staff by gender.
- Calculate the average age of staff by department.
- Determine the percentage of employment status of the staff.

## Scope and Requirements

- Data cleaning and preparation using Excel and SQL.
- Data analysis and visualization using Power BI.

## Data Sources

Employee dataset with columns: `id`, `first_name`, `last_name`, `birthdate`, `gender`, `race`, `department`, `jobtitle`, `location`, `hire_date`, `termdate`, `location_city`, `location_state`.

## Tools

| Tool       | Purpose                                        |
|------------|------------------------------------------------|
| SQL Server | Cleaning, testing, and analyzing the data     |
| Excel      | Exploring and transforming the data           |
| Power BI   | Visualizing the data via interactive dashboards|
| GitHub     | Hosting the project documentation and version control |
| Mokkup AI  | Designing the wireframe/mockup of the dashboard |

## Data Exploration Notes

1. There are at least 4 columns that contain the data needed for this analysis, indicating we have everything we need from the file without requiring additional data from the client.
2. The first column contains channel IDs, which are separated by an `@` symbol. We need to extract the channel names from this.
3. Some cells and header names are in a different language. We need to confirm if these columns are necessary, and if so, address them.
4. We have more data than needed, so some columns will need to be removed.

## Data Collection and Extraction

### SQL Database Connection

- Connect to the SQL database.
- Import and load the table into the SQL database.

### Data Cleaning and Preparation

**Data Cleaning:** The aim is to refine our dataset to ensure it is structured and ready for analysis. The cleaned data should meet the following criteria and constraints:

| Property          | Description  |
|-------------------|--------------|
| Number of Rows    | 100          |
| Number of Columns | 4            |

Here is a tabular representation of the expected schema for the clean data:

| Column Name       | Data Type    |
|-------------------|--------------|
| ID                | VARCHAR      |
| NAME              | INTEGER      |
| BIRTHDATE         | INTEGER      |
| GENDER            | INTEGER      |
| DEPARTMENT        | INTEGER      |
| JOB_TITLE         | INTEGER      |
| LOCATION          | INTEGER      |
| HIRE_DATE         | INTEGER      |
| TERMDATE          | INTEGER      |
| LOCATION_CITY     | INTEGER      |
| LOCATION_STATE    | INTEGER      |

### SQL Transformation

1. **ALTER COLUMN NAME:**
   ```sql
   -- We have to change the field name "ï»¿id" to the correct one "id"
   ALTER TABLE human_resources RENAME COLUMN ï»¿id TO id;


![](Screenshot%202024-06-21%20142554.png)
https://github.com/gabrielolaitan/HR_DATA/blob/main/Screenshot%202024-06-21%20142554.png



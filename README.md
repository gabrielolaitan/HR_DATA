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

1. There are at least 13 columns that contain the data we need for this analysis, which signals we have everything we need from the file without needing to contact the client for any more data.
2. The second and third columns contain the first name and last name with what appears to be employee names - we need to concatenate the two columns to get a new “NAME”.
3. Some of the header names are in a different language and lowercase, we need to address them and change them to uppercase.
4. We have more data than we need, so some of these columns would need to be removed.
## Data Collection and Extraction

### SQL Database Connection

- Connect to the SQL database.
- Import and load the table into the SQL database.

## Data Cleaning and Preparation

**Data Cleaning:** The aim is to refine our dataset to ensure it is structured and ready for analysis. The cleaned data should meet the following criteria and constraints:

| Property          | Description  |
|-------------------|--------------|
| Number of Rows    | 100          |
| Number of Columns | 4            |

### And here is a tabular representation of the expected schema for the clean data:
| Column Name | Data Type |
| --- | --- |
| ID | VARCHAR | 
| NAME| CHAR | 
| BIRTHDATE| DATE | 
| GENDER| CHAR | 
| DEPARTMENT| CHAR |
| JOB_TITLE| CHAR |
| LOCATION| CHAR |
| HIRE_DATE| DATE |
| TERMDATE| DATETIME |
| LOCATION_CITY| CHAR |
| LOCATION_STATE| CHAR |

## SQL Transformation

1. **ALTER COLUMN NAME:**
   ```sql
   -- We have to change the field name "ï»¿id" to the correct one "id"
   ALTER TABLE human_resources RENAME COLUMN ï»¿id TO id;


![output](Screenshot%202024-07-21%20142117.png)

### Concatenate:
-- Concatenate first name and last name as name 
 ```sql
SELECT 
    id AS ID,
    CONCAT(first_name, " ", last_name) AS NAME,
    birthdate AS BIRTHDATE,
    gender AS GENDER,
    department AS DEPARTMENT,
    jobtitle AS JOB_TITLE,
    location AS LOCATION,
    hire_date AS HIRE_DATE,
    COALESCE(termdate, '-') AS TERMDATE,
    location_city AS LOCATION_CITY,
    location_state AS LOCATION_STATE
FROM human_resources;
```

### Create The SQL View:

-- Create a view to store the transformed data
```sql
CREATE VIEW project_X AS 
SELECT 
    id AS ID,
    CONCAT(first_name, " ", last_name) AS NAME,
    birthdate AS BIRTHDATE,
    gender AS GENDER,
    department AS DEPARTMENT,
    jobtitle AS JOB_TITLE,
    location AS LOCATION,
    hire_date AS HIRE_DATE,
    COALESCE(termdate, '-') AS TERMDATE,
    location_city AS LOCATION_CITY,
    location_state AS LOCATION_STATE
FROM human_resources;
```

## Testing
### Row Count Check:
```sql
-- Count the total number of records (or rows) in the SQL view
SELECT COUNT(*) AS no_of_rows FROM project_x;
```

### Column Count Check:
```sql
-- Count the total number of columns (or fields) in the SQL view
SELECT COUNT(*) AS column_count 
FROM INFORMATION_SCHEMA.COLUMNS 
WHERE TABLE_NAME = 'project_x';
```

### Duplicate Count Check:
```sql
-- Check for duplicate rows in the view
SELECT 
    NAME, 
    ID, 
    BIRTHDATE, 
    GENDER, 
    DEPARTMENT, 
    JOB_TITLE, 
    LOCATION, 
    HIRE_DATE, 
    TERMDATE, 
    LOCATION_CITY, 
    LOCATION_STATE
FROM project_x
GROUP BY 
    NAME, 
    ID, 
    BIRTHDATE, 
    GENDER, 
    DEPARTMENT, 
    JOB_TITLE, 
    LOCATION, 
    HIRE_DATE, 
    TERMDATE, 
    LOCATION_CITY, 
    LOCATION_STATE
HAVING COUNT(*) > 1;
```

## Excel Transformation

### Creating The Age Column

-- create a new column "AGE" with the datedif formula
```excel
= DATEDIF(C2,TODAY(),"Y")
```


### Creating The Employment Status Column

-- create a new column "EMPLOYMENT STATUS" with the Nextedif formula
```excel
= IF(I2="-","current",IF(I2>=TODAY(),"contract","terminated"))
```



### Creating The Employment Duration Column

-- create a new column "EMPLOYMENT DURATION" with the datedif formula
```excel
= DATEDIF(H2,TODAY(),"Y")
```











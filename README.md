# MySQL Assignment 1 – DDL Commands & Constraints

## Overview
This repository contains the SQL solution for **MySQL Assignment 1 – DDL Commands & Constraints**. The assignment uses an employee database with three related tables:

- `Departments`
- `Location`
- `Employees`

The SQL script demonstrates database and table creation, table alteration, table renaming, truncation, dropping database objects, and the use of relational constraints.

## Files in this repository

| File | Description |
|---|---|
| `SQL_Assignment1_DDL_Commands.sql` | Complete SQL solution for the DDL commands and constraints sections. |
| `MySQL_Assignment_1_Detailed_Documentation.docx` | Detailed explanation and question-by-question compliance review. |
| `README.md` | Project overview and execution instructions. |

> Add the original assignment PDF to the repository only if you are permitted to share it.

## Database schema

### Departments
| Column | Data type | Constraint |
|---|---|---|
| `department_id` | `INT` | `PRIMARY KEY` |
| `department_name` | `VARCHAR(100)` | `UNIQUE`, `NOT NULL` in the constraints section |

### Location
| Column | Data type | Constraint |
|---|---|---|
| `location_id` | `INT` | `PRIMARY KEY`; `AUTO_INCREMENT` in the constraints section |
| `location` | `VARCHAR(30)` | `UNIQUE`, `NOT NULL` in the constraints section |

### Employees
| Column | Data type | Constraint / purpose |
|---|---|---|
| `employee_id` | `INT` | `PRIMARY KEY` |
| `employee_name` | `VARCHAR(50)` | `NOT NULL` in the constraints section |
| `gender` | `ENUM('M','F')` | Allows only `M` or `F` |
| `age` | `INT` | `CHECK (age >= 18)` in the constraints section |
| `hire_date` | `DATE` | Defaults to the current date in the constraints section |
| `designation` | `VARCHAR(100)` initially | Modified to `VARCHAR(255)` in the DDL section |
| `department_id` | `INT` | Foreign key to `Departments.department_id` |
| `location_id` | `INT` | Foreign key to `Location.location_id` |
| `salary` | `DECIMAL(10,2)` | Salary amount |

The `Employees` table contains foreign-key relationships to both parent tables.

## Work completed

### Part A – DDL commands
1. Created the `employee` database and selected it.
2. Created `Departments`, `Location`, and `Employees` using the supplied schema.
3. Added an `email` column to `Employees`.
4. Modified `designation` from `VARCHAR(100)` to `VARCHAR(255)`.
5. Dropped the `age` column.
6. Renamed `hire_date` to `date_of_joining`.
7. Renamed `Departments` to `Departments_Info`.
8. Renamed `Location` to `Locations`.
9. Truncated the `Employees` table.
10. Dropped the `Employees` table and then the `employee` database.

### Part B – Constraints
1. Dropped the database if it existed and recreated it.
2. Applied a primary key to `Departments.department_id`.
3. Applied `UNIQUE` and `NOT NULL` to `Departments.department_name`.
4. Applied `PRIMARY KEY` and `AUTO_INCREMENT` to `Location.location_id`.
5. Applied `UNIQUE` and `NOT NULL` to `Location.location`.
6. Applied a primary key to `Employees.employee_id`.
7. Required `Employees.employee_name` using `NOT NULL`.
8. Restricted `gender` to `M` or `F` using `ENUM`.
9. Added `CHECK (age >= 18)`.
10. Set the default `hire_date` to the current date.
11. Added foreign keys from `Employees` to `Departments` and `Location`.

## Requirements cross-check

The submitted SQL script contains statements addressing **all requirements listed in the assignment PDF**:

- Database and three-table creation
- All four requested `ALTER TABLE` operations
- Both table renames
- `TRUNCATE TABLE Employees`
- Dropping the Employees table and employee database
- Database recreation
- All primary-key, unique, not-null, enum, check, default and foreign-key constraints

The detailed Word document contains the requirement-by-requirement checklist and explanations.

## How to run

1. Install and open MySQL Server and a MySQL client such as MySQL Workbench.
2. Clone or download this repository.
3. Open `SQL_Assignment1_DDL_Commands.sql` in the SQL editor.
4. Confirm that you are using a practice database and that you do not need any existing database named `employee`.
5. Execute the script from top to bottom.
6. Inspect the final tables using:

```sql
USE employee;
SHOW TABLES;

SHOW CREATE TABLE Departments;
SHOW CREATE TABLE Location;
SHOW CREATE TABLE Employees;
```

The script has two phases. The first phase demonstrates the DDL modifications and then drops the database. The second phase recreates the database and creates the tables with constraints. Therefore, the final database contains the constrained schema using the original table names.

## MySQL compatibility notes

- Use **MySQL 8.0.16 or later** for enforced `CHECK` constraints.
- The script uses `hire_date DATE DEFAULT (CURRENT_DATE)`. Expression defaults are supported in modern MySQL 8.0 versions; confirm compatibility with the exact server version used.
- The script contains `DROP DATABASE IF EXISTS employee`, which deletes the existing database and its contents before recreating it. Do not run it against a database containing data you need.
- The assignment does not request sample records or negative test cases. They are not included in the submitted solution.

## Verification status

The SQL was reviewed against the supplied assignment question sheet. All listed requirements are represented in the script. This repository documentation records a **code-level review**; it does not claim that the SQL has been executed successfully on a live MySQL server. Run it in your MySQL environment and retain screenshots or execution output if your submission requires proof.

## Learning outcomes

This assignment demonstrates practical use of:

- Data Definition Language (DDL)
- `CREATE DATABASE` and `CREATE TABLE`
- `ALTER TABLE` operations
- `RENAME TABLE`
- `TRUNCATE TABLE`
- `DROP TABLE` and `DROP DATABASE`
- Primary and foreign keys
- `UNIQUE`, `NOT NULL`, `ENUM`, `CHECK`, `DEFAULT`, and `AUTO_INCREMENT`
- Basic relational database design

# Secondary School Student Records & Academic Reporting Database

## Project Overview

This project is a MySQL-based Student Records and Academic Reporting Database designed to help secondary schools manage student information, academic subjects, examination results, and report card generation.

The system provides a structured way to store student records, track academic performance across different terms and academic years, calculate subject averages, assign grades, and generate student report cards using SQL queries and stored procedures.

The project uses sample student records to demonstrate how the database works and can be expanded to accommodate additional students, subjects, and academic levels.

## Objectives

- Create a centralized database for managing student information.
- Store student details, including names, dates of birth, gender, admission dates, and class levels.
- Maintain a structured list of academic subjects.
- Record students' assessment scores across different subjects.
- Automatically calculate term averages and weighted subject totals.
- Assign grades and performance remarks based on students' results.
- Generate academic report cards for individual students.

## Technologies Used

- **Database Management System:** MySQL
- **Query Language:** SQL
- **Development Environment:** MySQL Workbench

## Database Structure

The database is named `sac_management` and consists of four main tables:

| Table | Description |
|---|---|
| `students` | Stores student personal and admission information. |
| `forms` | Stores the five secondary school levels, from Form One to Form Five. |
| `subjects` | Maintains the list of academic subjects offered by the school. |
| `results` | Stores student assessment scores, averages, coefficients, totals, grades, and remarks. |

### Database Relationships

- Each student is assigned to a form.
- Each student can have multiple academic result records.
- Each subject can have results recorded for multiple students.
- Student and subject records are connected to the results table through foreign keys.

## Key Features

### 1. Student Information Management
Stores student details such as:
- Student ID and student number
- First and last names
- Date of birth
- Gender
- Admission date
- Form/class
- Student status (Active or Inactive)

### 2. Subject Management
Maintains a list of academic subjects, including English Language, Mathematics, Biology, Chemistry, Physics, Geography, History, and Computer Science.

### 3. Academic Results Management
Records the following information for each student and subject:
- Academic year
- Term
- S1 assessment score
- S2 assessment score
- Term average
- Subject coefficient
- Weighted total
- Grade
- Performance remarks

### 4. Automated Academic Calculations

SQL UPDATE statements are used to calculate academic performance.

**Term Average:**

`(S1 + S2) / 2`

**Weighted Subject Total:**

`Term Average × Coefficient`

**Grade Classification:**

| Average | Grade |
|---|---|
| 80–100 | A |
| 70–79.99 | B |
| 60–69.99 | C |
| 50–59.99 | D |
| 40–49.99 | E |
| Below 40 | F |

**Performance Remarks:**

| Average | Remark |
|---|---|
| 80–100 | Excellent |
| 70–79.99 | Good |
| 60–69.99 | Satisfactory |
| 50–59.99 | Needs Improvement |
| Below 50 | Poor |

### 5. Report Card Generation

A stored procedure called `generate_report_card` retrieves academic results for an individual student based on their student ID, academic year, and term.

The generated report includes:
- Student name
- Form/class
- Academic year
- Term
- Subject names
- S1 and S2 scores
- Term average
- Coefficient
- Total
- Grade
- Performance remarks

## Sample Data

The database currently contains two sample students:

| Student Name | Student Number | Form |
|---|---|---|
| Mary Ann | STU-2026-0001 | Form One |
| John Doe | STU-2026-0002 | Form One |

Sample academic results are provided for five subjects per student for the 2026/2027 academic year, First Term.

## How to Run the Project

1. Install MySQL Server and MySQL Workbench.
2. Open MySQL Workbench and connect to your local MySQL server.
3. Create a new SQL script.
4. Copy the project SQL queries into the script.
5. Execute the queries in their correct order, starting with database creation and table creation, followed by data insertion, calculations, and stored procedure creation.
6. Run the report card procedure to retrieve a student's academic results.

**Create the database:**

```sql
CREATE DATABASE sac_management;
USE sac_management;
```

**Generate Mary Ann's report card:**

```sql
CALL generate_report_card(
    1,
    '2026/2027',
    'Term 1'
);
```

**Generate John Doe's report card:**

```sql
CALL generate_report_card(
    2,
    '2026/2027',
    'Term 1'
);
```

## Example SQL Queries

**View all registered students:**

```sql
SELECT * FROM students;
```

**View all available subjects:**

```sql
SELECT * FROM subjects;
```

**View academic results:**

```sql
SELECT * FROM results;
```

**Retrieve a student's information using their student number:**

```sql
SELECT
    student_number,
    CONCAT(first_name, ' ', last_name) AS Student_Name,
    date_of_birth,
    gender,
    admission_date,
    student_status
FROM students
WHERE student_number = 'STU-2026-0001';
```

## Future Improvements

The database can be expanded with additional functionality, including:

- Registration of students across all five forms.
- Support for additional subjects and instructors.
- Management of multiple academic years and school terms.
- Student class rankings and subject positions.
- Class averages and overall academic performance.
- Attendance and disciplinary records.
- Automated report card generation and printing.
- Student identification card generation.
- Promotion and progression tracking.

## Project Status

**Current Status:** Initial Database Implementation Completed.

The project currently demonstrates student registration, subject management, academic result recording, automated grade calculations, and report card generation using MySQL.

## Author

**Kathleen Elaine Efelelanyoh**

GitHub: [Kathleen-Elaine](https://github.com/Kathleen-Elaine)

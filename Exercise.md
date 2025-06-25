# Two Tables Design Recipe Template

## 1. Extract nouns from the user stories or specification
As a coach
So I can get to know all students
I want to see a list of students' names.


As a coach
So I can get to know all students
I want to see a list of cohorts' names.


As a coach
So I can get to know all students
I want to see a list of cohorts' starting dates.


As a coach
So I can get to know all students
I want to see a list of students' cohorts.

Nouns:
student, name, cohort, name, starting date

## 2. Infer the Table Name and Columns

Put the different nouns in this table.
```
| Record                | Properties          |
| --------------------- | ------------------  |
| student               | name                |
| cohort                | name, starting date |
```

1. Name of the first table (always plural): `cohorts` 

    Column names: `name`, `starting_date`

2. Name of the second table (always plural): `students` 

    Column names: `name`

## 3. Decide the column types

Table: cohorts
- id: SERIAL
- name: text
- starting_date: date


Table: students
- id: SERIAL
- name: text

## 4. Decide on The Tables Relationship

1. Can one cohort have many students? YES
2. Can one student have many cohorts? NO

-> Therefore,
-> A cohort HAS MANY students
-> A student BELONGS TO a cohort

-> Therefore, the foreign key is on the students table.

## 5. Write the SQL

```sql
-- file: student_directory_2.sql

-- Create the table without the foreign key first.
CREATE TABLE cohorts (
  id SERIAL PRIMARY KEY,
  name text,
  starting_date date
);

-- Then the table with the foreign key second.
CREATE TABLE students (
  id SERIAL PRIMARY KEY,
  name text,
  -- The foreign key name is always {other_table_singular}_id
  cohort_id int,
  constraint fk_cohort foreign key(cohort_id)
    references cohorts(id)
    on delete cascade
);

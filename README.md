# Student Directory Database Project

## Overview
A PostgreSQL database system for managing students and their cohorts. This project implements a two-table relational database design to help coaches track students and the cohorts they belong to.

## Database Schema

### Tables
- **cohorts**: Stores cohort information (name, starting date)  
- **students**: Stores student information (name, cohort assignment)

### Relationship
- One cohort can have many students
- One student belongs to one cohort
- Implemented using foreign key relationship

## User Stories Implemented

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

## Setup Instructions

### Prerequisites
- PostgreSQL installed and running
- Command line access

### Database Setup
```bash
# 1. Create the database
createdb student_directory_2

# 2. Load the schema
psql -h 127.0.0.1 student_directory_2 < student_directory_2.sql

# 3. Connect to verify setup
psql -h 127.0.0.1 student_directory_2

-- Check tables were created
\dt

-- View table structure
\d cohorts
\d students
```

### Database Structure


![Screenshot 2025-06-25 at 14 30 58](https://github.com/user-attachments/assets/3b5e33dd-afa2-41f5-a50e-8c30609c0914)

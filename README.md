# Homework Assignment #7 - Extended Database Operations

## Introduction

In this homework assignment, we will continue working with the homework from the previous module.

For this assignment, we will use the PostgreSQL database. Start a Docker container in the command line using the following command:

```bash
docker run --name some-postgres -p 5432:5432 -e POSTGRES_PASSWORD=mysecretpassword -d postgres
```
 ## Execution Steps

### Step 1: Set Up Database

1. Replace "some-postgres" with your preferred container name and "mysecretpassword" with your chosen password for connecting to the database.

   **CAUTION:** If agreed with the mentor and due to technical limitations in using PostgreSQL, you can replace it with SQLite.

### Step 2: Implement SQLAlchemy Models

1. Implement SQLAlchemy models for the following tables:
   - Students
   - Groups
   - Instructors
   - Subjects with an indication of the instructor who teaches the subject
   - Table where each student has grades for specified subjects with the indication of when the grade was received

### Step 3: Use Alembic for Database Migrations

1. Utilize Alembic to create migrations in the database.

### Step 4: Write seed.py Script

1. Write a script named seed.py to fill the obtained database with random data:
   - Approximately 30-50 students
   - 3 groups
   - 5-8 subjects
   - 3-5 instructors
   - Up to 20 grades for each student in all subjects
   - Use the Faker package for data population
   - During data population, use the SQLAlchemy session mechanism

### Step 5: Execute Queries

1. Perform the following queries on the obtained database:

   - Find 5 students with the highest average grade across all subjects.
   - Find the student with the highest average grade in a specific subject.
   - Find the average grade in groups for a specific subject.
   - Find the overall average grade.
   - Find the courses taught by a specific instructor.
   - Find the list of students in a specific group.
   - Find the grades of students in a specific group for a certain subject.
   - Find the average grade given by a specific instructor for their subjects.
   - Find the list of courses attended by a student.
   - Find the list of courses taught by a specific instructor to a specific student.

   Create separate SQL query files for each query in my_select.py, where there will be 10 functions from select_1 to select_10. Each function should return results similar to the previous homework. Use the SQLAlchemy session mechanism in queries.

### Additional Task

#### Part 1

1. For the additional task, create queries of increased complexity:
   - Average grade given by a specific instructor to a specific student.
   - Grades of students in a specific group for a specific subject on the last session.

#### Part 2

1. Instead of the seed.py script, think and implement a full CLI program for CRUD operations with the database. Use the argparse module for this purpose.

   - Use the command --action or the shortened version -a for CRUD operations.
   - Use the command --model (-m) to specify on which model the operation should be performed.

   **Example:**

   - `--action create -m Teacher --name 'Boris Jonson'` for creating a teacher.
   - `--action list -m Teacher` to show all teachers.
   - `--action update -m Teacher --id 3 --name 'Andry Bezos'` to update data for the teacher with id=3.
   - `--action remove -m Teacher --id 3` to remove the teacher with id=3.

   Implement these operations for each model.

   **INFO:** Examples of executing commands in the terminal.

   - Create a teacher:

     ```bash
     py main.py -a create -m Teacher -n 'Boris Jonson'
     ```

   - Create a group:

     ```bash
     py main.py -a create -m Group -n 'AD-101'
     ```

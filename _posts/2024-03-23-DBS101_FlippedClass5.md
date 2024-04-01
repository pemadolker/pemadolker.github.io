---
Title: DBS101 Flipped Class 5
categories: [DBS101, Flipped_Class5]
tags: [DBS101]
---

### Topic: Types of Normal Forms

### Let's get started
Students were divided into 4 groups for this flipped class as well and the topic for the flipped class was normal forms. Each group was assigned to a topic on the types of normal forms; group 1 got first normal form and second normal form, group 2 got the topic Boyce-Codd Normal Form (BCNF), group 3 and 4 got third normal form and fourth normal form . For the first 10 minutes, we were briefed on the instructions for the flipped class and we got 30 minutes for group discussions and 20 minutes to present an example of the given topic to the class. 

### Expected outcome
1. Apply normal forms to optimise database designs.
2. Understand the importance of reducing databases to normal forms.

#### Before we move on to the topic, let's run through what a normalization actually is.
DBMS Normalization is a systematic approach to decompose (break down) tables to eliminate data redundancy(repetition) and undesirable characteristics like Insertion anomaly in DBMS, Update anomaly in DBMS, and Delete anomaly in DBMS.
It is a` multi-step process` that puts data into tabular form, removes duplicate data, and set up the relationship between tables.
- Why we need Normalization in DBMS ?
1. for handling data integrity
2. for keeping data consistent 
3. for storage optimization
4. for making the database structure more scalable and adaptable and
5. To ensure data dependencies 

### Types of DBMS Normal forms
Normalization rules are divided into the following normal forms:
#### 1. First normal form (1NF)
For a table to be in the First Normal Form, it should follow the following 4 rules:
1. It should only have single(atomic) valued attributes/columns.
2. Values stored in a column should be of the same domain.
3. All the columns in a table should have unique names.
4. And the order in which data is stored should not matter.

Let's see an example.

The table below has 4 columns and it fulfills the First Normal form except that the emp_skills column holds multiple comma-separated values while each column should have a single value.

![alt text](<../img/DBS/Screenshot from 2024-03-24 16-58-31.png>)

To fix this, we can either remove the emp_skills column from the Employee table and keep it in some other table or add multiple rows for the employee and each row is linked with one skill.

1.Create Separate tables for Employee and Employee Skills

![alt text](<../img/DBS/Screenshot from 2024-03-24 17-04-04.png>)

![alt text](<../img/DBS/Screenshot from 2024-03-24 17-04-29.png>)

2.Add Multiple rows for Multiple skills

![alt text](<../img/DBS/Screenshot from 2024-03-24 17-04-43.png>)

#### 2. Second normal form (2NF)
For a table to be in the Second Normal Form,
1. It should be in the First Normal form and 
2. It should not have Partial Dependency(when a non-primary key column depends on only a part of the primary key.)

Let's say we have two tables Students and Subjects, to store student information and information related to subjects.

Student table:   

![alt text](<../img/DBS/Screenshot from 2024-03-24 17-39-59.png>) 

subject table:

![alt text](<../img/DBS/Pasted image.png>)

another table Score to store the marks scored by students in any subject :

![alt text](<../img/DBS/Screenshot from 2024-03-24 17-45-37.png>)

Entire system will be Normalized as per the Second Normal Form if we move the column teacher_name(which depends on the subject information or just the subject_id) to the Subjects table.
 
Updated Subject table:

![alt text](<../img/DBS/Screenshot from 2024-03-24 17-55-25.png>) 

Updated Score table:

![alt text](<../img/DBS/Screenshot from 2024-03-24 17-55-50.png>)

#### 3. Third normal form (3NF)
A table is said to be in the Third Normal Form when,
1. It satisfies the First Normal Form and the Second Normal form and 
2. It doesn't have Transitive Dependency( when a non-primary key column depends on another non-primary key column rather than directly on the primary key).

For example:

![alt text](<../img/DBS/Screenshot from 2024-03-24 19-39-03.png>)

The above table has a primary key`Student_ID` and a transitive dependency where`Teacher_Department` depends on `Teacher`, which is not the primary key. In oder to obtain 3NF, we split the table into following tables;

- Student table:

![alt text](<../img/DBS/Screenshot from 2024-03-24 19-39-21.png>)

- Subject table:

![alt text](<../img/DBS/Screenshot from 2024-03-24 19-39-36.png>)

- Teacher table:

![alt text](<../img/DBS/Screenshot from 2024-03-24 19-39-45.png>)

- Student_Teacher table:

![alt text](<../img/DBS/Screenshot from 2024-03-24 19-39-59.png>)

Now, Teacher_Department does not depend on Teacher in a transitive manner, satisfying the third normal form.

#### 4. Boyce-Codd Normal Form (BCNF)
Is a higher version of the Third Normal Form and a 3NF table that does not have `multiple overlapping candidate keys` is said to be in BCNF.

For a table to be in BCNF, 
1. R must be in the 3rd Normal Form and 
2. for each functional dependency ( X → Y ), X should be a Super Key.

- Employees

![alt text](<../img/DBS/Screenshot from 2024-03-24 20-06-18.png>)

The above table is in 3NF as there is no transitive dependencies. However, it is not in BCNF because Project_ID determines Project_Name, and Department is functionally dependent on Project_ID, not on the entire primary key.

To normalize it into BCNF, we can split the table into two:

- Employee_Projects table:

![alt text](<../img/DBS/Screenshot from 2024-03-24 20-06-28.png>)

- Projects table:

![alt text](<../img/DBS/Screenshot from 2024-03-24 20-06-49.png>)

These tables ensure that no non-trivial functional dependencies are there other than those involving candidate keys.

#### 5. Fourth normal form (4NF)
A table is said to be in the Fourth Normal Form when,
1. It is in the Boyce-Codd Normal Form and 
2. it doesn't have Multi-Valued Dependency(when a row in a table implies the existence of multiple rows in another table).

Let's consider a table called `Student_Courses` that tracks students and the courses they are enrolled in.

![alt text](<../img/DBS/Screenshot from 2024-03-24 20-24-15.png>)

The above table have a multi-valued dependency: for a given Student_ID, the combination of Student_Name and Instructor determines the Course_Name. In order to normalize this into 4NF, we split the taable into two:

- Student_Courses table:

![alt text](<../img/DBS/Screenshot from 2024-03-24 20-29-04.png>)

- Course_Instructors table: 

![alt text](<../img/DBS/Screenshot from 2024-03-24 20-28-42.png>)

Now both the tables are in 4NF and there's no multi-valued dependency as each instructor is associated with a specific course.

### KEY TAKEAWAY 

- Normalization helps you with data integrity, data consistency, better relationship between tables, more scalable design for tables and removes dependencies, such as Partial Dependency, Transitive Dependency, Join Dependency, etc.
- First Normal form, Second Normal form, Third Normal form, Boyce-Codd Normal form, Fourth Normal form and Fifth Normal form are the different Normal Forms in DBMS.
- BCNF is a higher version of the Third Normal Form.
- Fifth Normal Form or 5NF is also known as Project-Join Normal Form as it fixes Join dependency in tables.
 
### Experience
The flipped class session was around an hour long and all the groups did their best in presenting their topic along with an example to the class. I would rate this flipped class 4.5 on the scale of 5 and I personally think flipped class is very effective.

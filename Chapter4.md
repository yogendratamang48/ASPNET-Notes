## Chapter 4 ADO.NET and Entity Framework
### Database Fundamentals
Database is organized collection of data. There are tables, views, queries, reports and other objects in database.
Database Management System Software stores data so that it will be easy for us to retrieve, manipulate and produce information.
### Core Concepts:
#### Tables
Tables are real world entities represenation in the database. They have their own attributes. They are related to other entities through some relations. 
For eg. If you are going to make database for school. There can be a table 'Student' (representing Students). The table may have attributes like age, roll number etc. Student table may be realted to other tables like Faculty, Teacher, Subject etc.
Tables give structure in which we put our real world data. Records are inserted into table after the structure is created.
#### Queries
Queries are language to interact with the database. We perform queries to **C**reate, **R**ead, **U**pdate and **D**eleting records of the database.
### *Usefule Examples* ###
Consider we have table 'Student' like below:  
| StudentID | FullName | Roll | Age |
| --------- | -------- | ---- | --- |
| 1 | Sulav Poudel | ELX-014-440 | 22 |


#### *SELECT* Query ###
Select query is used to retrieve or read data from database.
example:  
>   *SELECT * FROM Student*  
This query will return all data with all attributes
  
>   SELECT FullName, Roll FROM Student;  
>   SELECT * FROM Student WHERE Age>20;


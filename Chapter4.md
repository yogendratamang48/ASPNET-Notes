## Chapter 4 ADO.NET and Entity Framework
### 4.1 Database Fundamentals
Database is organized collection of data. There are tables, views, queries, reports and other objects in database.
Database Management System Software stores data so that it will be easy for us to retrieve, manipulate and produce information.
### 4.2 Core Concepts:
#### 4.2.1 Tables
Tables are real world entities represenation in the database. They have their own attributes. They are related to other entities through some relations. 
For eg. If you are going to make database for school. There can be a table 'Student' (representing Students). The table may have attributes like age, roll number etc. Student table may be realted to other tables like Faculty, Teacher, Subject etc.
Tables give structure in which we put our real world data. Records are inserted into table after the structure is created.
#### 4.2.2 Queries
Queries are language to interact with the database. We perform queries to **C**reate, **R**ead, **U**pdate and **D**eleting records of the database.
### *Usefule Examples* ###
| StudentID | FullName | Roll | Age |
| --------- | -------- | ---- | ---- |
| 1 | Sulav Poudel | ELX-014-440 | 22 |
|2|Dhiroj Kumar Majhi|ELX-014-412|23|
|3|Sampurna Khanal|ELX-014-435|24|
|4|Renuka Kshetri|ELX-014-430|18|
|5|Bibek khanal|ELX-014-410|26|
|6|Purna Kalyan Shakya|ELX-014-428|17|
|7|Niraj Budhathoki|ELX-014-416|24|
|8|Manish Kshettri |ELX-014-414|21|
|10|Utsab Uprety |ELX-014-442|19|
|11|Samana Devkota|ELX-014-434|20|
|12|Subarna Rai |ELX-014-441|21|
|13|Ravi Timsina |ELX-014-446|19|
|14|Ayusha Gartaula |ELX-014-409|20|
|1003|Ashish Thapamagar|ELX-014-407|22|

#### *4.2.2.1 INSERT * Query  
This query is used to enter data in the tables  
(Look into Chapter 4_1 file)  

#### *4.2.2.2 SELECT* Query ###
Select query is used to retrieve or read data from database.
example:  
___
>   `SELECT * FROM Student;`  
This query will return all data with all attributes
 ###  Result ###
| StudentID | FullName | Roll | Age |
| ------ | ----------- | ------ | ---- |
| 1 | Sulav Poudel | ELX-014-440 | 22 |
|2|Dhiroj Kumar Majhi|ELX-014-412|23|
|3|Sampurna Khanal|ELX-014-435|24|
|4|Renuka Kshetri|ELX-014-430|18|
|5|Bibek khanal|ELX-014-410|26|
|6|Purna Kalyan Shakya|ELX-014-428|17|
|7|Niraj Budhathoki|ELX-014-416|24|
|8|Manish Kshettri |ELX-014-414|21|
|10|Utsab Uprety |ELX-014-442|19|
|11|Samana Devkota|ELX-014-434|20|
|12|Subarna Rai |ELX-014-441|21|
|13|Ravi Timsina |ELX-014-446|19|
|14|Ayusha Gartaula |ELX-014-409|20|
|1003|Ashish Thapamagar|ELX-014-407|22| 
___
>   `SELECT FullName, Roll FROM Student;`  
This query retrieves all students but only two attributes: FullName and Roll  
### Result ###
| FullName | Roll |
| ------ | ----------- |
| Sulav Poudel | ELX-014-440 |
|Dhiroj Kumar Majhi|ELX-014-412|
|Sampurna Khanal|ELX-014-435|
|Renuka Kshetri|ELX-014-430|
|Bibek khanal|ELX-014-410|
|Purna Kalyan Shakya|ELX-014-428|
|Niraj Budhathoki|ELX-014-416|
|Manish Kshettri |ELX-014-414|
|Utsab Uprety |ELX-014-442|
|Samana Devkota|ELX-014-434|
|Subarna Rai |ELX-014-441|
|Ravi Timsina |ELX-014-446||
|Ayusha Gartaula |ELX-014-409|
|Ashish Thapamagar|ELX-014-407|
___
>   `SELECT * FROM Student WHERE Age>20;`  
This query will result all students (with all attributes due to *) whose age is greater than 20
___
#### Update and Delete Query ####  
**Update** Query is used to update record in the table. **Delete** is used to remove record from the table. (For example look into Chapter 4_1 File)
#### ADO.NET ####  
![ADO.NET Architecure](ado.JPG)  
ADO.NET is part of **Base Base Class Libraries (BCL)** used for access and modification of data stored data in Database Systems(Mostly Relational). It provides set of classes that exposes data access services.  
ADO.NET Components:  
 * .NET Framework data providers  
 It is used for connecting to database, executing commands, and retrieving results. Data providers mainly contains following four core objects:
    * Connection  
    it establishes a connection to specific datasource
    * Command  
    Executes commands against the datasource.
    * DataReader  
    Reads data from the datasource in read-only fashion.
    * DataAdapter  
    It provides bridge between the Dataset oject and datasource. It populates a dataset and resolves updates with datasource.
 * DataSet  
 The dataset is memory based relational represenation of data. It is part of disconnected environment. It consists of one or more data table (DataTable) objects made up of rows (DataRow) and Column (DataColun) of data

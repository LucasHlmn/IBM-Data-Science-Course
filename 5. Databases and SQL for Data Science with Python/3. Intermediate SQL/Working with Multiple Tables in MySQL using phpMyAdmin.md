<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0110EN-SkillsNetwork/labs/Lab%20-%20Create%20Tables%20and%20Load%20Data%20in%20MySQL%20using%20phpMyAdmin/images/IDSNlogo.png" width="200" height="200">

# Hands-on Lab: Working with Multiple Tables in MySQL using phpMyAdmin

**Estimated time needed:** 20 minutes

In this lab, you will learn how to create tables and load data in the MySQL database service using the phpMyAdmin graphical user interface (GUI) tool.

# 

## Software Used in this Lab

In this lab, you will use <a href="https://www.mysql.com/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDB0110ENSkillsNetwork24601058-2021-01-01">MySQL</a>. MySQL is a Relational Database Management System (RDBMS) designed to efficiently store, manipulate, and retrieve data.

<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0110EN-SkillsNetwork/labs/Lab%20-%20Create%20Tables%20and%20Load%20Data%20in%20MySQL%20using%20phpMyAdmin/images/mysql.png" width="100" height="100">
<p></p>

To complete this lab you will utilize MySQL relational database service available as part of IBM Skills Network Labs (SN Labs) Cloud IDE. SN Labs is a virtual lab environment used in this course.

# 

## Database Used in this Lab

The database used in this lab is an internal database. You will be working on a sample HR database. This HR database schema consists of 5 tables called **EMPLOYEES**, **JOB_HISTORY**, **JOBS**, **DEPARTMENTS** and **LOCATIONS**. Each table has a few rows of sample data. The following diagram shows the tables for the HR database:

<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20Create%20tables%20using%20SQL%20scripts%20and%20Load%20data%20into%20tables/images/Sample_1.PNG" width="670" height="400">

## Objectives

After completing this lab you will be able to:

*   Write SQL queries that access more than one table
*   Compose queries that access multiple tables using a nested statement in the WHERE clause
*   Build queries with multiple tables in the FROM clause
*   Write Implicit Join queries with join criteria specified in the WHERE clause
*   Specify aliases for table names and qualify column names with table aliases

In this lab, you will through some SQL practice problems that will provide hands-on experience with SQL queries that access multiple tables. You will be:

*   Accessing Multiple Tables with Sub-Queries
*   Accessing Multiple Tables with Implicit Joins

<br>

**How does an Implicit version of CROSS JOIN (also known as Cartesian Join) statement syntax look?**

```
SELECT column_name(s)
FROM table1, table2;
```

<br>

**How does an Implicit version of INNER JOIN statement syntax look?**

```
SELECT column_name(s)
FROM table1, table2
WHERE table1.column_name = table2.column_name;
```

# Exercise 1: Accessing Multiple Tables with Sub-Queries

1.  Problem:

    > *Retrieve only the EMPLOYEES records that correspond to jobs in the JOBS table.*

     <details>
     <summary>Solution</summary>

    ```
    select * from EMPLOYEES where JOB_ID IN (select JOB_IDENT from JOBS);
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/1A.png)

     </details>

2.  Problem:

    > *Retrieve only the list of employees whose JOB_TITLE is Jr. Designer.*

     <details>
     <summary>Solution</summary>

    ```
    select * from EMPLOYEES where JOB_ID IN (select JOB_IDENT from JOBS where JOB_TITLE= 'Jr. Designer');
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/1B.png)

     </details>

3.  Problem:

    > *Retrieve JOB information and list of employees who earn more than $70,000.*

     <details>
     <summary>Solution</summary>

    ```
    select JOB_TITLE, MIN_SALARY,MAX_SALARY,JOB_IDENT from JOBS where JOB_IDENT IN (select JOB_ID from EMPLOYEES where SALARY > 70000 );
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/1C.png)

     </details>

4.  Problem:

    > *Retrieve JOB information and list of employees whose birth year is after 1976.*

     <details>
     <summary>Solution</summary>

    ```
    select JOB_TITLE, MIN_SALARY,MAX_SALARY,JOB_IDENT from JOBS where JOB_IDENT IN (select JOB_ID from EMPLOYEES where YEAR(B_DATE)>1976 );
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/1D.png)

     </details>

5.  Problem:

    > *Retrieve JOB information and list of female employees whose birth year is after 1976.*

     <details>
     <summary>Solution</summary>

    ```
    select JOB_TITLE, MIN_SALARY,MAX_SALARY,JOB_IDENT from JOBS  where JOB_IDENT IN (select JOB_ID from EMPLOYEES where YEAR(B_DATE)>1976 and SEX='F' );
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/1E.png)

     </details>

<br>

# Exercise 2: Accessing Multiple Tables with Implicit Joins

1.  Problem:

    > *Perform an implicit cartesian/cross join between EMPLOYEES and JOBS tables.*

     <details>
     <summary>Solution</summary>

    ```
    select * from EMPLOYEES, JOBS;
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/2A.png)

     </details>

2.  Problem:

    > *Retrieve only the EMPLOYEES records that correspond to jobs in the JOBS table.*

     <details>
     <summary>Solution</summary>

    ```
    select * from EMPLOYEES, JOBS where EMPLOYEES.JOB_ID = JOBS.JOB_IDENT;
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/2B.png)

     </details>

3.  Problem:

    > *Redo the previous query, using shorter aliases for table names.*

     <details>
     <summary>Solution</summary>

    ```
    select * from EMPLOYEES E, JOBS J where E.JOB_ID = J.JOB_IDENT;
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/2C.png)

     </details>

4.  Problem:

    > *Redo the previous query, but retrieve only the Employee ID, Employee Name and Job Title.*

     <details>
     <summary>Solution</summary>

    ```
    select EMP_ID,F_NAME,L_NAME, JOB_TITLE from EMPLOYEES E, JOBS J where E.JOB_ID = J.JOB_IDENT;
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/2D.png)

     </details>

5.  Problem:

    > *Redo the previous query, but specify the fully qualified column names with aliases in the SELECT clause.*

     <details>
     <summary>Solution</summary>

    ```
    select E.EMP_ID,E.F_NAME,E.L_NAME, J.JOB_TITLE from EMPLOYEES E, JOBS  J where E.JOB_ID = J.JOB_IDENT;
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/2E.png)

     </details>

<br>

# Solution Script

If you would like to run all the solution queries of the SQL problems of this lab with a script, download the script below. Import the script to mysql phpadmin interface and run. Follow [Hands-on Lab : Create tables using SQL scripts and Load data into tables](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week2/Create_and%20\_Load.md.html) on how to import a script to MYsql phpadmin interface and run it.

*   [MultipleTables_Solution_Script.sql](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/multipletables.sql)

<br>

<h3> Congratulations! You have completed this lab, and you are ready for the next topic. <h3/>

<br>

# Author(s)

[Lakshmi Holla](https://www.linkedin.com/in/lakshmi-holla-b39062149/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDB0201ENSkillsNetwork20127838-2021-01-01)

[Malika Singla](https://www.linkedin.com/in/malika-goyal-04798622/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDB0201ENSkillsNetwork20127838-2021-01-01)

## Changelog

| Date       | Version | Changed by                   | Change Description |
| ---------- | ------- | ---------------------------- | ------------------ |
| 2021-11-01 | 0.1     | Lakshmi Holla, Malika Singla | Initial Version    |

## <h3 align="center"> Â© IBM Corporation 2021. All rights reserved. <h3/>
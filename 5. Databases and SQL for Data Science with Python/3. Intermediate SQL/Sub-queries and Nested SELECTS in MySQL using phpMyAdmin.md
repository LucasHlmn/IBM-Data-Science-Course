<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0110EN-SkillsNetwork/labs/Lab%20-%20Create%20Tables%20and%20Load%20Data%20in%20MySQL%20using%20phpMyAdmin/images/IDSNlogo.png" width="200" height="200">

# Hands-on Lab : Sub-queries and Nested SELECTS in MySQL using phpMyAdmin

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

# 

## Objectives

After completing this lab you will be able to:

*   Write SQL queries that demonstrate the necessity of using sub-queries
*   Compose sub-queries in the where clause
*   Build Column Expressions (i.e. sub-query in place of a column)
*   Write Table Expressions (i.e. sub-query in place of a table)

In this lab, you will run through some SQL practice problems that will provide hands-on experience with nested SQL SELECT statements (also known as Sub-queries).

<br>

**How does a typical Nested SELECT statement syntax look?**

```
SELECT column_name [, column_name ]
FROM table1 [, table2 ]
WHERE column_name OPERATOR
   (SELECT column_name [, column_name ]
   FROM table1 [, table2 ]
   WHERE condition);
```

<br>

# Exercise:

1.  Problem:

    > *Execute a failing query (i.e. one which gives an error) to retrieve all employees records whose salary is lower than the average salary.*

     <details>
     <summary>Hint</summary>

    > Use the AVG aggregate function.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    select * 
    from EMPLOYEES 
    where salary < AVG(salary);
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/1.png)

     </details>

<br>

2.  Problem:

    > *Execute a working query using a sub-select to retrieve all employees records whose salary is lower than the average salary.*

     <details>
     <summary>Hint</summary>

    > Put AVG(SALARY) of the inner SELECT in comparison with SALARY of the outer SELECT.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    select EMP_ID, F_NAME, L_NAME, SALARY 
    from EMPLOYEES
    where SALARY < (select AVG(SALARY) 
                    from EMPLOYEES);
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/2.png)

     </details>

<br>

3.  Problem:

    > *Execute a failing query (i.e. one which gives an error) to retrieve all employees records with EMP_ID, SALARY and maximum salary as MAX_SALARY in every row.*

     <details>
     <summary>Hint</summary>

    > Use the MAX aggregate function.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    select EMP_ID, SALARY, MAX(SALARY) AS MAX_SALARY 
    from EMPLOYEES;		
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/3.png)

     </details>

<br>

4.  Problem:

    > *Execute a Column Expression that retrieves all employees records with EMP_ID, SALARY and maximum salary as MAX_SALARY in every row.*

     <details>
     <summary>Hint</summary>

    > Use the SELECT (which retrieves MAX(SALARY)) as a column of the other SELECT.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    select EMP_ID, SALARY, ( select MAX(SALARY) from EMPLOYEES ) AS MAX_SALARY 
    from EMPLOYEES;
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/4.png)

     </details>

<br>

5.  Problem:

    > *Execute a Table Expression for the EMPLOYEES table that excludes columns with sensitive employee data (i.e. does not include columns: SSN, B_DATE, SEX, ADDRESS, SALARY).*

     <details>
     <summary>Hint</summary>

    > Use a SELECT (which retrieves non-sensitive employee data) after FROM of the other SELECT.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    select * from ( select EMP_ID, F_NAME, L_NAME, DEP_ID from EMPLOYEES) AS EMP4ALL;
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/5.png)

     </details>

<br>

# Solution Script

If you would like to run all the solution queries of the SQL problems in this lab with a script, download the script below. Import the script to the mysql phpadmin interface  and run it. Follow [Hands-on Lab : Create tables using SQL scripts and Load data into tables](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week2/Create_and%20\_Load.md.html) on how to upload a script to mysql phpadmin.

*   [SubQueries_Solution_Script.sql](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/subqueries.sql)

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
<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0110EN-SkillsNetwork/labs/Lab%20-%20Create%20Tables%20and%20Load%20Data%20in%20MySQL%20using%20phpMyAdmin/images/IDSNlogo.png" width="200" height="200">

# Hands-on Lab: String Patterns, Sorting and Grouping in MySQL using phpMyAdmin

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

After completing this lab, you will be able to:

*   Simplify a SELECT statement by using string patterns, ranges, or sets of values
*   Sort the result set in either ascending or descending order and identify which column to use for the sorting order
*   Eliminate duplicates from a result set and further restrict a result set

Once the tables are  loaded open the sql editor to start executing the functions.

<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/queryeditor.png">

# Exercise 1: String Patterns

In this exercise, you will go through some SQL problems on String Patterns.

1.  Problem:

    > *Retrieve all employees whose address is in Elgin,IL.*

     <details>
     <summary>Hint</summary>

    > Use the LIKE operator to find similar strings.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT F_NAME , L_NAME
    FROM EMPLOYEES
    WHERE ADDRESS LIKE '%Elgin,IL%';
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/3A.png)

     </details>

<br>

2.  Problem:

    > *Retrieve all employees who were born during the 1970's.*

     <details>
     <summary>Hint</summary>

    > Use the LIKE operator to find similar strings.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT F_NAME , L_NAME
    FROM EMPLOYEES
    WHERE B_DATE LIKE '197%';
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/3B.png)

     </details>

<br>

3.  Problem:

    > *Retrieve all employees in department 5 whose salary is between 60000 and 70000.*

     <details>
     <summary>Hint</summary>

    > Use the keyword BETWEEN for this SQL problem.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT *
    FROM EMPLOYEES
    WHERE (SALARY BETWEEN 60000 AND 70000) AND DEP_ID = 5;
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/3C.png)

     </details>

<br>

# Exercise 2: Sorting

In this exercise, you will go through some SQL problems on Sorting.

1.  Problem:

    > *Retrieve a list of employees ordered by department ID.*

     <details>
     <summary>Hint</summary>

    > Use the ORDER BY clause for this SQL problem. By default, the ORDER BY clause sorts the records in ascending order.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT F_NAME, L_NAME, DEP_ID 
    FROM EMPLOYEES
    ORDER BY DEP_ID;
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/3E.png)

     </details>

<br>

2.  Problem:

    > *Retrieve a list of employees ordered in descending order by department ID and within each department ordered alphabetically in descending order by last name.*

     <details>
     <summary>Hint</summary>

    > Use the ORDER BY clause with DESC for this SQL problem.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT F_NAME, L_NAME, DEP_ID 
    FROM EMPLOYEES
    ORDER BY DEP_ID DESC, L_NAME DESC;
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/3F.png)

     </details>

<br>

3.  (Optional) Problem:

    > *In SQL problem 2 (Exercise 2 Problem 2), use department name instead of department ID. Retrieve a list of employees ordered by department name, and within each department ordered alphabetically in descending order by last name.*

     <details>
     <summary>Hint</summary>

    > Department name is in the DEPARTMENTS table. So your query will need to retrieve data from more than one table. DonÃ¢â‚¬â„¢t worry if you are not able to figure this SQL problem out. WeÃ¢â‚¬â„¢ll cover working with multiple tables in the lecture **Working with Multiple Tables**.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT D.DEP_NAME , E.F_NAME, E.L_NAME
    FROM EMPLOYEES as E, DEPARTMENTS as D
    WHERE E.DEP_ID = D.DEPT_ID_DEP
    ORDER BY D.DEP_NAME, E.L_NAME DESC;
    ```

    > In the SQL Query above, `D` and `E` are aliases for the table names. Once you define an alias like `D` in your query, you can simply write `D.COLUMN_NAME` rather than the full form `DEPARTMENTS.COLUMN_NAME`.

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/3G.png)

     </details>

<br>

# Exercise 3: Grouping

In this exercise, you will go through some SQL problems on Grouping.

**NOTE:** The SQL problems in this exercise involve usage of SQL Aggregate functions AVG and COUNT. COUNT has been covered earlier. AVG is a function that can be used to calculate the Average or Mean of all values of a specified column in the result set. For example, to retrieve the average salary for all employees in the EMPLOYEES table, issue the query: `SELECT AVG(SALARY) FROM EMPLOYEES;`. You will learn more about AVG and other aggregate functions later in the lecture **Built-in Database Functions**.

1.  Problem:

    > *For each department ID retrieve the number of employees in the department.*

     <details>
     <summary>Hint</summary>

    > Use COUNT(\*) to retrieve the total count of a column, and then GROUP BY.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT DEP_ID, COUNT(*)
    FROM EMPLOYEES
    GROUP BY DEP_ID;
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/3H.png)

     </details>

<br>

2.  Problem:

    > *For each department retrieve the number of employees in the department, and the average employee salary in the department..*

     <details>
     <summary>Hint</summary>

    > Use COUNT(\*) to retrieve the total count of a column, and AVG() function to compute average salaries, and then GROUP BY.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT DEP_ID, COUNT(*), AVG(SALARY)
    FROM EMPLOYEES
    GROUP BY DEP_ID;
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/3J.png)

     </details>

<br>

3.  Problem:

    > *Label the computed columns in the result set of SQL problem 2 (Exercise 3 Problem 2) as NUM_EMPLOYEES and AVG_SALARY.*

     <details>
     <summary>Hint</summary>

    > Use SQL Aliases: `column_name AS alias_name`.  For example, AVG(SALARY) AS "AVG_SALARY".

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT DEP_ID, COUNT(*) AS "NUM_EMPLOYEES", AVG(SALARY) AS "AVG_SALARY"
    FROM EMPLOYEES
    GROUP BY DEP_ID;
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/3K.png)

     </details>

<br>

4.  Problem:

    > *In SQL problem 3 (Exercise 3 Problem 3), order the result set by Average Salary..*

     <details>
     <summary>Hint</summary>

    > Use ORDER BY after the GROUP BY.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT DEP_ID, COUNT(*) AS "NUM_EMPLOYEES", AVG(SALARY) AS "AVG_SALARY"
    FROM EMPLOYEES
    GROUP BY DEP_ID
    ORDER BY AVG_SALARY;
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/3L.png)

     </details>

<br>

5.  Problem:

    > *In SQL problem 4 (Exercise 3 Problem 4), limit the result to departments with fewer than 4 employees.*

     <details>
     <summary>Hint</summary>

    > Use HAVING after the GROUP BY, and use the count() function in the HAVING clause instead of the column label.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT DEP_ID, COUNT(*) AS "NUM_EMPLOYEES", AVG(SALARY) AS "AVG_SALARY"
    FROM EMPLOYEES
    GROUP BY DEP_ID
    HAVING count(*) < 4
    ORDER BY AVG_SALARY;
    ```

     </details>

     <details>
     <summary>Output</summary>

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/3M.png)

     </details>

<br>

# Solution Script

If you would like to run all the solution queries of the SQL problems of this lab with a script, download the script below\.Import the script to phpadmin mysql interface and run. Follow [Hands-on Lab : Create tables using SQL scripts and Load data into tables](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week2/Create_and%20\_Load.md.html) on how to upload a script to phpmyadmin console and run it.

*   [StringPattern-Sorting-Grouping_Solution_Script.sql](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/StringPattern-Sorting-Grouping_Solution_Script.sql)

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
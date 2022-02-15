<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0110EN-SkillsNetwork/labs/Lab%20-%20Create%20Tables%20and%20Load%20Data%20in%20MySQL%20using%20phpMyAdmin/images/IDSNlogo.png" width="200" height="200">

# Hands-on Lab: Built-in functions - Aggregate, Scalar, String, Date and Time Functions in MySQL using phpMyAdmin

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

**Mysql_learners** database has been used in this lab.

# 

## Objectives

After completing this lab, you will be able to use phpMyAdmin with MySQL to:

*   Compose queries consting of built in functions and check the results.

# 

## Exercise

In this exercise through different tasks, you will learn how to create tables and load data in the MySQL database service using the phpMyAdmin graphical user interface (GUI) tool.

# 

### Task A: Create a database

1.  Go to **Terminal > New Terminal** to open a terminal from the side by side launched Cloud IDE.

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0110EN-SkillsNetwork/labs/Lab%20-%20Create%20Tables%20and%20Load%20Data%20in%20MySQL%20using%20phpMyAdmin/images/2.1.png)

<br>

2.  Start MySQL service session in the Cloud IDE using the command below in the terminal. Find your MySQL service session password from the highlighted location of the terminal shown in the image below. Note down your MySQL service session password because you may need to use it later in the lab.

    ```
    start_mysql
    ```

    {: codeblock}

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0110EN-SkillsNetwork/labs/Lab%20-%20Create%20Tables%20and%20Load%20Data%20in%20MySQL%20using%20phpMyAdmin/images/2.2.png)

<br>

3.  Copy your phpMyAdmin weblink from the highlighted location of the terminal shown in the image below. Past it into the address bar in a new tab of your web browser. This will open the phpMyAdmin tool.

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0110EN-SkillsNetwork/labs/Lab%20-%20Create%20Tables%20and%20Load%20Data%20in%20MySQL%20using%20phpMyAdmin/images/2.3.png)

<br>

4.  You will see the phpMyAdmin GUI tool.

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0110EN-SkillsNetwork/labs/Lab%20-%20Create%20Tables%20and%20Load%20Data%20in%20MySQL%20using%20phpMyAdmin/images/2.4.png)

<br>

5.  In the tree-view, click **New** to create a new empty database. Then enter **Mysql_Learners** as the name of the database and click **Create**.

    The encoding will be left as **utf8mb4\_0900\_ai_ci**. UTF-8 is the most commonly used character encoding for content or data.

    Proceed to Task B.

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/db1.png)

<br>

Compose and run the following queries in the textarea of the **SQL** page. Click **Go** to execute the queries and observe the the results.

**Note:** The solutions are provided at the end of this lab, but please try to compose the queries on your own before checking the solutions.

# Exercise 1: Create the Pet Rescue table

Rather than create the table manually by typing the DDL commands in the SQL editor, you will execute a script containing the create table command.

1.  Download the script file [PETRESCUE-CREATE.sql](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/PETSALE-CREATE.sql) <br>

**Note**: To download, just right-click on the link above and click on **Save As..** or **Save Link As...** depending on your browser. Save the file as a .sql file and not HTML.

2.  Next load the sql to your database using the Import option.

<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/loadpetrescue.png">

3.  Once the table is loaded open the sql editor to start executing the functions.

<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week3/images/queryeditor.png">

# Exercise 2: Aggregate Functions

**Query A1:** Enter a function that calculates the total cost of all animal rescues in the PETRESCUE table.

**Query A2:** Enter a function that displays the total cost of all animal rescues in the PETRESCUE table in a column called SUM_OF_COST.

**Query A3:** Enter a function that displays the maximum quantity of animals rescued.

**Query A4:** Enter a function that displays the average cost of animals rescued.

**Query A5:** Enter a function that displays the average cost of rescuing a dog.

# Exercise 3: Scalar and String Functions

**Query B1:** Enter a function that displays the rounded cost of each rescue.

**Query B2:** Enter a function that displays the length of each animal name.

**Query B3:** Enter a function that displays the animal name in each rescue in uppercase.

**Query B4:** Enter a function that displays the animal name in each rescue in uppercase without duplications.

**Query B5:** Enter a query that displays all the columns from the PETRESCUE table, where the animal(s) rescued are cats. Use **cat** in lower case in the query.

# Exercise 4: Date and Time Functions

**Query C1:** Enter a function that displays the day of the month when cats have been rescued.

**Query C2:** Enter a function that displays the number of rescues on the 5<sup>th</sup> month.

**Query C3:** Enter a function that displays the number of rescues on the 14<sup>th</sup> day of the month.

**Query C4:** Animals rescued should see the vet within three days of arrivals. Enter a function that displays the third day from each rescue.

**Query C5:** Enter a function that displays the length of time the animals have been rescued; the difference between todayÃ¢â‚¬â„¢s date and the rescue date.

# Lab Solutions

# Exercise 2 Solutions: Aggregate Functions

\*\*Query A1:\*\*Ã‚ Enter a function that calculates the total cost of all animal rescues in the PETRESCUE table.

`select SUM(COST) from PETRESCUE;`

\*\*Query A2:\*\*Ã‚ Enter a function that displays the total cost of all animal rescues in the PETRESCUE table in a column called SUM_OF_COST.

`select SUM(COST) AS SUM_OF_COST from PETRESCUE;`

\*\*Query A3:\*\*Ã‚ Enter a function that displays the maximum quantity of animals rescued.

`select MAX(QUANTITY) from PETRESCUE;`

**Query A4:** Enter a function that displays the average cost of animals rescued.

`select AVG(COST) from PETRESCUE;`

**Query A5:** Enter a function that displays the average cost of rescuing a dog.
*Hint - Bear in my the cost of rescuing one dog on day, is different from another day. So you will have to use and average of averages.*

`select AVG(COST/QUANTITY) from PETRESCUE where ANIMAL = 'Dog';`

# Exercise 3 Solutions: Scalar and String Functions

\*\*Query B1:\*\*Ã‚ <a id="_Hlk38373248"></a>Enter a function that displays the rounded cost of each rescue.

`select ROUND(COST) from PETRESCUE;`

**Query B2:** <a id="_Hlk38373308"></a>Enter a function that displays the length of each animal name.

`select LENGTH(ANIMAL) from PETRESCUE;`

**Query B3:** <a id="_Hlk38373425"></a>Enter a function that displays the animal name in each rescue in uppercase.

`select UCASE(ANIMAL) from PETRESCUE;`

**Query B4:** Enter a function that displays the animal name in each rescue in uppercase without duplications.

`select DISTINCT(UCASE(ANIMAL)) from PETRESCUE;`

**Query B5:** Enter a query that displays all the columns from the PETRESCUE table, where the animal(s) rescued are cats. Use **cat** in lower case in the query.

`select * from PETRESCUE where LCASE(ANIMAL) = 'cat';`

# Exercise 4 Solutions: Date and Time Functions

**Query C1:** Enter a function that displays the day of the month when cats have been rescued.

`select DAY(RESCUEDATE) from PETRESCUE where ANIMAL = 'Cat';`

**Query C2:** Enter a function that displays the number of rescues on the 5<sup>th</sup> month.

`select SUM(QUANTITY) from PETRESCUE where MONTH(RESCUEDATE)='05';`

**Query C3:** Enter a function that displays the number of rescues on the 14<sup>th</sup> day of the month.

`select SUM(QUANTITY) from PETRESCUE where DAY(RESCUEDATE)='14';`

**Query C4:** Animals rescued should see the vet within three days of arrivals. Enter a function that displays the third day from each rescue.

`select DATE_add(RESCUEDATE, INTERVAL 3 DAY) from PETRESCUE;`

**Query C5:** Enter a function that displays the length of time the animals have been rescued; the difference between todayÃ¢â‚¬â„¢s date and the recue date.

`select DATEDIFF(CURRENT_TIMESTAMP,RESCUEDATE) from PETRESCUE;`

# Summary

You can now compose and run queries, check results and view the logs. You will use these skills in later labs.

# Author(s)

[Lakshmi Holla](https://www.linkedin.com/in/lakshmi-holla-b39062149/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDB0201ENSkillsNetwork20127838-2021-01-01)

[Malika Singla](https://www.linkedin.com/in/malika-goyal-04798622/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDB0201ENSkillsNetwork20127838-2021-01-01)

## Changelog

| Date       | Version | Changed by                   | Change Description |
| ---------- | ------- | ---------------------------- | ------------------ |
| 2021-11-01 | 0.1     | Lakshmi Holla, Malika Singla | Initial Version    |

## <h3 align="center"> Â© IBM Corporation 2021. All rights reserved. <h3/>
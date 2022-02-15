<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-DB0110EN-SkillsNetwork/labs/Lab%20-%20Create%20Tables%20and%20Load%20Data%20in%20MySQL%20using%20phpMyAdmin/images/IDSNlogo.png" width="200" height="200">

# Hands-on Lab: Create Tables using SQL Scripts and Load Data into Tables in MySQL using phpMyAdmin

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

After completing this lab, you will be able to use phpMyAdmin with MySQL to:

*   Create a database.
*   Create tables using SQL scripts
*   Load data into tables

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

5.  In the tree-view, click **New** to create a new empty database. Then enter **HR** as the name of the database and click **Create**.

    The encoding will be left as **utf8mb4\_0900\_ai_ci**. UTF-8 is the most commonly used character encoding for content or data.

    Proceed to Task B.

    ![image](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week2/images/HRdb.png)

<br>

## Exercise 1: Create tables using SQL scripts

In this exercise, you will learn how to execute a script containing the CREATE TABLE commands for all the tables rather than create each table manually by typing the DDL commands in the SQL editor.

1.  Download the script file to your computer:

    *   [HR_Database_Create_Tables_Script.sql](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week2/HR_Database_Create_Tables_Script.sql)

<p>

*   Select the HR database. Later click on the Import tab.

*   Click on **choose file**. Browse for the file and upload it .

*   Later  scroll down and click on **Go**.

<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week2/images/import.png">

*   The script then gets imported successfully.

<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week2/images/importsuccess.png">

*   Click on any of the tables and you will see its Table Definition (that is, its list of columns, data types, etc).

 <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week2/images/tabledef.png">

## Exercise 2: Load data into tables

In this exercise, you will learn how data can be loaded into Db2. You could manually insert each row into the table one by one, but that would take a long time. Instead, Db2 (and almost every other database) allows you to load data from .CSV files.

The steps below explain the process of loading data into the tables you created earlier in exercise 1.

1.  Download the 5 .csv files below to your local computer:

    *   [Departments.csv](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/datasets/HR_Database/Departments.csv)
    *   [Employees.csv](data/Employees_updated.csv)
    *   [Jobs.csv](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/datasets/HR_Database/Jobs.csv)
    *   [Locations.csv](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/datasets/HR_Database/Locations.csv)
    *   [JobsHistory.csv](data/JobsHistory.csv)

<p>

To load each table do the following steps.

*   Select each table .

*   Click on Import tab.

*   Select the **csv** file and click on **Go** to load the csv file.

<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week2/images/loadtable.png">

Once the tables are loaded , you will get a message that the records are inserted successfully.

<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week2/images/insertsuccess.png">

Further you can click on browse and view the data of each table.

<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/MySQL/week2/images/browse.png">

<h3> Congratulations! You have completed this lab, and you are ready for the next topic. <h3/>

# Author(s)

[Lakshmi Holla](https://www.linkedin.com/in/lakshmi-holla-b39062149/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDB0201ENSkillsNetwork20127838-2021-01-01)

[Malika Singla](https://www.linkedin.com/in/malika-goyal-04798622/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDB0201ENSkillsNetwork20127838-2021-01-01)

## Changelog

| Date       | Version | Changed by                   | Change Description |
| ---------- | ------- | ---------------------------- | ------------------ |
| 2021-11-01 | 0.1     | Lakshmi Holla, Malika Singla | Initial Version    |

## <h3 align="center"> Â© IBM Corporation 2021. All rights reserved. <h3/>
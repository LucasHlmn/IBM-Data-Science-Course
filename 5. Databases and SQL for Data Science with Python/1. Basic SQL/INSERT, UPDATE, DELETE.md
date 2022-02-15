<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20INSERT%20-%20UPDATE%20-%20DELETE/images/IDSNlogo.png" width="200" height="200"> 

# Hands-on Lab : INSERT, UPDATE, DELETE

**Estimated time needed:** 20 minutes

In this lab, you will learn some commonly used DML (Data Manipulation Language) statements of SQL other than SELECT. First, you will learn the INSERT statement, which is used to insert new rows into a table. Next, you will learn the UPDATE statement which is used to update the data in existing rows in the table. Lastly, you will learn the DELETE statement which is used to remove rows from a table.

<br>

**How does the syntax of an INSERT statement look?**

```
INSERT INTO table_name (column1, column2, ... )
VALUES (value1, value2, ... )
;
```

{: codeblock}

<br>

**How does the syntax of an UPDATE statement look?**

```
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition
;
```

{: codeblock}

<br>

**How does the syntax of a DELETE statement look?**

```
DELETE FROM table_name
WHERE condition
;
```

{: codeblock}

<br>

# 

## Software Used in this Lab

In this lab, you will use <a href="https://github.com/simonw/datasette?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDB0201ENSkillsNetwork20127838-2021-01-01" target="_blank">Datasette </a>, an open source multi-tool for exploring and publishing data.

<br>

## Database Used in this Lab

The dataset used in this lab is an internal database.

<br>

## Objectives

After completing this lab, you will be able to:

*   Insert new rows into a table
*   Update data in existing rows of the table
*   Remove rows from a table

<br>

# Exploring the Database

Let us first explore the **Instructors** database using the **Datasette** tool:

1.  If the first statement listed below is not already in the Datasette textbox on the right, then copy the code below by clicking on the little copy button on the bottom right of the codeblock below and then paste it into the textbox of the Datasette tool using either **Ctrl+V** or right-click in the text box and choose **Paste**.

    ```
    SELECT * FROM Instructor;
    ```

    {: codeblock}

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20INSERT%20-%20UPDATE%20-%20DELETE/images/ExploringDB.1.png" width="520" height="180">

2.  Click **Submit Query**.

3.  Now you can scroll down the table and explore all the columns and rows of the **Instructor** table to get an overall idea of the table contents.

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20INSERT%20-%20UPDATE%20-%20DELETE/images/ExploringDB.2.png" width="520" height="170">

4.  These are the column attribute descriptions from the **Instructor** table:

    ```
    Instructor (
        ins_id:     unique identification number of the instructors,    
        lastname:   last name of the instructors,
        firstname:  first name of the instructors,
        city:       name of the cities where instructors are located,
        country:    two-letter country code of the countries where instructors are located
    )
    ```

    {: codeblock}

<br>

# Exercise 1: INSERT

In this exercise, you will first go through some examples of using INSERT in queries and then solve some exercise problems by using it.

# 

## Task A: Example exercises on INSERT

Let us go through some examples of INSERT related queries:

<br>

1.  In this example, suppose we want to insert a new single row into the **Instructor** table.

    1.  Problem:

        > *Insert a new instructor record with id 4 for Sandip Saha who lives in Edmonton, CA into the "Instructor" table.*

    2.  Solution:

        ```
        INSERT INTO Instructor(ins_id, lastname, firstname, city, country)
        VALUES(4, 'Saha', 'Sandip', 'Edmonton', 'CA');
        ```

        {: codeblock}

     <br>

    3.  Copy the solution code above by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

     <br>

    4.  Copy the code below by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

        ```
        SELECT * FROM Instructor;
        ```

        {: codeblock}

     <br>

    5.  Your output resultset should look like the image below:

         <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20INSERT%20-%20UPDATE%20-%20DELETE/images/1.A.1.5.png" width="520" height="400">

<br>
<br>

2.  In this example, suppose we want to insert some new multiple rows into the **Instructor** table.

    1.  Problem:

        > *Insert two new instructor records into the "Instructor" table. First record with id 5 for John Doe who lives in Sydney, AU. Second record with id 6 for Jane Doe who lives in Dhaka, BD.*

    2.  Solution:

        ```
        INSERT INTO Instructor(ins_id, lastname, firstname, city, country)
        VALUES(5, 'Doe', 'John', 'Sydney', 'AU'), (6, 'Doe', 'Jane', 'Dhaka', 'BD');
        ```

        {: codeblock}

     <br>

    3.  Copy the solution code above by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

     <br>

    4.  Copy the code below by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

        ```
        SELECT * FROM Instructor;
        ```

        {: codeblock}

     <br>

    5.  Your output resultset should look like the image below:

         <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20INSERT%20-%20UPDATE%20-%20DELETE/images/1.A.2.5.png" width="520" height="400">

<br>

# 

## Task B: Practice exercises on INSERT

Now, let us practice creating and running some INSERT related queries.

<br>

1.  Problem:

    > *Insert a new instructor record with id 7 for Antonio Cangiano who lives in Vancouver, CA into the "Instructor" table.*

     <details>
     <summary>Hint</summary>

    > Follow example 1 of the INSERT exercise.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    INSERT INTO Instructor(ins_id, lastname, firstname, city, country)
    VALUES(7, 'Cangiano', 'Antonio', 'Vancouver', 'CA');

    SELECT * FROM Instructor;
    ```

    {: codeblock}

     </details>

     <details>
     <summary>Output</summary>

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20INSERT%20-%20UPDATE%20-%20DELETE/images/1.B.1.O.png" width="520" height="400">

     </details>

<br>

2.  Problem:

    > *Insert two new instructor records into the "Instructor" table. First record with id 8 for Steve Ryan who lives in Barlby, GB. Second record with id 9 for Ramesh Sannareddy who lives in Hyderabad, IN.*

     <details>
     <summary>Hint</summary>

    > Follow example 2 of the INSERT exercise.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    INSERT INTO Instructor(ins_id, lastname, firstname, city, country)
    VALUES(8, 'Ryan', 'Steve', 'Barlby', 'GB'), (9, 'Sannareddy', 'Ramesh', 'Hyderabad', 'IN');

    SELECT * FROM Instructor;
    ```

    {: codeblock}

     </details>

     <details>
     <summary>Output</summary>

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20INSERT%20-%20UPDATE%20-%20DELETE/images/1.B.2.O.png" width="520" height="400">

     </details>

<br>

# Exercise 2: UPDATE

In this exercise, you will first go through some examples of using UPDATE in queries and then solve some exercise problems by using it.

# 

## Task A: Example exercises on UPDATE

Let us go through some examples of UPDATE related queries:

<br>

1.  In this example, we want to update one column of an existing row of the table.

    1.  Problem:

        > *Update the city for Sandip to Toronto.*

    2.  Solution:

        ```
        UPDATE Instructor 
        SET city='Toronto' 
        WHERE firstname="Sandip";
        ```

        {: codeblock}

     <br>

    3.  Copy the solution code above by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

     <br>

    4.  Copy the code below by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

        ```
        SELECT * FROM Instructor;
        ```

        {: codeblock}

     <br>

    5.  Your output resultset should look like the image below:

         <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20INSERT%20-%20UPDATE%20-%20DELETE/images/2.A.1.5.png" width="520" height="400">

<br>
<br>

2.  In this example, we want to update multiple columns of an existing row of the table.

    1.  Problem:

        > *Update the city and country for Doe with id 5 to Dubai and AE respectively.*

    2.  Solution:

        ```
        UPDATE Instructor 
        SET city='Dubai', country='AE' 
        WHERE ins_id=5;
        ```

        {: codeblock}

     <br>

    3.  Copy the solution code above by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

     <br>

    4.  Copy the code below by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

        ```
        SELECT * FROM Instructor;
        ```

        {: codeblock}

     <br>

    5.  Your output resultset should look like the image below:

         <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20INSERT%20-%20UPDATE%20-%20DELETE/images/2.A.2.5.png" width="520" height="400">

<br>

# 

## Task B: Practice exercises on UPDATE

Now, let us practice creating and running some UPDATE related queries.

<br>

1.  Problem:

    > *Update the city of the instructor record to Markham whose id is 1.*

     <details>
     <summary>Hint</summary>

    > Follow example 1 of the UPDATE exercise.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    UPDATE Instructor 
    SET city='Markham' 
    WHERE ins_id=1;

    SELECT * FROM Instructor;
    ```

    {: codeblock}

     </details>

     <details>
     <summary>Output</summary>

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20INSERT%20-%20UPDATE%20-%20DELETE/images/2.B.1.O.png" width="520" height="400">

     </details>

<br>

2.  Problem:

    > *Update the city and country for Sandip with id 4 to Dhaka and BD respectively.*

     <details>
     <summary>Hint</summary>

    > Follow example 2 of the UPDATE exercise.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    UPDATE Instructor 
    SET city='Dhaka', country='BD' 
    WHERE ins_id=4;

    SELECT * FROM Instructor;
    ```

    {: codeblock}

     </details>

     <details>
     <summary>Output</summary>

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20INSERT%20-%20UPDATE%20-%20DELETE/images/2.B.2.O.png" width="520" height="400">

     </details>

<br>

# Exercise 3: DELETE

In this exercise, you will first go through an example of using DELETE in a query and then solve an exercise problem by using it.

# 

## Task A: Example exercise on DELETE

Let us go through an example of a DELETE related query:

<br>

1.  In this example, we want to remove a row from the table.

    1.  Problem:

        > *Remove the instructor record of Doe whose id is 6.*

    2.  Solution:

        ```
        DELETE FROM instructor
        WHERE ins_id = 6;
        ```

        {: codeblock}

     <br>

    3.  Copy the solution code above by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of **Custom SQL query** of the Datasette tool. Then click **Submit query**.

     <br>

    4.  Copy the code below by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

        ```
        SELECT * FROM Instructor;
        ```

        {: codeblock}

     <br>

    5.  Your output resultset should look like the image below:

         <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20INSERT%20-%20UPDATE%20-%20DELETE/images/3.A.1.5.png" width="520" height="400">

<br>

# 

## Task B: Practice exercise on DELETE

Now, let us practice creating and running a DELETE related query.

<br>

1.  Problem:

    > *Remove the instructor record of Hima.*

     <details>
     <summary>Hint</summary>

    > Follow example 1 of the DELETE exercise.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    DELETE FROM instructor
    WHERE firstname = 'Hima';

    SELECT * FROM Instructor;
    ```

    {: codeblock}

     </details>

     <details>
     <summary>Output</summary>

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20INSERT%20-%20UPDATE%20-%20DELETE/images/3.B.1.O.png" width="520" height="400">

     </details>

<br>

# 

<h3> Congratulations! You have completed this Lab. <h3/>

<br>

## Author(s)

*   <a href="https://www.linkedin.com/in/sandipsahajoy/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDB0201ENSkillsNetwork20127838-2021-01-01" target="_blank">Sandip Saha Joy</a>

<br>

## Other Contributor(s)

*

<br>

## Changelog

| Date       | Version | Changed by      | Change Description      |
| ---------- | ------- | --------------- | ----------------------- |
| 2020-12-23 | 1.1     | Steve Ryan      | ID Review               |
| 2020-11-30 | 1.0     | Sandip Saha Joy | Initial version created |

<br>

## <h3 align="center"> Â© IBM Corporation 2020. All rights reserved. <h3/>
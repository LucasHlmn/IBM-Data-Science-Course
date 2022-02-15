<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20Basics%20of%20SQL%20SELECT%20Statement/images/IDSNlogo.png" width="200" height="200"> 

# Hands-on Lab : Basics of SQL SELECT Statement

**Estimated time needed:** 20 minutes

In this lab, you will learn one of the most commonly used statements of SQL (Structured Query Language), the SELECT statement. The SELECT statement is used to select data from a database.

<br>

**How does the syntax of a SELECT statement look?**

```
SELECT column1, column2, ...
FROM table_name
WHERE condition
;
```

{: codeblock}

<br>

**What do the keywords / clauses of a SQL statement shown above do?**

*   **FROM**: Specifies from which table to get the data. The clause can include optional JOIN subclauses to specify the rules for joining tables.
*   \[Optional Clause] **WHERE** : Specifies which rows to retrieve.

<br>

**Why is there a semicolon after the SQL statements?**

*   Some database systems require a semicolon at the end of each SQL statement for execution. It is a standard way to separate one SQL statement from another which allows more than one SQL statement to be executed in the same call to the server. So, it is good practice to use a semicolon at the end of each SQL statement.

<br>

# 

## Software Used in this Lab

In this lab, you will use <a href="https://github.com/simonw/datasette?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDB0201ENSkillsNetwork20127838-2021-01-01" target="_blank">Datasette </a>, an open source multi-tool for exploring and publishing data.

<br>

## Database Used in this Lab

The database used in this lab comes from the following dataset source: <a href="https://data.sfgov.org/Culture-and-Recreation/Film-Locations-in-San-Francisco/yitu-d5am?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDB0201ENSkillsNetwork20127838-2021-01-01" target="_blank">Film Locations in San Francisco</a> under a <a href="https://opendatacommons.org/licenses/pddl/1-0/?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDB0201ENSkillsNetwork20127838-2021-01-01" target="_blank">PDDL: Public Domain Dedication and License</a>.

<br>

## Objectives

After completing this lab, you will be able to:

*   Query a database
*   Retrieve data records from one or more tables of a database as resultset according to the criteria you specify

<br>

# Task A: Exploring the Database

Let us first explore the **SanFranciscoFilmLocations** database using the **Datasette** tool:

1.  If the first statement listed below is not already in the Datasette textbox on the right, then copy the code below by clicking on the little copy button on the bottom right of the codeblock below and then paste it into the textbox of the Datasette tool using either **Ctrl+V** or right-click in the text box and choose **Paste**.

    ```
    SELECT * FROM FilmLocations;
    ```

    {: codeblock}

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20Basics%20of%20SQL%20SELECT%20Statement/images/A.1.png" width="520" height="180">

2.  Click **Submit Query**.

3.  Now you can scroll down the table and explore all the columns and rows of the **FilmLocations** table to get an overall idea of the table contents.

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20Basics%20of%20SQL%20SELECT%20Statement/images/A.2.png" width="520" height="400">

4.  These are the column attribute descriptions from the **FilmLocations** table:

    ```
    FilmLocations(
        Title:              titles of the films, 
        ReleaseYear:        time of public release of the films, 
        Locations:          locations of San Francisco where the films were shot, 
        FunFacts:           funny facts about the filming locations, 
        ProductionCompany:  companies who produced the films, 
        Distributor:        companies who distributed the films, 
        Director:           people who directed the films, 
        Writer:             people who wrote the films, 
        Actor1:             person 1 who acted in the films, 
        Actor2:             person 2 who acted in the films, 
        Actor3:             person 3 who acted in the films
    )
    ```

    {: codeblock}

<br>

# Task B: Example exercises on SELECT statement

Now let us go through some examples of SELECT queries:

<br>

1.  In this example, suppose we want to retrieve details of all the films from the "FilmLocations" table. The details of each film record should contain all the film columns.

    1.  Problem:

        > *Retrieve all records with all columns from the "FilmLocations" table.*

     <br>

    2.  Solution:

        ```
        SELECT * FROM FilmLocations;
        ```

        {: codeblock}

     <br>

    3.  Copy the solution code above by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

         <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20Basics%20of%20SQL%20SELECT%20Statement/images/B.1.3.png" width="520" height="180">

     <br>

    4.  Your output resultset should match like below:

         <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20Basics%20of%20SQL%20SELECT%20Statement/images/B.1.4.png" width="520" height="400">

<br>

2.  In this example, now we want to retrieve selective details of all the film records. Let us retrieve the names of all the films along with director names and writer names.

    1.  Problem:

        > *Retrieve the names of all films with director names and writer names.*

     <br>

    2.  Solution:

        ```
        SELECT Title, Director, Writer FROM FilmLocations;
        ```

        {: codeblock}

     <br>

    3.  Copy the solution code above by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

         <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20Basics%20of%20SQL%20SELECT%20Statement/images/B.2.3.png" width="520" height="180">

     <br>

    4.  Your output resultset should match like below:

         <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20Basics%20of%20SQL%20SELECT%20Statement/images/B.2.4.png" width="520" height="400">

<br>

3.  In this example, we want to retrieve film names along with filming locations and release years. But we also want to restrict the output resultset so that we can retrieve only the film records released in 2001 and onwards (release years after 2001 including 2001).

    1.  Problem:

        > *Retrieve the names of all films released in the 21st century and onwards (release years after 2001 including 2001), along with filming locations and release years.*

     <br>

    2.  Solution:

        ```
        SELECT Title, ReleaseYear, Locations FROM FilmLocations WHERE ReleaseYear>=2001;
        ```

        {: codeblock}

     <br>

    3.  Copy the solution code above by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

         <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20Basics%20of%20SQL%20SELECT%20Statement/images/B.3.3.png" width="520" height="180">

     <br>

    4.  Your output resultset should match like below:

         <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20Basics%20of%20SQL%20SELECT%20Statement/images/B.3.4.png" width="520" height="400">

<br>

# Task C: Practice exercises on SELECT statement

Finally, let us practice creating and running some SELECT queries.

<br>

1.  Problem:

    > *Retrieve the fun facts and filming locations of all films.*

     <details>
     <summary>Click here for Hint</summary>

    > Follow example 2 of SELECT where records have been retrieved containing details of some particular columns.

     </details>

     <details>
     <summary>Click here for Solution</summary>

    ```
    SELECT Locations, FunFacts FROM FilmLocations;
    ```

    {: codeblock}

     </details>

     <details>
     <summary>Click here for Output</summary>

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20Basics%20of%20SQL%20SELECT%20Statement/images/C.1.O.png" width="520" height="400">

     </details>

<br>

2.  Problem:

    > *Retrieve the names of all films released in the 20th century and before (release years before 2000 including 2000) that, along with filming locations and release years.*

     <details>
     <summary>Click here for Hint</summary>

    > Follow example 3 of SELECT where we restricted the output resultset so that we can retrieve only the film records with certain release years. Use WHERE clause comparsion operator `<=` which means **"Less than or equal to"**.

     </details>

     <details>
     <summary>Click here for Solution</summary>

    ```
    SELECT Title, ReleaseYear, Locations FROM FilmLocations WHERE ReleaseYear<=2000;
    ```

    {: codeblock}

     </details>

     <details>
     <summary>Click here for Output</summary>

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20Basics%20of%20SQL%20SELECT%20Statement/images/C.2.O.png" width="520" height="400">

     </details>

<br>

3.  Problem:

    > *Retrieve the names, production company names, filming locations, and release years of the films which are not written by James Cameron.*

     <details>
     <summary>Click here for Hint</summary>

    > Use WHERE clause comparsion operator `<>` which means **"Not equal to"**.

     </details>

     <details>
     <summary>Click here for Solution</summary>

    ```
    SELECT Title, ProductionCompany, Locations, ReleaseYear FROM FilmLocations WHERE Writer<>"James Cameron";
    ```

    {: codeblock}

     </details>

     <details>
     <summary>Click here for Output</summary>

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20Basics%20of%20SQL%20SELECT%20Statement/images/C.3.O.png" width="520" height="400">

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
| 2020-11-23 | 1.1     | Steve Ryan      | ID Review               |
| 2020-11-20 | 1.0     | Sandip Saha Joy | Initial version created |

<br>

## <h3 align="center"> Â© IBM Corporation 2020. All rights reserved. <h3/>
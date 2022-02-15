<img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/IDSNlogo.png" width="200" height="200"> 

# Hands-on Lab : COUNT, DISTINCT, LIMIT

**Estimated time needed:** 35 minutes

In this lab, you will learn a few useful expressions that are used with SELECT statements. First, you will learn COUNT, which is an aggregate function that retrieves the number of rows that matches the query criteria. Next, you will learn DISTINCT, which is used to remove duplicate values from a specified result set and only return the unique values. Lastly, you will learn LIMIT, which is used for restricting the number of rows retrieved from the table.

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

*   Retrieve the number of rows that match a query criteria
*   Remove duplicate values from a result set and return the unique values
*   Restrict the number of rows retrieved from a table

<br>

# Exploring the Database

Let us first explore the **SanFranciscoFilmLocations** database using the **Datasette** tool:

1.  If the first statement listed below is not already in the Datasette textbox on the right, then copy the code below by clicking on the little copy button on the bottom right of the codeblock below and then paste it into the textbox of the Datasette tool using either **Ctrl+V** or right-click in the text box and choose **Paste**.

    ```
    SELECT * FROM FilmLocations;
    ```

    {: codeblock}

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/ExploringDB.1.png" width="520" height="180">

2.  Click **Submit Query**.

3.  Now you can scroll down the table and explore all the columns and rows of the **FilmLocations** table to get an overall idea of the table.

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/ExploringDB.2.png" width="520" height="400">

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

# Exercise 1: COUNT

In this exercise, you will first go through some examples of using COUNT in queries and then solve some exercise problems by using it.

# 

## Task A: Example exercises on COUNT

Let us go through some examples of COUNT related queries:

<br>

1.  In this example, suppose we want to count the number of records or rows of the "FilmLocations" table.

    1.  Problem:

        > *Retrieve the number of rows from the "FilmLocations" table.*

    2.  Solution:

        ```
        SELECT COUNT(*) FROM FilmLocations;
        ```

        {: codeblock}

     <br>

    3.  Copy the solution code above by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

     <br>

    4.  Your output resultset should look like the image below:

         <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/1.A.1.4.png" width="520" height="400">

<br>
<br>

2.  In this example, now we want to count the number of locations of the films. But we also want to restrict the output resultset in such a way that we only retrieve the number of locations of the films written by a certain writer.

    1.  Problem:

        > *Retrieve the number of locations of the films which are written by James Cameron.*

    2.  Solution:

        ```
        SELECT COUNT(Locations) FROM FilmLocations WHERE Writer="James Cameron";
        ```

        {: codeblock}

     <br>

    3.  Copy the solution code above by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

     <br>

    4.  Your output resultset should look like the image below:

         <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/1.A.2.4.png" width="520" height="400">

# 

## Task B: Practice exercises on COUNT

Now, let us practice creating and running some COUNT related queries.

<br>

1.  Problem:

    > *Retrieve the number of locations of the films which are directed by Woody Allen.*

     <details>
     <summary>Hint</summary>

    > Follow example 2 of the COUNT exercise. Use the WHERE clause comparison operator `=` which means **"Equal to"**.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT COUNT(Locations) FROM FilmLocations WHERE Director="Woody Allen";
    ```

    {: codeblock}

     </details>

     <details>
     <summary>Output</summary>

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/1.B.1.O.png" width="520" height="400">

     </details>

<br>

2.  Problem:

    > *Retrieve the number of films shot at Russian Hill.*

     <details>
     <summary>Hint</summary>

    > Follow example 2 of the COUNT exercise. Use the WHERE clause comparison operator `=` which means **"Equal to"**.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT Count(Title) FROM FilmLocations WHERE Locations="Russian Hill";
    ```

    {: codeblock}

     </details>

     <details>
     <summary>Output</summary>

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/1.B.2.O.png" width="520" height="400">

     </details>

<br>

3.  Problem:

    > *Retrieve the number of rows having a release year older than 1950 from the "FilmLocations" table.*

     <details>
     <summary>Hint</summary>

    > Follow example 1 of the COUNT exercise. Use the WHERE clause comparison operator `<` which means **"Less than"**.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT Count(*) FROM FilmLocations WHERE ReleaseYear<1950;
    ```

    {: codeblock}

     </details>

     <details>
     <summary>Output</summary>

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/1.B.3.O.png" width="520" height="400">

     </details>

<br>

# Exercise 2: DISTINCT

In this exercise, you will first go through some examples of using DISTINCT in queries, and then solve some exercise problems by using it.

# 

## Task A: Example exercises of DISTINCT

Let us go through some examples of DISTINCT related queries:

<br>

1.  In this example, we want to retrieve the title of all films in the table in such a way that duplicates will be discarded in the output resultset.

    1.  Problem:

        > *Retrieve the name of all films without any repeated titles.*

    2.  Solution:

        ```
        SELECT DISTINCT Title FROM FilmLocations;
        ```

        {: codeblock}

     <br>

    3.  Copy the solution code above by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

     <br>

    4.  Your output resultset should look like the image below:

         <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/2.A.1.4.png" width="520" height="400">

<br>
<br>

2.  In this example, we want to retrieve the count of release years of the films produced by a specific company in such a way that duplicate release years of those films will be discarded in the count.

    1.  Problem:

        > *Retrieve the number of release years of the films distinctly, produced by Warner Bros. Pictures.*

    2.  Solution:

        ```
        SELECT COUNT(DISTINCT ReleaseYear) FROM FilmLocations WHERE ProductionCompany="Warner Bros. Pictures";
        ```

        {: codeblock}

     <br>

    3.  Copy the solution code above by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

     <br>

    4.  Your output resultset should look like the image below:

         <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/2.A.2.4.png" width="520" height="400">

# 

## Task B: Practice exercises on DISTINCT

Now, let us practice creating and running some DISTINCT related queries.

<br>

1.  Problem:

    > *Retrieve the name of all unique films released in the 21st century and onwards, along with their release years.*

     <details>
     <summary>Hint</summary>

    > Follow example 1 of DISTINCT. Use WHERE clause comparsion operator `>=` which means **"Greater than or equal to"**.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT DISTINCT Title, ReleaseYear FROM FilmLocations WHERE ReleaseYear>=2001;
    ```

    {: codeblock}

     </details>

     <details>
     <summary>Output</summary>

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/2.B.1.O.png" width="520" height="400">

     </details>

<br>

2.  Problem:

    > *Retrieve the names of all the directors and their distinct films shot at City Hall.*

     <details>
     <summary>Hint</summary>

    > Follow example 1 of DISTINCT. Use WHERE clause comparsion operator `=` which means **"Equal to"**.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT DISTINCT Title, Director FROM FilmLocations WHERE Locations="City Hall";
    ```

    {: codeblock}

     </details>

     <details>
     <summary>Output</summary>

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/2.B.2.O.png" width="520" height="400">

     </details>

<br>

3.  Problem:

    > *Retrieve the number of distributors distinctly who distributed films acted by Clint Eastwood as 1st actor.*

     <details>
     <summary>Hint</summary>

    > Follow example 2 of DISTINCT. Use WHERE clause comparsion operator `=` which means **"Equal to"**.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT COUNT(DISTINCT Distributor) FROM FilmLocations WHERE Actor1="Clint Eastwood";
    ```

    {: codeblock}

     </details>

     <details>
     <summary>Output</summary>

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/2.B.3.O.png" width="520" height="400">

     </details>

<br>

# Exercise 3: LIMIT

In this exercise, you will first go through some examples of using LIMIT in queries and then solve some exercise by using it.

# 

## Task A: Example exercises of LIMIT

Let us go through some examples of LIMIT related queries:

<br>

1.  In this example, let us retrieve a specific number of rows from the top of the table in such a way that rows other than those are not in the output resultset.

    1.  Problem:

        > *Retrieve the first 25 rows from the "FilmLocations" table.*

    2.  Solution:

        ```
        SELECT * FROM FilmLocations LIMIT 25;
        ```

        {: codeblock}

     <br>

    3.  Copy the solution code above by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

     <br>

    4.  Your output resultset should look like the image below:

         <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/3.A.1.4.png" width="520" height="400">

<br>
<br>

2.  In this example, let us take the first example to a more advanced level. Now we want to retrieve a specific number of rows from the table, but thid time, not from the top of the table. This time we want to retrieve a specific number of rows starting from a specific row in the table.

    1.  Problem:

        > *Retrieve the first 15 rows from the "FilmLocations" table starting from row 11.*

    2.  Solution:

        ```
        SELECT * FROM FilmLocations LIMIT 15 OFFSET 10;
        ```

        {: codeblock}

     <br>

    3.  Copy the solution code above by clicking on the little copy button on the bottom right of the codeblock below and paste it to the textbox of the Datasette tool. Then click **Submit query**.

     <br>

    4.  Your output resultset should look like the image below:

         <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/3.A.2.4.png" width="520" height="400">

<br>

# 

## Task B: Practice exercises on LIMIT

Now, let us practice creating and running some LIMIT related queries.

<br>

1.  Problem:

    > *Retrieve the name of first 50 films distinctly.*

     <details>
     <summary>Hint</summary>

    > Follow example 1 of LIMIT. Use DISTINCT.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT DISTINCT Title FROM FilmLocations LIMIT 50;
    ```

    {: codeblock}

     </details>

     <details>
     <summary>Output</summary>

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/3.B.1.O.png" width="520" height="400">

     </details>

<br>

2.  Problem:

    > *Retrieve first 10 film names distinctly released in 2015.*

     <details>
     <summary>Hint</summary>

    > Follow example 1 of LIMIT. Use DISTINCT. Use WHERE clause comparsion operator `=` which means **"Equal to"**.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT DISTINCT Title FROM FilmLocations WHERE ReleaseYear=2015 LIMIT 10;
    ```

    {: codeblock}

     </details>

     <details>
     <summary>Output</summary>

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/3.B.2.O.png" width="520" height="400">

     </details>

<br>

3.  Problem:

    > *Retrieve the next 3 film names distinctly after first 5 films released in 2015.*

     <details>
     <summary>Hint</summary>

    > Follow example 2 of the LIMIT exercise to learn how to use OFFSET. Use DISTINCT and use the WHERE clause comparison operator `=` which means **"Equal to"**.

     </details>

     <details>
     <summary>Solution</summary>

    ```
    SELECT DISTINCT Title FROM FilmLocations WHERE ReleaseYear=2015 LIMIT 3 OFFSET 5;
    ```

    {: codeblock}

     </details>

     <details>
     <summary>Output</summary>

     <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/Labs_Coursera_V5/labs/Lab%20-%20COUNT%20-%20DISTINCT%20-%20LIMIT/images/3.B.3.O.png" width="520" height="400">

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
| 2020-11-24 | 1.0     | Sandip Saha Joy | Initial version created |

<br>

## <h3 align="center"> Â© IBM Corporation 2020. All rights reserved. <h3/>
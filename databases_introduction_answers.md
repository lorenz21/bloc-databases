#### Exercises

1. What data types do each of these values represent?

  1. "A Clockwork Orange"

    A:[STRING]
  1. 42

    A:[INTEGER]
  1. 09/02/1945

    A:[DATE]
  1. 98.7

    A:[FLOAT]
  1. $15.99

    A:[STRING]
1. Explain when a database would be used. Explain when a text file would be used.

  A: A database would be used when a developer wants to store data that will still be available when an applications processes have been ended. A good example of this is User log on information, when a user logs off and closes the application, their data should be saved for the next time they return.

1. Describe one difference between SQL and other programming languages.

  A: SQL's syntax is very close to everyday speech. As a developer you are just asking and requesting for certain data, but when querying a database you aren't concerned with how you get the data, the database engine will decide on what is the most efficient way to get that data.

1. In your own words, explain how the pieces of a database system fit together at a high level.

  A: The data is organized to fit into various tables, rows, and columns of a database management system. This makes it easy to create, update, and delete entries in various tables, columns, and rows in the DBS.

1. Explain the meaning of table, row, column, and value.

  A: A table is a collection of related data that is held together by, various columns and rows in the table. Columns are used to describe what kind of data is being stored in the table, (i.e., persons name, email, password, etc.). A row represents a single structured data item in the table that is labeled by the columns.

1. List three data types that can be used in a table.

  A:
  * `INTEGER`
  * `FLOAT`
  * `DATE`

1. Given this payments table, provide an English description of the following queries and include their results:
  ```SQL
     SELECT date, amount
     FROM payments;

     SELECT amount
     FROM payments
     WHERE amount > 500;

     SELECT *
     FROM payments
     WHERE payee = 'Mega Foods';
  ```
    A:
    * Give me `date`s and `amount`s from the `payments` table
    * Give me `amount`s from the `payments` table where the `amount` is greater than 500
    * Give me all items from the `payments` table where the `payee` is Mega Foods
1. Given this users table, write SQL queries using the following criteria and include the output:

  * The email and sign-up date for the user named DeAndre Data.
  * The user ID for the user with email 'aleesia.algorithm@uw.edu'.
  * All the columns for the user ID equal to 4.

  ```SQL
     SELECT email, signup
     FROM Users
     WHERE name = 'DeAndre Data';
  ```
  ![Email and Signup SQL query result](https://i.imgur.com/m4q3njM.png)
  ```SQL
  SELECT userId
  FROM Users
  WHERE email= 'aleesia.algorithm@uw.edu';
  ```
  ![Email SQL query result](https://i.imgur.com/DBURCph.png)
  ```SQL
  SELECT *
  FROM Users
  WHERE userId= '4';
  ```
  ![All userID 4 SQL query result](https://i.imgur.com/AMfcxdD.png)

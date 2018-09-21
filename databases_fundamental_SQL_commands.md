#### Exercises
1. List the commands for adding, updating, and deleting data.

```SQL
[ADD] Insert Into
[EDIT] Update
[DELETE] Delete
```

1. Explain the structure for each type of command.

  A: The structure is `command` what you want to do, then where you want to use that command on (i.e., specific table or column), then a possible where clause to specify the exact rows or data that should be affected.

1. What are some of the data types that can be used in tables? Give a real-world example of each type.

  A: `money` type can be used in any financial table to store currency, like a banking application that needs to store balance, withdrawals, deposits, etc. `date` data type which can be used to store timestamps, maybe in a blogging application that stores a timestamp.

1. Decide how to create a new table to hold a list of people invited to a wedding dinner. The table needs to have first and last names, whether they sent in their RSVP, the number of guests they are bringing, and the number of meals (1 for adults and 1/2 for children).

  * Which data type would you use to store each of the following pieces of information?
    * First and last name. [char]
    * Whether they sent in their RSVP. [boolean]
    * Number of guests. [smallint]
    * Number of meals. [float]
  * Write a command that creates the table to track the wedding dinner.
    ```SQL
    CREATE TABLE dinner_list(
	     id integer,
	     first_name char(50),
	     last_name char(50),
	     rsvp boolean,
	     guest integer,
	     meals float
    );
    ```
  * Write a command that adds a column to track whether the guest sent a thank you card.
  ```SQL
  ALTER TABLE dinner_list ADD COLUMN tycard boolean;
  ```
  * You have decided to move the data about the meals to another table, so write a command to remove the column storing the number meals from the wedding table.
  ```SQL
  ALTER TABLE dinner_list DROP COLUMN meals;
  ```
  * The guests will need a place to sit at the reception, so write a command that adds a column for table number.
  ```SQL
  ALTER TABLE dinner_list ADD COLUMN table_number integer;
  ```
  * The wedding is over and we do not need to keep this information, so write a command that deletes the table numbers from the database.
  ```SQL
  ALTER TABLE dinner_list DROP COLUMN table_number;
  ```

1. Write a command to create a new table to hold the books in a library with the columns ISBN, title, author, genre, publishing date, number of copies, and available copies.
  ```SQL
  CREATE TABLE books (
    id integer,
    ISBN text,
    title text,
    author char(255),
    genre char(255),
    publishing_date date,
    copies integer,
    available_copies integer
  );
  ```
  * Find three books and add their information to the table.
  ```SQL
    INSERT INTO books (id, ISBN, title, author, genre, publishing_date, copies, available_copies)
    VALUES
    (1, '978-136802245-3', 'The Darkest Minds', 'Alexandra Bracken', 'Fantasy', '08-26-2012', 24, 20),
    (2, 'B008EMKWYA', 'Poison Study', 'Maria V. Snyder', 'Fantasy', '08-15-2012', 12, 2),
    (3, 'B06VXWPMV5', 'The City of Brass', 'S. A. Chakraborty', 'Fantasy', '11-14-2017', 5, 2);
    ```
  * Someone has just checked out one of the books. Change the number of available copies to 1 fewer.
  ```SQL
  UPDATE books SET available_copies=19 WHERE title='The Darkest Minds';
  ```
  * Now one of the books has been added to the banned books list. Remove it from the table.
  ```SQL
  DELETE FROM books WHERE title='Poison Study';
  ```
1. Write a command to make a new table to hold spacecrafts. Information should include id, name, year launched, country of origin, a brief description of the mission, orbiting body, if it is currently operating, and its approximate miles from Earth. In addition to the table creation, provide commands that perform the following operations:
  ```SQL
  CREATE TABLE spacecrafts (
    id integer,
    name char(255),
    launch_year date,
    country char(255),
    description text,
    orbiting_body text,
    operating boolean,
    earth_distance float
  );
  ```
  * Add three non-Earth-orbiting satellites to the table.
  ```SQL
  INSERT INTO spacecrafts (id, name, launch_year, country, description, orbiting_body, operating, earth_distance)
    VALUES
    (1, 'Juno', '2011', 'US', 'Space probe orbiting Jupiter', 'Jupiter', 'True', 2672),
    (2, 'Mars Reconnaissance Orbiter', '2005', 'US', 'Spacecraft designed to conduct reconnaissance and exploration of Mars from orbit', 'Mars', 'True', 33554044.38),
    (3, 'Cassini Huygens', '2004', 'UK', 'Space probe to study Saturn and its system', 'Saturn', 'False',  76223762);
  ```
  * Remove one of the satellites from the table since it has just crashed into the planet.
  ```SQL
  DELETE FROM spacecrafts WHERE name='Cassini Huygens';
  ```
  * Edit another satellite because it is no longer operating and change the value to reflect that.
  ```SQL
  UPDATE spacecrafts SET operating='False' WHERE name='Juno';
  ```
1. Write a command to create a new table to hold the emails in your inbox. This table should include an id, the subject line, the sender, any additional recipients, the body of the email, the timestamp, whether or not you have read the email, and the id of the email chain it's in. Also provide commands that perform the following operations:
```SQL
CREATE TABLE email (
  id integer,
  subject char(255),
  sender char(255),
  recipients text,
  body text,
  timestamp timestamp,
  read boolean,
  chain_id integer
);
```
  * Add three new emails to the inbox.
  ```SQL
  INSERT INTO email (id, subject, sender, recipients, body, timestamp, read, chain_id)
  VALUES
  (1, 'Job Offer', 'sarahsmith@gmail.com', 'stevenjohn@outlook.com', 'Hello Steven, Just checking if you are still intersted in the job', '2018-09-20 13:45:06', 'True', 1123),
  (2, 'Credit Check', 'creditkarma@credit.io', 'philmoore@hotmail.com', 'Hello Phill, Have you checked your credit lately?', '2017-03-02 09:23:00', 'False', 2334),
  (3, 'Bank Statment', 'chase@banking.gov', 'melissa@outlook.com', 'Hello Melissa, Your e-stament is avaliable online', '2018-06-01 19:12:23', 'False', 234);
  ```
  * You deleted one of the emails, so write a command to remove the row from the inbox table.
  ```SQL
  DELETE FROM email WHERE subject='Bank Statment';
  ```
  * You started reading an email but just heard a crash in another room. Mark the email as unread before investigating the crash, so you can come back and read it later.
  ```SQL
  UPDATE email SET read='False' WHERE sender='sarahsmith@gmail.com';
  ```

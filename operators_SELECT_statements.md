#### Exercises
1. Write out a generic SELECT statement.
  A:
  ```SQL
  SELECT <column1, column2, ... *>
  FROM <table1, table2 ...>
  <optional: WHERE <condition>>
  ```
1. Create a fun way to remember the order of operations in a SELECT statement, such as a mnemonic.

    A: `Saved From Werewolf`

1. Given this dogs table, write queries to select the following pieces of data:

  > Intake teams typically guess the breed of shelter dogs, so the breed column may have multiple words (for example, "Labrador Collie mix").

  * Display the name, gender, and age of all dogs that are part Labrador.
  ```SQL
  SELECT name, gender, age
  FROM dogs
  WHERE breed LIKE '%labrador%';
  ```
  * Display the ids of all dogs that are under 1 year old.
  ```SQL
  SELECT id
  FROM dogs
  WHERE age < 1;
  ```
  * Display the name and age of all dogs that are female and over 35lbs.
  ```SQL
  SELECT name, age
  FROM dogs
  WHERE gender='F' AND weight > 35;
  ```
  * Display all of the information about all dogs that are not Shepherd mixes.
  ```SQL
  SELECT *
  FROM dogs
  WHERE breed NOT LIKE '%shepherd%';
  ```
  * Display the id, age, weight, and breed of all dogs that are either over 60lbs or Great Danes.
  ```SQL
  SELECT id, age, weight, breed
  FROM dogs
  WHERE weight > 60 OR breed LIKE '%great dane%';
  ```
1. Given this cats table, what records are returned from these queries?

  * SELECT name, adoption_date FROM cats;

    A: Every row in the `cats` table with the columns of `name` and `adoption_date`

  * SELECT name, age FROM cats;

    A: Every row in the `cats` table with the columns of `name` and `age`

1. From the cats table, write queries to select the following pieces of data.
  * Display all the information about all of the available cats.
  ```SQL
  SELECT * FROM cats;
  ```
  * Display the name and sex of all cats who are 7 years old.
  ```SQL
  SELECT name, gender
  FROM cats
  WHERE age=7;  
  ```
  * Find all of the names of the cats, so you don’t choose duplicate names for new cats.
  ```SQL
  SELECT name FROM cats;
  ```
1. List each comparison operator and explain when you would use it. Include a real world example for each.
  * If you can’t list these from memory, do these flashcards until you can!
  * `<` - See if all cats in a cat database have an age that is less than (`<`) 5
  * `>` - See if all cats in a cat database have an age that is less than (`>`) 7
  * `<=` - See if all cats in a cat database have a weight that is less than or equal to (`<=`) 10 lbs
  * `>=` - See if all cats in a cat database have a weight that is greater than or equal to (`>=`) 80 lbs
  * `=` - See if any cats in a cat database have a gender that is equal to (`=`) F or Female
  * `!=` - See if any cats in a cat database have an age that is not equal to (`!=`) 1
1. From the cats table, what data is returned from these queries?
  * SELECT name FROM cats WHERE gender = ‘F’;

    A: The two female cats are returned: **Seashell** and **Nala**

  * SELECT name FROM cats WHERE age <> 3;

    A: Returns all cats that are less than or greater than 3 years old: **Mushi**, **Seashell**, **Victoire** and **Nala**. **Azul** is 3 years old so it is not returned

  * SELECT ID FROM cats WHERE name != ‘Mushi’ AND gender = ‘M’;

    A: ID for 3 and 4 are returned. The queries have back-ticks instead of quotes for the name and gender, so that might cause errors, I changed them to quotes. 

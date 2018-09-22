#### Exercises
1. How do you find related data held in two separate data tables?

  A: You use the `JOIN` method to combine data from two or more tables.

1. Explain, in your own words, the difference between an INNER JOIN, LEFT OUTER JOIN, and RIGHT OUTER JOIN. Give a real-world example for each.

  A: When you have two tables, like `employees` and `desks`, an employee can or can not have a desk and desks may or may not be assigned to a particular employee.
  `INNER JOIN` - Would be asking for all `employees` that have `desks` assigned to them, but it would omit employees who don't have desk assigned to them, and it would omit desks that don't have an employees assigned to them
  `LEFT OUTER JOIN` - Assuming `employees` is the left table, this would be asking to return all employees with the desk they are assigned to
  `RIGHT OUTER JOIN` - This would be asking to return all `desks` with their linked employee if they have one.

1. Define primary key and foreign key. Give a real-world example for each.

  A: A primary key is unique identifier in a table, and a foreign key is linked to this primary key to join together related data in different tables. A good example of this is from question 2, `employeeId` could be a primary key for the employee table, then it can link specific employees to specific desks.

1. Define aliasing.

  A: It a method used to shorted the amount of code needed to be written to refer to certain tables.

1. Change this query so that you are using aliasing:
  ```SQL
  SELECT professor.name, compensation.salary,
  compensation.vacation_days FROM professor JOIN
  compensation ON professor.id =
  compensation.professor_id;
  ```
  ```SQL
  SELECT p.name, c.salary,
  c.vacation_days
  FROM professor AS p
  JOIN compensation AS c
  ON p.id = c.p_id;
  ```

1. Why would you use a `NATURAL JOIN`? Give a real-world example.

  A: When you want to simply your syntax, and you don't mind joining every related item in the tables. In the example above with the employees and desks, you might want to use a `NATURAL JOIN` as you know want to see all data that is related to both tables.

1. Using this [Employee schema and data](https://www.db-fiddle.com/f/sG1TKgR15GhH8cjbAwzjAm/0), write queries to find the following information:
  * List all employees and all shifts.
  ```SQL
  SELECT e.name, s.date, s.start_time, s.end_time
  FROM scheduled_shifts as ss
  JOIN employees AS e ON ss.employee_id = e.id
  JOIN shifts AS s ON ss.shift_id = s.id;
  ```
1. Using this [Adoption schema and data](https://www.db-fiddle.com/f/tpodLv3A43VL4gHqohqx2o/0), please write queries to retrieve the following information and include the results:
  * Create a list of all volunteers. If the volunteer is fostering a dog, include each dog as well.
  ```SQL
  SELECT v.first_name, v.last_name, d.name
  FROM volunteers as v
  JOIN dogs as d ON v.foster_dog_id=d.id;
  ```
  * The cat's name, adopter's name, and adopted date for each cat adopted within the past month to be displayed as part of the "Happy Tail" social media promotion which posts recent successful adoptions.
  ```SQL
  SELECT c.name, a.first_name, a.last_name, ca.date
  FROM cat_adoptions as ca
  JOIN cats as c ON ca.cat_id=c.id
  JOIN adopters as a ON ca.adopter_id=a.id
  WHERE ca.date>='2018-09-01' AND ca.date<'2018-09-21';
  ```
  * Create a list of adopters who have not yet chosen a dog to adopt.
  ```SQL
  SELECT a.first_name, a.last_name
  FROM dog_adoptions as da
  JOIN dogs as d ON da.dog_id=d.id
  INNER JOIN adopters as a ON da.adopter_id=a.id;
  ```
  * Lists of all cats and all dogs who have not been adopted.
  ```SQL
  SELECT d.name, c.name
  FROM adopters as a
  LEFT OUTER JOIN dog_adoptions as da ON da.adopter_id=a.id
  LEFT OUTER JOIN cat_adoptions as ca ON ca.adopter_id=a.id
  LEFT OUTER JOIN cats as c ON ca.cat_id=c.id
  LEFT OUTER JOIN dogs as d ON da.dog_id=d.id;
  ```
  * The name of the person who adopted Rosco.
  ```SQL
  SELECT a.first_name, a.last_name
  FROM adopters as a
  JOIN dog_adoptions as da ON da.adopter_id=a.id
  JOIN dogs as d ON da.dog_id=d.id;  
  ```
1. Using this [Library schema and data](https://www.db-fiddle.com/f/j4EGoWzHWDBVtiYzB9ygC4/0), write queries applying the following scenarios and include the results:
  * To determine if the library should buy more copies of a given book, please provide the names and position, in order, of all of the patrons with a hold (request for a book with all copies checked out) on "Advanced Potion-Making".
  ```SQL
  SELECT p.name
  FROM holds AS h
  JOIN patrons AS p ON h.patron_id=p.id
  WHERE h.isbn='9136884926';
  ```
  * List all of the library patrons. If they have one or more books checked out, list the books with the patrons.
  ```SQL
  SELECT DISTINCT p.name
  FROM transactions AS t
  RIGHT OUTER JOIN patrons AS p ON t.patron_id=p.id
  WHERE t.checked_in_date IS NOT NULL;
  ```

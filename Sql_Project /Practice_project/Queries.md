## SELECTING ALL THE STUDENTS ID AND THEIR FORE SUBJECTS MARKS.
    SELECT *
    FROM students;

## Retrieve all columns from the name table.
    SELECT *
    FROM name;

## List the students who have not paid their fees.
      SELECT 
        s.studend_id,
        f.fees_paid,
        n.firstname
      FROM 
        students AS s
      JOIN 
        name AS n ON s.studend_id = n.studend_id
      JOIN
        fees AS f ON n.fessid = f.fessid
      WHERE f.fees_paid = 'no';

## Find students who scored more than 80 in English.
            SELECT *
               FROM students 
               WHERE english > 80;

## Retrieve student details sorted by their total marks in descending order.
            SELECT 
              s.studend_id , 
              n.firstname ,
              n.lastname ,
              s.total_marks 
           FROM 
             students AS s
           JOIN 
             name AS n ON s.studend_id = n.studend_id
           ORDER BY total_marks DESC;

## Join the name and fees tables to show which students have paid or not paid their fees.
               SELECT * 
               FROM 
                 name AS n
               Join 
                 fees AS f ON n.fessid = f.fessid;    


## Find the names of students whose total marks are above the average total marks.
               SELECT 
                 s.studend_id,
                 n.firstname,
                 n.lastname,
                 s.total_marks
              FROM students AS s
              JOIN
                 name AS n ON n.studend_id = s.studend_id
              WHERE total_marks > 247.12;

## Join all three tables to show the complete details of students, including fees paid and marks.
            SELECT *
            FROM 
               students AS s
            JOIN
               name AS n ON n.studend_id = s.studend_id
            JOIN 
               fees AS f ON f.fessid = n.fessid;

## List the students who have scored the highest in Science.
         SELECT 
           s.studend_id,
           n.firstname,
           n.lastname,
           s.science
         FROM 
           students AS s
         JOIN
           name AS n ON s.studend_id = n.studend_id 
         ORDER BY science DESC
         LIMIT 5;

## Update the fees table to mark fees as paid for all students who have scored above 300 total marks.
   

            
## Finding the first name of the student and student_id for all those who have paid their fees.
     SELECT 
        s.studend_id,
        f.fees_paid
        n.firstname
     FROM 
        students AS s
     JOIN 
        name AS n ON s.studend_id = n.studend_id
     JOIN
        fees AS f ON n.fessid = f.fessid
     WHERE f.fees_paid = 'yes';
     
## Finding the amount of scholarship for all the students using 'Case Statements' and "Joins"
    SELECT 
    s.studend_id,
    n.firstname,
    n.lastname,  
    CASE
        WHEN s.total_marks > 250 AND f.fees_paid = 'yes' THEN 100000 * s.avg
        WHEN s.total_marks > 150 AND s.total_marks <= 250 AND f.fees_paid = 'yes' THEN 50000 * s.avg
        WHEN s.total_marks > 80 AND s.total_marks <= 150 AND f.fees_paid = 'yes' THEN 20000 * s.avg
        WHEN f.fees_paid = 'no' THEN "NO SCHOLARSHIP"
        ELSE 10000 * s.avg
    END AS calculated_scholarship_amt
    FROM 
          students AS s
    JOIN 
          name AS n ON s.studend_id = n.studend_id
    JOIN 
          fees AS f ON n.fessid = f.fessid;

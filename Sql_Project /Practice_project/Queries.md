## SELECTING ALL THE STUDENTS ID AND THEIR FORE SUBJECTS MARKS.
    SELECT *
    FROM students;

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

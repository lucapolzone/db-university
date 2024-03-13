 # Query con JOIN

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia 

 ```
 SELECT 
  `students`.`name` AS `student_name`,
  `students`.`surname`AS `student_surname`,
  `degrees`.`name` AS `degree_name`
FROM `students`

INNER JOIN `degrees`
ON `degrees`.`department_id` = `students`.`degree_id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';
 ```

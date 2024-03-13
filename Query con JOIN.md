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

<br>

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

```
SELECT
  `degrees`.`level` AS `degrees_level`, 
  `degrees`.`name` AS `degrees_name`
FROM `degrees`
INNER JOIN `departments`
ON `departments`.`id` = `degrees`.`department_id` 
WHERE `degrees`.`level` = 'magistrale' AND `departments`.`name`  = 'Dipartimento di Neuroscienze';
```

<br>

[comment]: <> (Molti a molti, tabella pivot)

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```
SELECT 
  `courses`.`name`  
FROM `courses`
INNER JOIN `teachers`
ON `teachers`.`id`
WHERE `teachers`.`id` = 44;
```
==== <br>
Soluzione migliore:

```
SELECT
  `teachers`.`name` AS `teachers_name`,
  `teachers`.`surname` AS `teachers_surname`,
  `courses`.`name`
FROM `teachers`
INNER JOIN `courses`
ON `courses`.`id`
WHERE `teachers`.`id` = 44;
```
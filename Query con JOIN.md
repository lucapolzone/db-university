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
<br>

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

```
SELECT
	`students`.`surname` AS `student_surname`,
    `students`.`name` AS `student_name`,
    `degrees`.`name`AS `degree_name`,
    `departments`.`name` AS `department_name`
FROM `students`
INNER JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id`
INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`
ORDER BY `student_surname`, `student_name` ASC;
```

<br>

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```
SELECT
    `degrees`.`name` AS `degree_name`,
	`courses`.`name` AS `course_name`,
	`teachers`.`surname` AS `teacher_surname`,
    `teachers`.`name` AS `teacher_name`	
FROM `degrees`
INNER JOIN `courses`
ON `degrees`.`id` = `courses`.`degree_id`
INNER JOIN `course_teacher`
ON `courses`.`id` = `course_teacher`.`course_id`
INNER JOIN `teachers`
ON `teacher_id` = `teachers`.`id`
ORDER BY `teacher_surname`, `teacher_name` ASC;
```

<br>

6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

```
SELECT DISTINCT
  `teachers`.`surname` AS `teacher_surname`,
  `teachers`.`name` AS `teacher_name`,
  `departments`.`name` AS `department_name`
FROM `teachers`
INNER JOIN `course_teacher`
ON `teachers`.`id` = `teacher_id`
INNER JOIN `courses`
ON `course_id` = `courses`.`id`
INNER JOIN `degrees`
ON `courses`.`degree_id` = `degrees`.`id`
INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = 'Dipartimento di Matematica'
ORDER BY `teacher_surname`, `teacher_name` ASC;
```
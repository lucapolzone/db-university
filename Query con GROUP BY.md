1. Contare quanti iscritti ci sono stati ogni anno

```
SELECT COUNT(*), `enrolment_date` FROM `students`
GROUP BY `enrolment_date`;
```
<br>

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```
SELECT COUNT(*), `office_address` FROM `teachers`
GROUP BY `office_address`;
```

<br>

3. Calcolare la media dei voti di ogni appello d'esame

```
SELECT AVG(vote) AS `average_vote` FROM `exam_student`;
```

<br>

4. Contare quanti corsi di laurea ci sono per ogni dipartimento
```
SELECT COUNT(*), `department_id` FROM `degrees`
GROUP BY `department_id`;
```
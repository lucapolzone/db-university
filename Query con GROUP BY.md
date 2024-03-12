1. Contare quanti iscritti ci sono stati ogni anno

```
SELECT COUNT(*), `enrolment_date` FROM `students`
GROUP BY `enrolment_date`;
```
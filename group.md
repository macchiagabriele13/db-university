Group by:
Contare quanti iscritti ci sono stati ogni anno

```sql
SELECT YEAR(enrolment_date) AS 'anno', COUNT(id) AS 'iscritti' FROM `students` GROUP BY YEAR(enrolment_date);
```

Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```sql
SELECT COUNT(id) AS 'insegnante', `office_address` AS 'edificio' FROM `teachers` GROUP BY `office_address`;

```

Calcolare la media dei voti di ogni appello d'esame

```sql
SELECT `exam_id` AS 'appello', AVG(`vote`) AS 'media voto' FROM `exam_student` GROUP BY `exam_id`;
```



Contare quanti corsi di laurea ci sono per ogni dipartimento

```sql
SELECT `department_id` as 'Dipartimento', COUNT(id) AS 'numero corsi' FROM `degrees` GROUP BY `department_id`;
```




Join:
Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```sql
SELECT `students`.`id`,`students`.`name`, `students`.`surname`, `students`.`registration_number`
FROM `students`
JOIN `degrees`
ON `students.degree_id` = `degrees.id`
WHERE `degrees.name` = 'Corso di Laurea in Economia';
```

Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze


```sql
SELECT degrees.name, degrees.level
FROM degrees
JOIN departments
ON degrees.department_id = departments.id
WHERE departments.name = 'Dipartimento di Neuroscienze' AND degrees.level = 'magistrale';
```

Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)


```sql
SELECT `courses`.`name`, `courses`.`period`, `courses`.`year`, `courses`.`cfu`, `courses`.`website`
FROM `courses`
JOIN `course_teacher`
ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `teachers`
ON `course_teacher`.`teacher_id` = `teachers`.`id`
WHERE `teachers`.`name` = "Fulvio" AND `teachers`.`surname`= "Amato";
```


Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome



```sql
SELECT `students`.`surname`, `students`.`name` AS 'nome studente', `students`.`registration_number`, `degrees`.`name`, `degrees`.`level`, `departments`.`name` AS 'nome dipartimento'
FROM `students`
JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id` 
JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id` 
ORDER BY `students`.`surname`, `students`.`name`;
```

Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti


```sql
SELECT `degrees`.`name` AS 'nome corso di laurea', `degrees`.`level`, `courses`.`name` AS 'nome corso', `courses`.`period`, `teachers`.`name` AS 'nome insegnante', `teachers`.`surname`
FROM `degrees`
JOIN `courses`
ON `degrees`.`id` = `courses`.`degree_id`
JOIN `course_teacher`
ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers`
ON `teachers`.`id` = `course_teacher`.`teacher_id`;
```


Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)


```sql
SELECT DISTINCT `teachers`.`name`, `teachers`.`surname`, `teachers`.`phone`, `teachers`.`email`, `teachers`.`office_address`, `teachers`.`office_number`, `departments`.`name` as 'departments'
FROM `teachers`
JOIN `course_teacher`
ON `teachers`.`id` = `course_teacher`.`teacher_id`
JOIN `courses`
ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `degrees`
ON `degrees`.`id` = `courses`.`degree_id`
JOIN `departments`
ON `departments`.`id` = `degrees`.`department_id`
WHERE `departments`.`name`='Dipartimento di Matematica';
```


BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami


```sql

```

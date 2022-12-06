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

```

Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze


```sql

```

Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)


```sql

```


Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome



```sql

```

Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti


```sql

```


Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)


```sql

```


BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami


```sql

```

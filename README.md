## Descrizione:

```txt
Usate il database che avete creato a lezione
per eseguire le nuove repository, vi allego query GROUP BY e JOIN da risolvere..
```

### Query da eseguire:

#### GROUP BY:

1. [Contare quanti iscritti ci sono stati ogni anno](#query-1) &check;
2. [Contare gli insegnanti che hanno l'ufficio nello stesso edificio](#query-2) &check;
3. [Calcolare la media dei voti di ogni appello d'esame](#query-3) &check;
4. [Contare quanti corsi di laurea ci sono per ogni dipartimento](#query-4) &check;

#### JOIN:

5. [Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia](#query-5) &check;
6. [Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze](#query-6) &check;
7. [Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)](#query-7) &check;
8. [Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome](#query-8) &check;
9. [Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti](#query-9) &check;
10. [Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica](#query-10) &cross;

#### BONUS:

11. [Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18](#query-11) &cross;

## Svolgimento:

#### GROUP BY:

- #### Query 1
  Contare quanti iscritti ci sono stati ogni anno &check;

```sql
SELECT
    COUNT(`id`) AS `n_iscrizioni`,
    YEAR(`enrolment_date`) AS `anno_iscrizione`
FROM
    `students`
GROUP BY
    `anno_iscrizione`;
```

- #### Query 2
  Contare gli insegnanti che hanno l'ufficio nello stesso edificio &check;

```sql
SELECT
    COUNT(`id`) AS `n_insegnati`,
    `office_address` AS `indirizzo`
FROM
    `teachers`
GROUP BY
    `indirizzo`;
```

- #### Query 3
  Calcolare la media dei voti di ogni appello d'esame &check;

```sql
SELECT
    `exam_id` AS `appello_esame`,
    ROUND(AVG(`vote`), 2) AS `media_voti`
FROM
    `exam_student`
GROUP BY
    `appello_esame`;
```

- #### Query 4
  Contare quanti corsi di laurea ci sono per ogni dipartimento &check;

```sql
SELECT
    COUNT(`id`) AS `n_corsi`,
    `department_id` AS `dipartimento`
FROM
    `degrees`
GROUP BY
    `dipartimento`;
```

#### JOIN:

- #### Query 5
  Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia &check;

```sql
SELECT
    `students`.*,
    `degrees`.`name` AS `corso`
FROM
    `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
WHERE
    `degrees`.`name` = 'Corso di Laurea in Economia';
```

- #### Query 6
  Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze &check;

```sql
SELECT
    `degrees`.`name` AS `corso`,
    `departments`.`name` AS `dipartimento`,
    `degrees`.`level` AS `durata`
FROM
    `degrees`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE
    `departments`.`name` = "Dipartimento di Neuroscienze" AND `degrees`.`level` = "magistrale";
```

- #### Query 7
  Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44) &check;

```sql
SELECT
    `courses`.`name` AS `corso`,
    `teachers`.`name` AS `nome_prof.`,
    `teachers`.`surname`
FROM
    `courses`
JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
WHERE
    `course_teacher`.`teacher_id` = 44
```

- #### Query 8
  Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome &check;

```sql
SELECT
    `students`.`name` AS `nome_studente`,
    `students`.`surname` AS `cognome_studente`,
    `degrees`.`name` AS `corso_di_laurea`,
    `departments`.`name` AS `dipartimento`
FROM
    `students`
JOIN `degrees` ON `degree_id` = `students`.`degree_id`
JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
ORDER BY
    `students`.`surname`;
```

- #### Query 9
  Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti &check;

```sql
SELECT
    `degrees`.`name` AS `corso_di_laurea`,
    `courses`.`name` AS `corso`,
    `teachers`.`name` AS `nome_prof.`,
    `teachers`.`surname` AS `cognome_prof.`
FROM
    `degrees`
JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id`
JOIN `teachers` ON `courses`.`id` = `teachers`.`id`;
```

- #### Query 10
  Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica &cross;

```sql
SELECT
    `teachers`.`name` AS `nome_prof.`,
    `teachers`.`surname` AS `cognome_prof.`,
    -- `courses`.`name` AS `nome_corso`,
    -- `degrees`.`name` AS `nome_corso_esame`,
    `departments`.`name` AS `nome_dipartimento`
FROM
    `teachers`
JOIN `courses` ON `teachers`.`id` = `courses`.`id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE
    `departments`.`name` = 'Dipartimento di Matematica'
```

#### BONUS:

- #### Query 11
  Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18 &cross;

```sql

```

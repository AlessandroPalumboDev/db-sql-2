## Descrizione:

```txt
Usate il database che avete creato a lezione
per eseguire le nuove repository, vi allego query GROUP BY e JOIN da risolvere..
```

### Query da eseguire:

#### GROUP BY:

1. [Contare quanti iscritti ci sono stati ogni anno](#query-1) &cross;
2. [Contare gli insegnanti che hanno l'ufficio nello stesso edificio](#query-2) &cross;
3. [Calcolare la media dei voti di ogni appello d'esame](#query-3) &cross;
4. [Contare quanti corsi di laurea ci sono per ogni dipartimento](#query-4) &cross;

#### JOIN:

5. [Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia](#query-5) &cross;
6. [Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze](#query-6) &cross;
7. [Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)](#query-7) &cross;
8. [Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome](#query-8) &cross;
9. [Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti](#query-9) &cross;
10. [Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica](#query-10) (54) &cross;

#### BONUS:

11. [Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18](#query-11) &cross;

## Svolgimento:

#### GROUP BY:

- #### Query 1
  Contare quanti iscritti ci sono stati ogni anno &cross;

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
  Contare gli insegnanti che hanno l'ufficio nello stesso edificio &cross;

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
  Calcolare la media dei voti di ogni appello d'esame &cross;

```sql

```

- #### Query 4
  Contare quanti corsi di laurea ci sono per ogni dipartimento &cross;

```sql

```

#### JOIN:

- #### Query 5
  Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia &cross;

```sql

```

- #### Query 6
  Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze &cross;

```sql

```

- #### Query 7
  Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44) &cross;

```sql

```

- #### Query 8
  Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome &cross;

```sql

```

- #### Query 9
  Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti &cross;

```sql

```

- #### Query 10
  Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica &cross;

```sql

```

#### BONUS:

- #### Query 11
  Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18 &cross;

```sql

```

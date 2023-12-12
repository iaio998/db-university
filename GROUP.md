- ## Contare quanti iscritti ci sono stati ogni anno

  SELECT COUNT(YEAR(\`enrolment_date\`)) AS 'iscrizioni',YEAR(\`enrolment_date`) AS 'anno'

  FROM \`students`

  GROUP BY YEAR(\`enrolment_date`)

- ## Contare gli insegnanti che hanno l'ufficio nello stesso edificio

  SELECT COUNT\(\`id\`), \`office_address`

  FROM \`teachers`

  GROUP BY \`office_address`

- ## Calcolare la media dei voti di ogni appello d'esame

  SELECT AVG(\`vote\`), COUNT(\`exam_id\`)

  FROM \`exam_student`

  GROUP BY \`exam_id`

- ## Contare quanti corsi di laurea ci sono per ogni dipartimento

  SELECT \`department_id\`, COUNT(\`name\`)

  FROM \`degrees`

  GROUP BY \`department_id`

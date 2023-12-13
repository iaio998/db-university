- ## Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

  SELECT \*

  FROM \`students\`

  JOIN \`degrees\` ON \`degrees\`.\`id\` = \`students\`.\`degree_id\`

  WHERE \`degrees\`.\`name\` = 'Corso di Laurea in Economia'

- ## Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

  SELECT \*

  FROM \`degrees\`

  JOIN \`departments\` ON \`departments\`.\`id\` = \`degrees\`.\`department_id\`

  WHERE \`departments\`.\`name\` = 'Dipartimento di Neuroscienze'

  AND \`degrees\`.\`level\` = 'magistrale'

- ## Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

  SELECT \`teachers\`.\`name\`, \`teachers\`.\`surname\`, \`courses\`.\`name\`, \`courses\`.\`period\`

  FROM \`teachers\`

  JOIN \`course_teacher\` ON \`course_teacher\`.\`teacher_id\` = \`teachers\`.\`id\`

  JOIN \`courses\` ON \`courses\`.\`id\` = \`course_teacher\`.\`course_id\`

  WHERE \`teachers\`.\`id\` = 44

- ## Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

  SELECT \`students\`.\`name\`, \`students\`.\`surname\`, \`degrees\`.\`name\`, \`departments\`.\`name\`

  FROM \`students\`

  JOIN \`degrees\` ON \`degrees\`.\`id\` = \`students\`.\`degree_id\`

  JOIN \`departments\` on \`departments\`.\`id\` = \`degrees\`.\`department_id\`

  ORDER BY \`students\`.\`surname\` DESC

- ## Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

- ## Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

- ## BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.

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

  ORDER BY \`students\`.\`surname\` ASC

- ## Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

  SELECT \`degrees\`.\`name\`, \`courses\`.\`name\`, \`teachers\`.\`name\`, \`teachers\`.\`surname\`

  FROM \`courses\`

  JOIN \`degrees\` on \`degrees\`.\`id\` = \`courses\`.\`degree_id\`

  JOIN \`course_teacher\` ON \`course_teacher\`.\`course_id\` = \`courses\`.\`id\`

  JOIN \`teachers\` on \`teachers\`.\`id\` = \`course_teacher\`.\`teacher_id\`

- ## Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

  SELECT DISTINCT \`teachers\`.\`name\`, \`teachers\`.\`surname\`, \`departments\`.\`name\` as \`dipartimento\`

  FROM \`teachers\`

  JOIN \`course_teacher\` on \`course_teacher\`.\`teacher_id\` = \`teachers\`.\`id\`

  JOIN \`courses\` on \`courses\`.\`id\` = \`course_teacher\`.\`course_id\`

  JOIN \`degrees\` on \`degrees\`.\`id\` = \`courses\`.\`degree_id\`

  JOIN \`departments\` on \`departments\`.\`id\` = \`degrees\`.\`department_id\`

  WHERE \`departments\`.\`name\` = 'Dipartimento di Matematica'

- ## BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.

  SELECT \`students\`.\`name\`, \`students\`.\`surname\`, COUNT(\`exam_student\`.\`vote\`) AS \`prove_esame\`, MAX(\`exam_student\`.\`vote\`) AS \`voto_massimo\`, \`courses\`.\`name\` AS \`course_id\`

  FROM \`students\`

  JOIN \`exam_student\` ON \`exam_student\`.\`student_id\` = \`students\`.\`id\`

  JOIN \`exams\` ON \`exams\`.\`id\` = \`exam_student\`.\`exam_id\`

  JOIN \`courses\` ON \`courses\`.\`id\` = \`exams\`.\`course_id\`

  GROUP BY \`students\`.\`id\`, \`courses\`.\`id\` HAVING \`max_vote\` >= 18

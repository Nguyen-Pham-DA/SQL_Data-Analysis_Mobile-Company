-- Question 1: A list of Movies including: Title, Realease Year, Runtime(in hrs & mins) and combine them into 1 column--

SELECT CONCAT(title, "(", m_movie.year, ",",CONCAT (m_movie.minute DIV 60, 'h',m_movie.minute%60,'mins') , ")") AS List_of_Movies
FROM m_movie;

-- Question 2: A list of Movies lasting for at least 2 hours that have "happy" in the tagline. Show title, year came out, the tagline, runtime and sort by title--

SELECT title, m_movie.year, tagline, TRUNCATE(m_movie.minute/60,1) AS runtime
FROM m_movie
WHERE m_movie.minute >= 120 AND tagline LIKE "%happy%"
ORDER BY title;

-- Question 3: A list of female customers in Indian subcontinent showing their full names, ages, countries -- 

SELECT CONCAT(first_name," ",last_name) AS Full_name, TRUNCATE(DATEDIFF(SYSDATE(),date_of_birth)/365.25,0) AS Age
FROM m_consumer
WHERE gender = 'F' AND country IN ('India','Nepal','Bangladesh','Bhutan','Sri Lanka','Maldives','Pakistan');

-- Question 4: List all the movies in Japanese, Italian, Greek just showing language_id 

SELECT language_id
FROM m_languages
WHERE language_id IN('7', '13', '32') 

-- Question 5: A list of movies released in December showing title, year released, runtime. Sort by year and then title--

SELECT title, m_movie.year, m_movie.minute, m_movie.released
FROM m_movie
WHERE DATE_FORMAT(m_movie.released, '%m') = 12
ORDER BY m_movie.year DESC, title ASC;

-- Question 6: The number of rows in Movie table --

SELECT COUNT(*)
FROM m_movie;

-- Question 7: The total number of consumers for each gender category (female, male, not specified) -- 

SELECT  COUNT(gender),
CASE  gender WHEN 'F' THEN 'Female'
             WHEN 'M' THEN 'Male'
             ELSE 'Not Specified' END AS Gender
            FROM m_consumer
           GROUP BY gender;
-- Question 8: Any languages with more than 500 films. Needs to show Language ID and the film count. Sort the film count --

SELECT language_id, COUNT(movie_id)
FROM m_languages
GROUP BY language_id
HAVING COUNT(movie_id) > 500
ORDER BY COUNT(movie_id) DESC;

-- Question 9: The gender of voters (with consumer_gender(consumer_id) function), the rating they gave, the number of votes for each combo of gender and rating, sort by gender then rating from 5 to 1 -- 
SELECT consumer_gender(consumer_id) AS Gender, rating, COUNT(vote_id)
FROM m_vote
GROUP BY consumer_gender(consumer_id), rating
ORDER BY consumer_gender(consumer_id), rating DESC;

-- Question 10: The total budget allocated for movie productions in each of the last 20 years (based on released date). Show the year and budget -- 

SELECT YEAR(released) AS ReleasedYear, SUM(budget) AS total_budget
FROM m_movie
WHERE YEAR(SYSDATE()) - YEAR(released) <= 20
GROUP BY YEAR(released)
ORDER BY YEAR(released);



### Movies Table:

| Movie Name         | Movie Length | Lead Artist         | Genre         | Release Year | Rating |
|--------------------|--------------|---------------------|---------------|--------------|--------|
| Inception          | 148          | Leonardo DiCaprio   | Sci-Fi        | 2010         | 8.8    |
| Titanic            | 195          | Leonardo DiCaprio   | Drama         | 1997         | 7.8    |
| The Dark Knight    | 152          | Christian Bale      | Action        | 2008         | 9.0    |
| Gladiator          | 155          | Russell Crowe       | Historical    | 2000         | 8.5    |
| The Matrix         | 136          | Keanu Reeves        | Sci-Fi        | 1999         | 8.7    |
| Interstellar       | 169          | Matthew McConaughey | Sci-Fi        | 2014         | 8.6    |
| The Revenant       | 156          | Leonardo DiCaprio   | Drama         | 2015         | 8.0    |
| Batman Begins      | 140          | Christian Bale      | Action        | 2005         | 8.3    |
| 300                | 117          | Gerard Butler       | Historical    | 2006         | 7.6    |
| John Wick          | 101          | Keanu Reeves        | Action        | 2014         | 7.9    |
| Avatar             | 162          | Sam Worthington     | Sci-Fi        | 2009         | 7.8    |
| The Lion King      | 88           | Matthew Broderick   | Animation     | 1994         | 8.5    |
| Gladiator 2        | 150          | Russell Crowe       | Historical    | 2023         | 8.1    |
| The Dark Knight Rises | 164        | Christian Bale      | Action        | 2012         | 8.4    |
| The Matrix Reloaded| 138          | Keanu Reeves        | Sci-Fi        | 2003         | 7.2    |

---

### SQL Practice Questions

#### **GROUP BY and Aggregate Functions:**
1. Find the average movie length for each genre.
2. Group movies by release year and find the average rating for each year.
3. Find the total number of movies released per year.
4. Find the highest rating per genre.
5. Calculate the total movie length for each genre.
6. Group by lead artist and find the number of movies they starred in.
7. Find the minimum rating for each genre.
8. Find the maximum movie length for each genre.
9. Group movies by lead artist and find the average rating of their movies.
10. Find the total movie length of all movies in 2000.
11. Find the total number of movies with ratings above 8.0.
12. Calculate the average movie length for movies released before 2005.
13. Find the minimum and maximum rating for each release year.
14. Calculate the average rating for each genre.
15. Find the number of movies with ratings above the average for their genre.

#### **ORDER BY:**
16. List all movies ordered by rating in descending order.
17. List all movies ordered by release year in ascending order.
18. List all movies ordered by movie length in descending order.
19. List movies ordered by rating and then by movie length (both descending).
20. List the top 3 highest-rated movies.
21. List the 2 longest movies.
22. List the 3 oldest movies.
23. Sort movies by rating, then by release year in ascending order.
24. Sort the movies by lead artist in alphabetical order.
25. List the movies ordered by movie length and then by rating.
26. Show the top 4 movies released after 2005, ordered by their ratings.

#### **LIMIT:**
27. Retrieve the first 3 movies in the table.
28. Retrieve the top 2 movies with the highest rating.
29. Show 4 movies released before 2000.
30. Retrieve the last 2 movies in the table based on release year.
31. Retrieve the top 3 longest movies.
32. Retrieve the movies with ratings higher than 8.5, limited to 3 results.
33. Limit the results to the 5 most recent movies.
34. Retrieve the top 2 movies of each genre.
35. Show only the movie(s) with the highest rating.
36. Show the first 3 movies sorted by movie length.

#### **Aggregate Functions (SUM, AVG, MIN, MAX):**
37. Find the sum of movie lengths for all movies.
38. Find the average movie length for all movies.
39. Find the highest movie rating in the table.
40. Find the lowest movie length in the table.
41. Find the sum of ratings for all movies released after 2005.
42. Find the average movie length for movies with ratings above 8.0.
43. Find the highest-rated movie released before 2000.
44. Calculate the average rating for movies in the "Action" genre.
45. Find the minimum movie length for movies released before 2000.
46. Find the sum of all ratings for movies released after 1999.
47. Find the maximum movie length for movies with ratings above 8.0.
48. Find the average length of movies starring "Leonardo DiCaprio."
49. Find the sum of movie lengths for all movies in the "Sci-Fi" genre.
50. Find the average movie rating for movies released before 2000.

---

Certainly! Below are SQL queries for the practice questions based on the updated **Movies** table.

### **GROUP BY and Aggregate Functions:**

1. **Find the average movie length for each genre:**
   ```sql
   SELECT Genre, AVG(Movie_Length) AS Avg_Length
   FROM Movies
   GROUP BY Genre;
   ```

2. **Group movies by release year and find the average rating for each year:**
   ```sql
   SELECT Release_Year, AVG(Rating) AS Avg_Rating
   FROM Movies
   GROUP BY Release_Year;
   ```

3. **Find the total number of movies released per year:**
   ```sql
   SELECT Release_Year, COUNT(*) AS Total_Movies
   FROM Movies
   GROUP BY Release_Year;
   ```

4. **Find the highest rating per genre:**
   ```sql
   SELECT Genre, MAX(Rating) AS Max_Rating
   FROM Movies
   GROUP BY Genre;
   ```

5. **Calculate the total movie length for each genre:**
   ```sql
   SELECT Genre, SUM(Movie_Length) AS Total_Length
   FROM Movies
   GROUP BY Genre;
   ```

6. **Group by lead artist and find the number of movies they starred in:**
   ```sql
   SELECT Lead_Artist, COUNT(*) AS Movie_Count
   FROM Movies
   GROUP BY Lead_Artist;
   ```

7. **Find the minimum rating for each genre:**
   ```sql
   SELECT Genre, MIN(Rating) AS Min_Rating
   FROM Movies
   GROUP BY Genre;
   ```

8. **Find the maximum movie length for each genre:**
   ```sql
   SELECT Genre, MAX(Movie_Length) AS Max_Length
   FROM Movies
   GROUP BY Genre;
   ```

9. **Group movies by lead artist and find the average rating of their movies:**
   ```sql
   SELECT Lead_Artist, AVG(Rating) AS Avg_Rating
   FROM Movies
   GROUP BY Lead_Artist;
   ```

10. **Find the total movie length of all movies in 2000:**
    ```sql
    SELECT SUM(Movie_Length) AS Total_Length
    FROM Movies
    WHERE Release_Year = 2000;
    ```

11. **Find the total number of movies with ratings above 8.0:**
    ```sql
    SELECT COUNT(*) AS Movies_Above_8
    FROM Movies
    WHERE Rating > 8.0;
    ```

12. **Calculate the average movie length for movies released before 2005:**
    ```sql
    SELECT AVG(Movie_Length) AS Avg_Length
    FROM Movies
    WHERE Release_Year < 2005;
    ```

13. **Find the minimum and maximum rating for each release year:**
    ```sql
    SELECT Release_Year, MIN(Rating) AS Min_Rating, MAX(Rating) AS Max_Rating
    FROM Movies
    GROUP BY Release_Year;
    ```

14. **Calculate the average rating for each genre:**
    ```sql
    SELECT Genre, AVG(Rating) AS Avg_Rating
    FROM Movies
    GROUP BY Genre;
    ```

15. **Find the number of movies with ratings above the average for their genre:**
    ```sql
    SELECT Genre, COUNT(*) AS Movies_Above_Avg
    FROM Movies
    WHERE Rating > (SELECT AVG(Rating) FROM Movies WHERE Genre = Movies.Genre)
    GROUP BY Genre;
    ```

### **ORDER BY:**

16. **List all movies ordered by rating in descending order:**
    ```sql
    SELECT * FROM Movies
    ORDER BY Rating DESC;
    ```

17. **List all movies ordered by release year in ascending order:**
    ```sql
    SELECT * FROM Movies
    ORDER BY Release_Year ASC;
    ```

18. **List all movies ordered by movie length in descending order:**
    ```sql
    SELECT * FROM Movies
    ORDER BY Movie_Length DESC;
    ```

19. **List movies ordered by rating and then by movie length (both descending):**
    ```sql
    SELECT * FROM Movies
    ORDER BY Rating DESC, Movie_Length DESC;
    ```

20. **List the top 3 highest-rated movies:**
    ```sql
    SELECT * FROM Movies
    ORDER BY Rating DESC
    LIMIT 3;
    ```

21. **List the 2 longest movies:**
    ```sql
    SELECT * FROM Movies
    ORDER BY Movie_Length DESC
    LIMIT 2;
    ```

22. **List the 3 oldest movies:**
    ```sql
    SELECT * FROM Movies
    ORDER BY Release_Year ASC
    LIMIT 3;
    ```

23. **Sort movies by rating, then by release year in ascending order:**
    ```sql
    SELECT * FROM Movies
    ORDER BY Rating DESC, Release_Year ASC;
    ```

24. **Sort the movies by lead artist in alphabetical order:**
    ```sql
    SELECT * FROM Movies
    ORDER BY Lead_Artist ASC;
    ```

25. **List the movies ordered by movie length and then by rating:**
    ```sql
    SELECT * FROM Movies
    ORDER BY Movie_Length DESC, Rating DESC;
    ```

26. **Show the top 4 movies released after 2005, ordered by their ratings:**
    ```sql
    SELECT * FROM Movies
    WHERE Release_Year > 2005
    ORDER BY Rating DESC
    LIMIT 4;
    ```

### **LIMIT:**

27. **Retrieve the first 3 movies in the table:**
    ```sql
    SELECT * FROM Movies
    LIMIT 3;
    ```

28. **Retrieve the top 2 movies with the highest rating:**
    ```sql
    SELECT * FROM Movies
    ORDER BY Rating DESC
    LIMIT 2;
    ```

29. **Show 4 movies released before 2000:**
    ```sql
    SELECT * FROM Movies
    WHERE Release_Year < 2000
    LIMIT 4;
    ```

30. **Retrieve the last 2 movies in the table based on release year:**
    ```sql
    SELECT * FROM Movies
    ORDER BY Release_Year DESC
    LIMIT 2;
    ```

31. **Retrieve the top 3 longest movies:**
    ```sql
    SELECT * FROM Movies
    ORDER BY Movie_Length DESC
    LIMIT 3;
    ```

32. **Retrieve the movies with ratings higher than 8.5, limited to 3 results:**
    ```sql
    SELECT * FROM Movies
    WHERE Rating > 8.5
    LIMIT 3;
    ```

33. **Limit the results to the 5 most recent movies:**
    ```sql
    SELECT * FROM Movies
    ORDER BY Release_Year DESC
    LIMIT 5;
    ```

34. **Retrieve the top 2 movies of each genre:**
    ```sql
    SELECT * FROM (
        SELECT * FROM Movies
        ORDER BY Rating DESC
    ) AS SortedMovies
    GROUP BY Genre
    LIMIT 2;
    ```

35. **Show only the movie(s) with the highest rating:**
    ```sql
    SELECT * FROM Movies
    WHERE Rating = (SELECT MAX(Rating) FROM Movies);
    ```

36. **Show the first 3 movies sorted by movie length:**
    ```sql
    SELECT * FROM Movies
    ORDER BY Movie_Length DESC
    LIMIT 3;
    ```

### **Aggregate Functions (SUM, AVG, MIN, MAX):**

37. **Find the sum of movie lengths for all movies:**
    ```sql
    SELECT SUM(Movie_Length) AS Total_Length
    FROM Movies;
    ```

38. **Find the average movie length for all movies:**
    ```sql
    SELECT AVG(Movie_Length) AS Avg_Length
    FROM Movies;
    ```

39. **Find the highest movie rating in the table:**
    ```sql
    SELECT MAX(Rating) AS Max_Rating
    FROM Movies;
    ```

40. **Find the lowest movie length in the table:**
    ```sql
    SELECT MIN(Movie_Length) AS Min_Length
    FROM Movies;
    ```

41. **Find the sum of ratings for all movies released after 2005:**
    ```sql
    SELECT SUM(Rating) AS Total_Rating
    FROM Movies
    WHERE Release_Year > 2005;
    ```

42. **Find the average movie length for movies with ratings above 8.0:**
    ```sql
    SELECT AVG(Movie_Length) AS Avg_Length
    FROM Movies
    WHERE Rating > 8.0;
    ```

43. **Find the highest-rated movie released before 2000:**
    ```sql
    SELECT * FROM Movies
    WHERE Release_Year < 2000
    ORDER BY Rating DESC
    LIMIT 1;
    ```

44. **Calculate the average rating for movies in the "Action" genre:**
    ```sql
    SELECT AVG(Rating) AS Avg_Rating
    FROM Movies
    WHERE Genre = 'Action';
    ```

45. **Find the minimum movie length for movies released before 2000:**
    ```sql
    SELECT MIN(Movie_Length) AS Min_Length
    FROM Movies
    WHERE Release_Year < 2000;
    ```

46. **Find the sum of all ratings for movies released after 1999:**
    ```sql
    SELECT SUM(Rating) AS Total_Rating
    FROM Movies
    WHERE Release_Year > 1999;
    ```

47. **Find the maximum movie length for movies with ratings above 8.0:**
    ```sql
    SELECT MAX(Movie_Length) AS Max_Length
    FROM Movies
    WHERE Rating > 8.0;
    ```

48. **Find the average length of movies starring "Leonardo DiCaprio":**
    ```sql
    SELECT AVG(Movie_Length) AS Avg_Length
    FROM Movies
    WHERE Lead_Artist = 'Leonardo DiCaprio';
    ```

49. **Find the sum of movie lengths for all movies in the "Sci-Fi" genre:**
    ```sql
    SELECT SUM(Movie_Length) AS Total_Length
    FROM Movies
    WHERE Genre = 'Sci-Fi';
    ```

50. **Find the average movie rating for movies released before 2000:**
    ```sql
    SELECT AVG(Rating) AS Avg_Rating
    FROM Movies
    WHERE Release_Year < 2000;
    ```

---

These queries cover a wide variety of SQL functions and concepts like `GROUP BY`, `ORDER BY`, `LIMIT`, and aggregate functions. Let me know if you need any further explanations or modifications!
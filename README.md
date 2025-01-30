# NETFLIX MOVIE AND TV SHOWS DATA ANALYSIS USING MYSQL
![NETFLIX LOGO](https://github.com/heisenberg904-star/netflix_sql/blob/main/NETFLIX_LOGO.jpg)

## OBJECTIVE
This project analyzes Netflix's content library using SQL to derive business insights. It includes querying content trends, identifying popular genres, understanding regional distributions, and evaluating director and cast contributions. The goal is to optimize content strategy and enhance decision-making for streaming services.


## Project Overview
This project aims to analyze Netflix's content library using SQL queries to extract business insights. The dataset includes information about Netflix movies and TV shows, such as title, director, cast, country, release year, rating, duration, genres, and date added to the platform.


## Dataset
The dataset used for this project consists of the following columns:
- **show_id**: Unique identifier for each content item.
- **type**: Specifies whether the content is a "Movie" or "TV Show".
- **title**: Name of the content.
- **director**: Name of the director (if available).
- **cast**: List of cast members.
- **country**: Country of production.
- **date_added**: The date the content was added to Netflix.
- **release_year**: The year the content was released.
- **rating**: Content rating (e.g., PG-13, TV-MA).
- **duration**: Length of the content (e.g., "90 min" or "2 Seasons").
- **listed_in**: Categories or genres.
- **description**: Brief description of the content.

## SQL Queries
The SQL queries in this project are divided into three categories:

### 1. Easy Questions (10 queries)
These queries retrieve basic insights such as the number of movies and TV shows, unique countries, distinct ratings, and specific genre-based searches.

### 2. Medium Questions (10 queries)
These queries include filtering by date, identifying frequent directors, categorizing genres, and calculating average release years for TV Shows.

### 3. Advanced Questions (6 queries)
These queries analyze deeper business aspects such as top countries producing content, content release trends, percentage calculations of Movies vs. TV Shows, and year-over-year content growth.

**10 easy level question**

### 1)Retrieve the titles of all movies.
Solution:

```sql
SELECT TITLE FROM NETFLIX_SQL WHERE TYPE="MOVIE";
```
### 2)List the distinct countries where Netflix content is produced.

Solution:

```sql
SELECT DISTINCT COUNTRY FROM NETFLIX_SQL;
```

### 3)Count the total number of TV Shows in the dataset.

Solution:
```sql
SELECT COUNT(*) AS total_tv_shows FROM NETFLIX_SQL WHERE type = 'TV Show';
```
### 4)Find the earliest release year of Netflix content.

Solution:

```sql
SELECT MIN(RELEASE_YEAR) AS EARLIEST_YEAR FROM NETFLIX_SQL;
```
### 5)Retrieve all content added in 2021.
Solution:
```sql
SELECT * FROM NETFLIX_SQL WHERE DATE_ADDED LIKE "%2021";
```
### 6)Get all unique content ratings available.
Solution:
```sql
SELECT DISTINCT RATING FROM NETFLIX_SQL;
```
### 7)List all the content directed by a specific director, e.g., 'Kirsten Johnson'.
Solution:
```sql
SELECT TITLE FROM NETFLIX_SQL WHERE DIRECTOR="KIRSTEN JONHSON";
```
### 8)Count the number of movies and TV shows separately.
Solution:
```sql 
SELECT type, COUNT(*) AS count FROM NETFLIX_SQL GROUP BY type;
```
### 9)Retrieve the titles of content available in the genre "Documentaries".
Solution:
```sql
SELECT TITLE FROM NETFLIX_SQL WHERE LISTED_IN LIKE "%DOCUMENTARIES%";
```
### 10)Find the total number of movies produced in the United States .
Solution:
```sql 
SELECT COUNT(*) AS TOTAL_MOVIE_US FROM NETFLIX_SQL WHERE TYPE = 'Movie' AND COUNTRY = 'United States';
```
**10 medium level question**

### 11)Find the top 5 most recent content added to Netflix.
Solution:
```sql 
SELECT TITLE,DATE_ADDED FROM NETFLIX_SQL ORDER BY DATE_ADDED DESC LIMIT 5;
```
### 12)List the directors who have directed more than 3 Netflix content items.
Solution:
```sql
SELECT DIRECTOR,COUNT(*) AS COUNT FROM NETFLIX_SQL
WHERE DIRECTOR IS NOT NULL GROUP BY DIRECTOR HAVING COUNT>3;
```
 ### 13)Retrieve all content added in September, regardless of the year.
Solution:
```sql
SELECT *FROM NETFLIX_SQL WHERE DATE_ADDED LIKE "SEPTEMBER%";
```
### 14) Find all movies released after 2015 with a "PG-13" rating.
Solution:
```sql
SELECT TITLE FROM NETFLIX_SQL WHERE TYPE="MOVIE" AND RELEASE_YEAR>2015 AND RATING="PG-13";
```
### 15)List all genres (categories) with their respective counts.
Solution:
```sql
SELECT LISTED_IN ,COUNT(*) AS COUNT FROM NETFLIX_SQL GROUP BY LISTED_IN;
```
### 16)Get the average release year for TV Shows.
Solution:
```sql
SELECT AVG(RELEASE_YEAR) AS AVERAGE_RELEASE_YEAR FROM NETFLIX_SQL WHERE TYPE='TV SHOW';
```
### 17)Find the longest duration for a movie in minutes.
Solution:
```sql
SELECT MAX(DURATION) AS LONGEST_DURATION FROM NETFLIX_SQL WHERE TYPE="MOVIE";
```
### 18)Retrieve the total number of movies by year of release.
Solution:
```sql
SELECT RELEASE_YEAR, COUNT(*) AS MOVIE_COUNT FROM NETFLIX_SQL WHERE TYPE = 'MOVIE' GROUP BY RELEASE_YEAR;
```

### 19)Get all TV shows that have more than one season.
Solution:
```sql
SELECT TITLE FROM NETFLIX_SQL WHERE TYPE="TV SHOW" AND DURATION LIKE "%SEASON%";
```
### 20)Identify the top 3 countries with the highest number of Netflix content.
Solution:
```sql
SELECT COUNTRY, COUNT(*) AS CONTENT_COUNT FROM NETFLIX_SQL 
WHERE COUNTRY IS NOT NULL GROUP BY COUNTRY ORDER BY CONTENT_COUNT DESC LIMIT 3;
```
**6 advance level question**

### 21)Find all TV Shows released in the last 5 years that belong to the genre "Crime TV Shows".
Solution:
```sql
SELECT TITLE FROM NETFLIX_SQL 
WHERE TYPE = 'TV Show' AND RELEASE_YEAR >= YEAR(CURDATE()) - 5 
AND LISTED_IN LIKE '%Crime TV Shows%';
```
### 22)Calculate the percentage of TV Shows vs. Movies in the dataset.
Solution:
```sql
SELECT TYPE,(COUNT(*)*100 / (SELECT COUNT(*) FROM NETFLIX_SQL)) AS PERCENTAGE
FROM NETFLIX_SQL GROUP BY TYPE;
```
### 23)List all the directors with more than 5 movies or shows in a specific country (e.g., India).
Solution:
```sql
SELECT DIRECTOR,COUNT(*) AS COUNT FROM NETFLIX_SQL WHERE COUNTRY="INDIA" 
AND DIRECTOR IS NOT NULL GROUP BY DIRECTOR HAVING COUNT>5;
```
### 24)Retrieve the year with the highest number of Netflix content added.
Solution:
```sql
SELECT YEAR(STR_TO_DATE(DATE_ADDED, '%M %D, %Y')) AS YEAR, COUNT(*) AS COUNT 
FROM NETFLIX_SQL
GROUP BY YEAR ORDER BY COUNT DESC LIMIT 1;
```

### 25)Analyze content trends: Find the year-over-year growth in Netflix content added.
Solution:
```sql
SELECT YEAR(STR_TO_DATE(DATE_ADDED, '%M %D, %Y')) AS YEAR, COUNT(*) AS COUNT 
FROM NETFLIX_SQL
GROUP BY YEAR ORDER BY YEAR;
```
### 26)Find all content with a duration between 60 and 120 minutes.
Solution:
```sql
SELECT TITLE FROM NETFLIX_SQL
WHERE TYPE="MOVIE" AND CAST(SUBSTRING_INDEX(DURATION,'',1) AS UNSIGNED) BETWEEN 60 AND 120;
```

## Usage
1. Load the Netflix dataset into a relational database.
2. Execute the provided SQL queries to extract meaningful insights.
3. Utilize the results to understand Netflix content trends and support business decision-making.

## Conclusion
This project provides a comprehensive SQL-based analysis of Netflix's content, helping businesses and analysts make data-driven decisions regarding content strategy, regional expansion, and genre trends.


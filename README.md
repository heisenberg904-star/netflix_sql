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

**10 easy question**

### 1)Retrieve the titles of all movies.
'''sql

SELECT TITLE FROM NETFLIX_SQL WHERE TYPE="MOVIE";

'''

## Usage
1. Load the Netflix dataset into a relational database.
2. Execute the provided SQL queries to extract meaningful insights.
3. Utilize the results to understand Netflix content trends and support business decision-making.

## Conclusion
This project provides a comprehensive SQL-based analysis of Netflix's content, helping businesses and analysts make data-driven decisions regarding content strategy, regional expansion, and genre trends.


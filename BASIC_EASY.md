# Basic and Easy

[HackerRank SQL (Basic, Solved, Easy) Challenges](https://www.hackerrank.com/domains/sql?filters%5Bskills%5D%5B%5D=SQL%20%28Basic%29&filters%5Bstatus%5D%5B%5D=solved&filters%5Bdifficulty%5D%5B%5D=easy
)

## Select All

https://www.hackerrank.com/challenges/select-all-sql/problem?isFullScreen=true

Query all columns (attributes) for every row in the `CITY` table.

```sql
SELECT *
FROM CITY;
```

## Select By ID

https://www.hackerrank.com/challenges/select-by-id/problem?isFullScreen=true

Query all columns for a city in `CITY` with the ID `1661`.

```sql
SELECT *
FROM CITY
WHERE ID = 1661;
```

## Japanese Cities' Attributes

https://www.hackerrank.com/challenges/japanese-cities-attributes/problem?isFullScreen=true

Query all attributes of every Japanese city in the `CITY` table. The `COUNTRYCODE` for Japan is `JPN`.

```sql
SELECT *
FROM CITY
WHERE COUNTRYCODE = 'JPN';
```

## Japanese Cities' Names

https://www.hackerrank.com/challenges/japanese-cities-name/problem?isFullScreen=true

Query the names of all the Japanese cities in the `CITY` table. The `COUNTRYCODE` for Japan is `JPN`.

```sql
SELECT NAME
FROM CITY
WHERE COUNTRYCODE = 'JPN';
```

## Revising the Select Query I

https://www.hackerrank.com/challenges/revising-the-select-query/problem?isFullScreen=true

Query all columns for all American cities in the `CITY` table with populations larger than `100000`. The `CountryCode`
for America is `USA`.

```sql
SELECT *
FROM CITY
WHERE COUNTRYCODE = 'USA'
    AND POPULATION > 100000;
```

## Revising the Select Query II

https://www.hackerrank.com/challenges/revising-the-select-query-2/problem?isFullScreen=true

Query the `NAME` field for all American cities in the `CITY` table with populations larger than `120000`. The
`CountryCode` for America is `USA`.

```sql
SELECT NAME
FROM CITY
WHERE COUNTRYCODE = 'USA'
    AND POPULATION > 120000;
```

## Weather Observation Station 1

https://www.hackerrank.com/challenges/weather-observation-station-1/problem?isFullScreen=true

Query a list of `CITY` and `STATE` from the `STATION` table.

```sql
SELECT CITY, STATE
FROM STATION;
```

## Weather Observation Station 2

https://www.hackerrank.com/challenges/weather-observation-station-2/problem?isFullScreen=true

Query the following two values from the `STATION` table:

The sum of all values in `LAT_N` rounded to a scale of `2` decimal places.
The sum of all values in `LONG_W` rounded to a scale of `2` decimal places.

```sql
SELECT ROUND(SUM(LAT_N), 2) AS SUM_LAT_N,
       ROUND(SUM(LONG_W), 2) AS SUM_LONG_W
FROM STATION;
```

## Weather Observation Station 3

https://www.hackerrank.com/challenges/weather-observation-station-3/problem?isFullScreen=true

Query a list of `CITY` names from `STATION` for cities that have an even `ID` number. Print the results in any order,
but exclude duplicates from the answer.

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE ID % 2 = 0;
```

## Weather Observation Station 4

https://www.hackerrank.com/challenges/weather-observation-station-4/problem?isFullScreen=true

Find the difference between the total number of `CITY` entries in the table and the number of distinct `CITY` entries in
the table.

```sql
SELECT COUNT(CITY) - COUNT(DISTINCT CITY) as CITY_DIFFERECE
FROM STATION;
```

## Weather Observation Station 5

https://www.hackerrank.com/challenges/weather-observation-station-5/problem

```sql
SELECT CITY, LENGTH(CITY) AS NAME_LENGTH
FROM STATION
ORDER BY NAME_LENGTH ASC, CITY ASC
LIMIT 1;

SELECT CITY, LENGTH(CITY) AS NAME_LENGTH
FROM STATION
ORDER BY NAME_LENGTH DESC, CITY ASC
LIMIT 1;
```

**Explanation**:

* Shortest City Name:
  * Orders the cities by `LENGTH(CITY)` in ascending order to get the **shortest name**.
  * If there is a tie, it sorts alphabetically (**ORDER BY CITY ASC**).
  * Limits the output to just one result (**LIMIT 1**).

* Shortest City Name:
  * Orders the cities by `LENGTH(CITY)` in descending order to get the **longest name**.
  * Resolves ties by sorting alphabetically (`ORDER BY CITY ASC`).
  * Limits the output to just one result (`LIMIT 1`).

```sql
SELECT CITY, LENGTH(CITY) AS NAME_LENGTH
FROM STATION
WHERE LENGTH(CITY) = (SELECT MIN(LENGTH(CITY)) FROM STATION)
ORDER BY CITY ASC
LIMIT 1;

SELECT CITY, LENGTH(CITY) AS NAME_LENGTH
FROM STATION
WHERE LENGTH(CITY) = (SELECT MAX(LENGTH(CITY)) FROM STATION)
ORDER BY CITY ASC
LIMIT 1;
```

**Explanation**:

* Shortest City Name:
  * Find the minimum length using `MIN(LENGTH(CITY))`
  * Filter the cities where the length matches this minimum
  * Order alphabetically (`ORDER BY CITY ASC`)
  * Use `LIMIT 1` to select the first one alphabetically in case of ties

* Shortest City Name:
  * Find the maximum length using `MAX(LENGTH(CITY))`
  * Filter the cities where the length matches this maximum
  * Order alphabetically (`ORDER BY CITY ASC`)
  * Use `LIMIT 1` to select the first one alphabetically in case of ties

## Weather Observation Station 6

https://www.hackerrank.com/challenges/weather-observation-station-6/problem?isFullScreen=true

Query the list of `CITY` names starting with vowels `(i.e., a, e, i, o, or u)` from `STATION`. Your result cannot
contain duplicates.

```sql
SELECT CITY
FROM STATION
WHERE LOWER(LEFT(CITY, 1)) IN ('a', 'e', 'i', 'o', 'u');
```

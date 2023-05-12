# https://pgexercises.com

## 1. Simple SQL Queries - basic

### 1.1 Retrieve everything from a table - selectall

```sql
SELECT * FROM cd.facilities;
```

### 1.2 Retrieve specific columns from a table - selectspecific

```sql
SELECT name, membercost FROM cd.facilities;
```

### 1.3 Control which rows are retrieved - where

```sql
SELECT * FROM cd.facilities WHERE membercost > 0;
```

### 1.4 Control which rows are retrieved - part 2 - where2

```sql
SELECT facid, name, membercost, monthlymaintenance
FROM cd.facilities
WHERE (membercost / monthlymaintenance) <= 0.02
AND membercost > 0;
```

### 1.5 Basic string searches - where3

```sql
SELECT * FROM cd.facilities
WHERE name LIKE '%Tennis%';
```

### 1.6 Matching against multiple possible values - where4

```sql
SELECT * FROM cd.facilities
WHERE facid IN (1, 5);
```

### 1.7 Classify results into buckets - classify

```sql
SELECT name,
CASE
  WHEN monthlymaintenance > 100
	THEN 'expensive'
	ELSE 'cheap'
END
AS cost
FROM cd.facilities;
```

### 1.8 Working with dates - date

```sql
SELECT memid, surname, firstname, joindate
FROM cd.members
WHERE joindate >= '2012-09-01';
```

### 1.9 Removing duplicates, and ordering results - unique

```sql
SELECT DISTINCT surname
FROM cd.members
ORDER BY surname ASC
LIMIT 10;
```

### 1.10 Combining results from multiple queries - union

```sql
SELECT surname FROM cd.members
UNION
SELECT name FROM cd.facilities;
```

### 1.11 Simple aggregation - agg

```sql
SELECT MAX(joindate) AS latest
FROM cd.members;
```

### 1.12 More aggregation - agg2

```sql
SELECT firstname, surname, joindate
FROM cd.members
WHERE joindate = (SELECT MAX(joindate) FROM cd.members);
```

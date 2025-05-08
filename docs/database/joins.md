# Joins in SQL

Joins in SQL are used to combine rows from two or more tables based on a related column between them. They allow you to retrieve data that is spread across multiple tables in a relational database.

## Types of Joins

### 1. **Inner Join**
An inner join returns only the rows where there is a match in both tables.

```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. **Left Join (or Left Outer Join)**
A left join returns all rows from the left table and the matching rows from the right table. If no match is found, NULL values are returned for columns from the right table.

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```

### 3. **Right Join (or Right Outer Join)**
A right join returns all rows from the right table and the matching rows from the left table. If no match is found, NULL values are returned for columns from the left table.

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```

### 4. **Full Join (or Full Outer Join)**
A full join returns all rows when there is a match in either table. If there is no match, NULL values are returned for the non-matching rows.

```sql
SELECT columns
FROM table1
FULL JOIN table2
ON table1.column = table2.column;
```

### 5. **Cross Join**
A cross join returns the Cartesian product of the two tables, meaning every row in the first table is combined with every row in the second table.

```sql
SELECT columns
FROM table1
CROSS JOIN table2;
```

### 6. **Self Join**
A self join is a join where a table is joined with itself. It is useful for comparing rows within the same table.

```sql
SELECT a.column, b.column
FROM table a
INNER JOIN table b
ON a.column = b.column;
```

### 7. **Natural Join**
A natural join automatically joins tables based on columns with the same name and compatible data types.

```sql
SELECT columns
FROM table1
NATURAL JOIN table2;
```

## Summary Table

| Join Type       | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| Inner Join       | Returns rows with matching values in both tables.                         |
| Left Join        | Returns all rows from the left table and matched rows from the right.     |
| Right Join       | Returns all rows from the right table and matched rows from the left.     |
| Full Join        | Returns rows when there is a match in either table.                       |
| Cross Join       | Returns the Cartesian product of both tables.                             |
| Self Join        | Joins a table with itself.                                                |
| Natural Join     | Automatically joins tables based on common column names.                 |

---
Title: DBS101 Flipped Class 3
categories: [DBS101, Flipped_Class3]
tags: [DBS101]
---

### TOPIC: SET OPERATIONS AND NULL VALUES IN SQL
---

The flipped class was conducted on the topic null values and set operations in SQL. For this flipped class, students were diveded into 4 groups making up 2 expert groups to learn more on specific topic - group 1 learning about set operations in SQL and group 2 learning about null values in SQL. We were given 30 mins each for reading the materials, discussing and explaining within expert group and presenting it to the home group. At the end of this flipped class we were expected to know what a null value is, how they are handled, importance and principles of null value and types of set operations.

### SET OPERATORS
SET operators are used to combine the result of two queries. To be able to perform SET operators in SQL, datatypes must be compatible and the number and order of columns must be same.
The SET operators are UNION, UNION ALL, INTERSECT and MINUS.

- UNION - It is used to combine the result sets of two SELECT statements in which all duplicates are removed and only unique rows from both sets are returned.
- UNION ALL - It combines all the records from both sets and the duplicates are not removed.
- INTERSECT - It is used to combine two SELECT statements  which only returns the common rows. 
- MINUS - It displays the rows which are present in the first query but absent in the second query with no duplicates.


### NULL VALUES 
A field with no values are known as NULL values and it is not a zero value or just space. NULL values are those values in which there is no data value in the particular field in the table. IS NULL and IS NOT NULL operators are used to look for NULL values. IS NULL operator is used to test for empty values while IS NOT NULL is usee to test for non-empty values. NULL values hold a specific meanings related to the absence of information.
NULL values usually have these three interpretations i.e 
~The value unknown (the actual value exists but is not known or not recorded in the database)
~Value not available (the value exists but it is intentionally withheld)
~Attribute not applicable (attribute or field is not applicable or undefined for a specific tuple), but the SQL does not distinguish between the different meanings of NULL.

### KEY TAKEAWAY 
- When a value doesnt make sense or is unknown, it is best to set a NULL value.
- A NULL value is NOT a zero.
- A NULL value can be inserted into columns of any datatype.
- The result of a expression is considered to be NULL when NULL values are involved in the expression.
- Constraints such as UNIQUE, FOREIGN KEY, and CHECK may ignore rows with NULL values.

### Experience
Today's flipped class topic was easy to understand and expert groups did a good job in discussing and understanding their topic well and was able to explain it well to the home groups and I understood the lesson .
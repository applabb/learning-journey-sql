# SQL Learning Progress - July 13, 2024

## Topics Covered

1. The Basics of Database Structures
2. The SQL Stack
3. The SQLite Database Environment
4. Composing Queries
   - Queries
   - Query commenting
   - Query composition
   - Query composition best practices
   - Column custom names
   - Sorting query results
   - Limiting query results
   - Code Challenge: Concise track pricing report
   - Solution: Concise track pricing report
   - Chapter Quiz
5. Discovering Insights in Data
   - Types of SQL operators
   - Filter and analyze numeric data
   - BETWEEN and IN operators
   - Filter and analyze text data
   - Search records without an exact match
   - Filter and analyze using dates
   - Filter records based on more than one condition
   - Logical operator OR
   - Brackets and order
   - IF THEN logic with CASE
   - Code Challenge: Categorize tracks by price
   - Solution: Categorize tracks by price
   - Chapter Quiz

## Code Snippets

### 1. Categorizing Tracks by Price

```sql
SELECT t.Name AS "Track Name", t.Composer, t.UnitPrice AS Price,
CASE
WHEN UnitPrice <= 0.99 THEN 'Budget'
WHEN UnitPrice BETWEEN 1.00 AND 1.49 THEN 'Regular'
WHEN UnitPrice BETWEEN 1.50 AND 1.99 THEN 'Premium'
ELSE 'Exclusive'
END AS PriceCategory
FROM Track AS t 
ORDER BY t.UnitPrice;
```

### 2. Analyzing Purchase Types (Version 1)

```sql
/*
WSDA Music Sales Goal:
They want as many customers as possible to spend between $7.00 and $15.00
Sales Categories:
Baseline Purchase - Between $0.99 and $1.99
Low Purchase - Between $2.00 and $6.99
Target Purchase - Between $7.00 and $15.00
Top Performer - Above $15.00
Created by: Firat
Created Date: 07/13/2024
Description: Get all invoices that are greater than 1.98 from any cities whose name start with P or starts with D?
*/
SELECT
InvoiceDate, BillingAddress, BillingCity, total,
CASE WHEN total < 2.00 THEN 'Baseline Purchase'
WHEN total Between 2.00 and 6.99 THEN 'Low Purchase'
WHEN total Between 7.00 and 15.00 THEN 'Target Purchase'
ELSE 'Top Performer'
END AS PurchaseType
FROM Invoice
WHERE PurchaseType = 'Top Performer'
ORDER BY total DESC
```

### 3. Analyzing Purchase Types (Version 2)

```sql
/*
WSDA Music Sales Goal:
They want as many customers as possible to spend between $7.00 and $15.00
Sales Categories:
Baseline Purchase - Between $0.99 and $1.99
Low Purchase - Between $2.00 and $6.99
Target Purchase - Between $7.00 and $15.00
Top Performer - Above $15.00
Created by: Firat
Created Date: 07/13/2024
Description: Get all invoices that are greater than 1.98 from any cities whose name start with P or starts with D?
*/
SELECT
InvoiceDate, BillingAddress, BillingCity, total,
CASE WHEN total < 2.00 THEN 'Baseline Purchase'
WHEN total Between 2.00 and 6.99 THEN 'Low Purchase'
WHEN total Between 7.00 and 15.00 THEN 'Target Purchase'
ELSE 'Top Performer'
END AS PurchaseType
FROM Invoice
ORDER BY PurchaseType DESC
```

### 4. Filtering Invoices by City and Total

```sql
/*
Created by: Firat
Created Date: 07/13/2024
Description: Get all invoices that are greater than 1.98 from any cities whose name start with P or starts with D?
*/
SELECT
InvoiceDate, BillingAddress, BillingCity, total
FROM Invoice
WHERE total > 1.98 AND (BillingCity LIKE 'P%' OR BillingCity LIKE 'D%') 
ORDER BY total
```

## Additional Notes

- Several more SQL queries were practiced but not included in this summary.
- The learning session focused on practical application of SQL concepts through various exercises and challenges.
- Key areas of focus included data filtering, categorization, and analysis using SQL.

## Next Steps

- Review and practice the concepts learned today
- Prepare for the upcoming chapter quiz
- Explore more complex SQL queries and database operations


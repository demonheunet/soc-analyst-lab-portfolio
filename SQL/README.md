# SQL Practice Labs: San Francisco Film Locations

This folder contains documentation and screenshots from my hands-on SQL practice sessions using a SQLite database tracking film locations in San Francisco. These labs demonstrate core database querying skills, including filtering, pattern matching, aggregate functions, and pagination.

---

## Lab 1: Using `DISTINCT` and Conditional Filtering (`WHERE`)

This session focuses on eliminating duplicate records using `DISTINCT`, combining columns, filtering by specific years, locations, and actors, and using aggregate functions like `COUNT()`.

| Query Description | SQL Syntax | Screenshot Preview |
| :--- | :--- | :--- |
| **Unique Film Titles** | `SELECT DISTINCT Title FROM FilmLocations;` | ![Distinct Titles](screenshots/sql_distinct_1.png) |
| **Warner Bros. Release Years** | `SELECT COUNT(DISTINCT ReleaseYear) FROM FilmLocations WHERE ProductionCompany="Warner Bros. Pictures";` | ![Warner Bros Years](screenshots/sql_distinct_2.png) |
| **Films Released Since 2001** | `SELECT DISTINCT Title, ReleaseYear FROM FilmLocations WHERE ReleaseYear>=2001;` | ![Films Since 2001](screenshots/sql_distinct_3.png) |
| **City Hall Filming Records** | `SELECT DISTINCT Title, Director FROM FilmLocations WHERE Locations="City Hall";` | ![City Hall Films](screenshots/sql_distinct_4.png) |
| **Clint Eastwood Distributors** | `SELECT COUNT(DISTINCT Distributor) FROM FilmLocations WHERE Actor1="Clint Eastwood";` | ![Clint Eastwood Distributors](screenshots/sql_distinct_5.png) |

---

## Lab 2: Pagination and Result Limiting (`LIMIT` & `OFFSET`)

This session explores controlling result set sizes and pagination using the `LIMIT` and `OFFSET` clauses combined with conditional filtering on specific release years (e.g., 2015).

| Query Description | SQL Syntax | Screenshot Preview |
| :--- | :--- | :--- |
| **Limit Rows** | `SELECT * FROM FilmLocations LIMIT 25;` | ![Limit 25](screenshots/sql_limit_1.png) |
| **Limit with Offset** | `SELECT * FROM FilmLocations LIMIT 15 OFFSET 10;` | ![Limit Offset](screenshots/sql_limit_2.png) |
| **Unique Titles (Limited)** | `SELECT DISTINCT Title FROM FilmLocations LIMIT 15;` | ![Distinct Titles Limit](screenshots/sql_limit_3.png) |
| **Filtered by Year (2015)** | `SELECT DISTINCT Title FROM FilmLocations WHERE ReleaseYear=2015 LIMIT 10;` | ![2015 Limit](screenshots/sql_limit_4.png) |
| **Pagination with Offset (2015)** | `SELECT DISTINCT Title FROM FilmLocations WHERE ReleaseYear=2015 LIMIT 3 OFFSET 5;` | ![2015 Limit Offset](screenshots/sql_limit_5.png) |

---

## Key SQL Skills Demonstrated
* **Data Retrieval:** Writing precise `SELECT` statements across single tables.
* **Deduplication:** Utilizing `DISTINCT` to isolate unique attribute combinations.
* **Aggregation:** Combining `COUNT()` with `DISTINCT` to calculate unique totals under specific conditions.
* **Conditional Filtering:** Applying `WHERE` clauses with comparison operators (`>=`, `=`) and string matching.
* **Result Control:** Managing output volume and pagination using `LIMIT` and `OFFSET`.

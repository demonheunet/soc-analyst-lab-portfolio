# SQL Distinct and Uniqueness Filtering Lab

## Overview
This laboratory module explores data deduplication, cardinal count aggregation, and conditional multi-column projection using SQL `DISTINCT` statements. Working against the **San Francisco Film Locations** relational database, queries evaluate unique film records, eliminate redundant multi-location entries, and combine distinct checks with aggregate functions (`COUNT(DISTINCT ...)`) across specified categorical and numeric attributes.

---

## Environment & Schema Reference
* **Database Platform:** SQLite / Datasette SQL Practice Environment
* **Database:** `SanFranciscoFilmLocations`
* **Table:** `FilmLocations`
* **Target Columns:** `Title`, `ReleaseYear`, `Locations`, `Director`, `ProductionCompany`, `Distributor`, `Actor1`

---

## Query Exercises & Verification

### 1. Extract Unique Film Titles
Retrieves a deduplicated list of all movie titles recorded in the database, eliminating repeated instances caused by multiple filming sites per film.

```sql
SELECT DISTINCT Title FROM FilmLocations;

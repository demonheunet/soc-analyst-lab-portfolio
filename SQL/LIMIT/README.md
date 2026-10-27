# SQL Result Limiting and Pagination Lab

## Overview
This laboratory module demonstrates row-count restriction and pagination strategies using the SQL `LIMIT` and `OFFSET` clauses. Query operations are executed against the **San Francisco Film Locations** relational database to control result set volume, skip leading record offsets, and combine pagination controls with conditional filtering (`WHERE`) and deduplication (`DISTINCT`).

---

## Environment & Schema Reference
* **Platform:** SQLite / Datasette SQL Practice Environment
* **Database:** `SanFranciscoFilmLocations`
* **Table:** `FilmLocations`
* **Columns:** `Title`, `ReleaseYear`, `Locations`, `FunFacts`, `ProductionCompany`, `Distributor`, `Director`, `Writer`, `Actor1`, `Actor2`, `Actor3`

---

## Query Exercises & Verification

### 1. Limit Query Results
Restricts the returned output to the first 25 records from the dataset to prevent excessive data retrieval and optimize query execution.

```sql
SELECT * FROM FilmLocations LIMIT 25;

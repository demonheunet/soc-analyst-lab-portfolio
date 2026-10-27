# SQL SELECT and Conditional Filtering Lab

## Overview
This laboratory module covers fundamental data retrieval and attribute projection techniques using SQL `SELECT` queries and `WHERE` predicate filtering. Executed against the **San Francisco Film Locations** relational database, these exercises demonstrate full-table inspections, multi-column projections, numerical boundary comparisons (`<=`), and inequality pattern exclusions (`<>`).

---

## Environment & Schema Reference
* **Platform:** SQLite / Datasette Practice Environment
* **Database:** `SanFranciscoFilmLocations`
* **Table:** `FilmLocations`
* **Schema Columns:** `Title`, `ReleaseYear`, `Locations`, `FunFacts`, `ProductionCompany`, `Distributor`, `Director`, `Writer`, `Actor1`, `Actor2`, `Actor3`

---

## Query Exercises & Verification

### 1. Full Table Inspection (Wildcard Retrieval)
Inspects the comprehensive structure and initial data records across every available column in the dataset using the wildcard operator (`*`).

```sql
SELECT * FROM FilmLocations;

# SQL Lab: Relational Database Querying & Data Manipulation (DML)

## Overview
This repository contains SQL query implementations and execution logs covering relational table querying (`SELECT`) and record insertion (`INSERT INTO`) using an `Instructors` relational database environment.

---

## Database Schema

### Table: `Instructor`
| Column Name | Data Type / Format | Description |
| :--- | :--- | :--- |
| `ins_id` | Integer (Primary Key) | Unique instructor identifier |
| `lastname` | Varchar / Text | Instructor's last name |
| `firstname` | Varchar / Text | Instructor's first name |
| `city` | Varchar / Text | City of residence |
| `country` | Char(2) / Text | Two-letter country code (e.g., `CA`, `US`, `GB`, `IN`) |

---

## Lab Progression & Queries Executed

### 1. Initial State Query
Verified the starting records stored in the `Instructor` table:

```sql
SELECT * FROM Instructor;

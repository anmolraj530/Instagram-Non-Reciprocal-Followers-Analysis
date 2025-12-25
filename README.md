# Instagram Non-Reciprocal Followers Analysis (MySQL)

## Project Overview
This project identifies Instagram accounts that a user follows but which do not follow back.
The analysis is performed entirely using MySQL on synthetic datasets to simulate real-world data.

## Problem Statement
Given:
- A list of accounts the user follows
- A list of accounts that follow the user

The goal is to find accounts that are followed but do not follow back.

## Tools Used
- MySQL
- SQL Joins (LEFT JOIN)
- CSV-based synthetic datasets

## Dataset Description
- following.csv: Accounts followed by the user (1000 records)
- followers.csv: Accounts that follow the user (500 records)

## Core Logic
A LEFT JOIN is used between the following and followers tables.
If a followed account has no matching record in the followers table, it is considered non-reciprocal.

## SQL Logic
```sql
SELECT f.user_name, f.profile_url
FROM following f
LEFT JOIN followers fr
ON f.user_name = fr.user_name
WHERE fr.user_name IS NULL;

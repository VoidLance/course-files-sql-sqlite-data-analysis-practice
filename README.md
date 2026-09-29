# SQLite Data Analysis Practice

A small, self-contained SQLite practice project for learning relational
database design and data analysis with SQL. It includes a sample movie
database, the SQL used to create it, and query exercises using joins,
sorting, filtering, and aggregation.

## Why use this project?

- Practice SQL against a ready-to-query database without installing a server.
- Explore relationships between movies, genres, and directors.
- Learn to write readable queries against a realistic multi-table dataset.
- Use the database interactively or adapt the scripts for your own exercises.

## Project contents

| File | Description |
| --- | --- |
| [`movies.db`](movies.db) | SQLite database containing the sample data. |
| [`movies.sql`](movies.sql) | SQL dump that recreates the schema and data. |
| [`practice.md`](practice.md) | SQL commands and example analysis queries. |
| [`SPLIT_REPO.md`](SPLIT_REPO.md) | Origin and repository split information. |

The database contains five movies, five genres, and five directors. The
`Movies` table stores titles, release years, genre and director IDs, and
ratings from 0 to 10.

## Getting started

### Prerequisites

Install the [SQLite command-line shell](https://sqlite.org/cli.html). No
additional packages or services are required.

### Open the included database

From the repository root, start an interactive session:

```bash
sqlite3 movies.db
```

Inspect the schema and data:

```sql
.tables
.schema Movies
SELECT title, release_year, rating
FROM Movies
ORDER BY rating DESC;
.quit
```

### Recreate the database from SQL

To create a new copy from the SQL dump:

```bash
sqlite3 practice.db < movies.sql
```

Then query it:

```bash
sqlite3 -header -column practice.db \
  "SELECT title, rating FROM Movies ORDER BY rating DESC LIMIT 3;"
```

### Try a join

Combine movie and genre information:

```sql
SELECT m.title, g.genre_name, m.rating
FROM Movies AS m
JOIN Genres AS g ON g.genre_id = m.genre_id
ORDER BY m.rating DESC;
```

More starter queries are available in [`practice.md`](practice.md).

## Getting help

For questions or problems:

1. Review the setup and example queries above.
2. Check the [SQLite documentation](https://sqlite.org/docs.html).
3. [Open an issue](https://github.com/VoidLance/course-files-sql-sqlite-data-analysis-practice/issues)
   with the command you ran, the expected result, and the actual error.

## Contributing

Contributions are welcome. To propose an improvement:

1. Fork the repository and create a focused branch.
2. Make the change, keeping examples compatible with SQLite.
3. Verify SQL examples against `movies.db` or a database recreated from
   `movies.sql`.
4. Open a pull request describing what changed and why.

Please use issues for larger proposals or questions before starting substantial
work.

## Maintainer

This project is maintained by [VoidLance](https://github.com/VoidLance).


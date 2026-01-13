---
date: '2023-04-30'
title: Javascript SQLite
draft: true
github: https://github.com/dunhamsteve/sqljs
---
sqljs is a toy implementation of a read-only sqlite3 in typescript. It was written as a learning exercise.

This project started out as an exercise to read a sqlite file and dump the table contents as a list of objects. I wrote it to learn a little bit about how sqlite works.

In 2021 I decided to add support for reading indexes and running SQL queries. The code is still a little terse because I was trying to see how far I could do with minimal code.  One catch with that is that SQLite requires you to parse the DDL to know the names of the columns. Also if one of the columns is the identity column (both primary key, integer, and doesn't say `WITHOUT ROWID`), then it is stored differently.

In 2023 I was playing with implementing the client (python) and server (typescript) side of the postgresql protocol to learn how it works. I ended up gluing it onto this project.

I started out with a regex hack to parse the DDL in my initial version. I later replaced by a state machine that is a bit inscrutible and hard to modify. It will eventually be replaced by a parser, like one used for SQL queries.

Reading sqlite3 files is in `src/sqlite.ts`, query parsing is `src/parser.ts`, query execution is `src/eval.ts`, and the postgresql server is `src/server.ts`. The table scanning and query execution are organized as javascript generators because I'd originally intended have it do ranged HTTP queries to fetch the database, but I never got around to implementing that.  I think it would require a bit of complexity to be efficient, possibly violating separation of layers.

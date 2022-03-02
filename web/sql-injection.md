# SQL Injection

One useful information that we may want to retrieve is the DBMS version number. Unfortunately, different DBMS uses different ways to retrieve this information.&#x20;

Some common functions/ways to retrive the database version number are:

* `version()` for MySQL and PostgreSQL
* `@@VERSION` for MSSQL
* `sqlite_version()` for sqlite

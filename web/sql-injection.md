# SQL Injection

One useful information that we may want to retrieve is the DBMS version number. Unfortunately, different DBMS uses different ways to retrieve this information.&#x20;

Some common functions/ways to retrive the database version number are:

* `version()` for MySQL and PostgreSQL
* `@@VERSION` for MSSQL
* `sqlite_version()` for sqlite

{% hint style="info" %}
We can use Google to search the version number and try to infer the DBMS that is actually used.&#x20;
{% endhint %}

We also want to know the available tables and columns in the DB. To this end, there are some tables, like:

* The `tables` table contains a list of all tables accessible by the current user. Its most useful columns are:
  * `table_name`: the name of the table;
  * `table_schema`: the schema that contains the table.
* The `columns` table that contains a list of all the columns of all the tables accessible by the current user. Its most useful columns are:
  * `column_name`: the name of the column;
  * `table_name`: the name of the table that contains the column;
  * `table_schema`: the name of the schema that contains the table that contains the column.

{% hint style="info" %}
Source: [http://sqlinjection.challs.cyberchallenge.it](http://sqlinjection.challs.cyberchallenge.it/union#5)
{% endhint %}

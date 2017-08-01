# Database setup and maintenance :lipstick: 

### Research points

* What is a build script and why do you need one? (think ahead to how this might come in useful when working on a project this week)
* What is database migration?
* Create a build script for a simple database (one or two tables only), which you can run locally. Check that it works for you and everyone on your team

## What are build scripts and why do we need them? :elephant: 

**Build Script**: is for automating the creation of a software build and associated processes. It ensures consistency and repeatability, unlike doing the build manually.

**Build Script for Database**: A build script for a database might have different purposes:
1. initialisation of the database schema for database start up
2. resetting and/or initialising database schema for testing

For creating a postgres database on Heroku see [this page](https://devcenter.heroku.com/articles/heroku-postgresql#create-a-new-database).


## What is database migration? :panda_face: 

Database migration, also known as schema migration, refers to the management of incremental changes to database schemas. A schema migration is performed on a database whenever it is necessary to update or revert that database's schema to some newer or older version.


Database migration allows for fixing mistakes and adapting the data as requirements change. They are an essential part of software evolution, especially in agile environments.

Migrations can be performed by using a schema migration tool. When invoked with a specified desired schema version, the tool automates the successive application or reversal of an appropriate sequence of schema changes until it is brought to the desired state. An advantage to using a database migration tool is that it mitigates risk when moving the data. A tool can also build scripts for you to manipulate the specific relationships within your original database rather than amending the entire thing. 
 

#### More on requirements:
A requirement is a statement that identifies a necessary attribute, capability, characteristic, or quality of a system for it to have value and utility to a customer, organization, internal user, or other stakeholder.

So if a product requirement changes and the user would like a new type of use for the data, a data migration might be in order.

## Questions: :facepunch: 
1. When might you need to perform a database migration?
2. What would you use a build script for?
3. What files might a build script involve?

## Bonus: automate psql setup with a bash script
In order to set up your postgres server you first have to run multiple commands; we automated this process by creating a bash script in a [filename].sh file with the following contents:
```bash
psql -c "CREATE DATABASE [dbName];"
psql -c "CREATE USER [user] WITH PASSWORD '[password]';"
psql -c "GRANT ALL PRIVILEGES ON DATABASE research TO [user];"
psql -c "ALTER DATABASE research OWNER TO [user];"
psql research -c "GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO [user];"
```
If sharing this script, care should be taken not to upload any passwords to github!


### Useful links:
Migration between PostgreSQL releases: https://www.postgresql.org/docs/9.0/static/migration.html

Database migration wiki:
https://en.wikipedia.org/wiki/Schema_migration

SQL Drop Table:
https://www.tutorialspoint.com/sql/sql-drop-table.htm




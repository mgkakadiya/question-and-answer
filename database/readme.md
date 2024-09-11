# Postgres Database setup
## Create new databse and setup new databse user and

```
psql -h localhost -U postgres
CREATE DATABASE <DATABASE_NAME>;
create user <DATABASE_USER> with encrypted password '<USER_PASSWORD>';
grant all privileges on database <DATABASE_NAME> to <DATABASE_USER>;
ALTER USER  <DATABASE_USER> PASSWORD '<NEW_USER_PASSWORD>';


# Other setup commonds
grant USAGE on schema my_schema to service_role;
grant all on all tables in schema my_schema to service_role;
```

### Validate database
```
psql -U <DATABASE_USER> -d <DATABASE_NAME> -h localhost
```

### commonds
```
psql -h localhost -U <DATABASE_USER> -d <DATABASE>

# List of database
\list

# use database
\c <DATABASE_NAME>

# create Schema
CREATE SCHEMA [IF NOT EXISTS] schema_name; 

# view  list of the privileges:
\dn+

# show all available tables in PostgreSQL
# 1. Using SQL Query
SELECT * FROM information_schema.tables;
# or in a particular schema:
SELECT * FROM information_schema.tables WHERE table_schema = 'schema_name';

# 2 Using psql
# List of tables
\dt 
# In all schemas:
\dt *.*
# In a particular schema:
\dt schema_name.*

```

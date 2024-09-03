# Postgres Database setup
## Create new databse and setup new databse user and

```
psql -h localhost -U postgres
CREATE DATABASE <DATABASE_NAME>;
create user <DATABASE_USER> with encrypted password '<USER_PASSWORD>';
grant all privileges on database <DATABASE_NAME> to <DATABASE_USER>;
ALTER USER  <DATABASE_USER> PASSWORD '<NEW_USER_PASSWORD>';
```

### Validate database
```
psql -U <DATABASE_USER> -d <DATABASE_NAME> -h localhost
```

### commond
```
psql -h localhost -U <DATABASE_USER> -d <DATABASE>
\list # List of database
\c <DATABASE_NAME> # use database
CREATE SCHEMA [IF NOT EXISTS] schema_name; # create Schema
\dt # List of tables

```

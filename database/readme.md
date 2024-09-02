# Postgres Database setup
## Create new databse and setup new databse user and

```
psql -h localhost -U postgres
CREATE DATABASE <DATABASE_NAME>;
create user <DATABASE_USER> with encrypted password '<USER_PASSWORD>';
grant all privileges on database <DATABASE_NAME> to <DATABASE_USER>;
```

### Validate database
```
psql -U <DATABASE_USER> -d <DATABASE_NAME> -h localhost
```

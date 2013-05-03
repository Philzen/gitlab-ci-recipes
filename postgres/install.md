## Installing Gitlab_CI on PostgreSql

Refer to these steps instead of the ones listed in section 3. of the [Gitlab CI installation instructions](https://github.com/gitlabhq/gitlab-ci/blob/2-2-stable/doc/installation.md)


```
sudo su pgsql
psql -d postgres

# list database users, checking that role gitlab_ci doesn't exist yet:
SELECT * FROM pg_user;

# if it doesn't, let's create it:
CREATE USER gitlab_ci WITH PASSWORD 'supersecret_password';

# check that the database doesn't exist yet with
\l

# if it doesn't, let's create it and make gitlab_ci the owner:
CREATE DATABASE "gitlab_ci_production" ENCODING 'UTF8' LC_COLLATE 'C' OWNER = gitlab_ci;

# exit psql console
\q




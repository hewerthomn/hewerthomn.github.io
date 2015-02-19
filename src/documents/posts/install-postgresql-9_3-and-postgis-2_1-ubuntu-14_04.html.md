```
title: Installing PostgreSQL 9.3 and PostGIS 2.1 on Ubuntu 14.04
layout: post
tags: ['post', 'postgresql','postgis', 'ubuntu 14.04']
date: 2015-02-19
```

## Remove old PostGIS Installation
The first step is to remove older version of PostGIS if any.

    sudo apt-get purge postgis

---

## Setup repository

    wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
    sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ trusty-pgdg main" >> /etc/apt/sources.list.d/postgresql.list'

---

## Install PostgreSQL and PostGIS

    sudo apt-get update && sudo apt-get install postgresql-9.3-postgis-2.1 -f

---

## Enable PostGIS extension

Now, let’s see how we can create a PostGIS enabled database. We have two ways of doing this, in which the first one is the latest and simple one:

### 1. Using the CREATE EXTENSION statement
This is as simple as running a query in the database where you want to enable PostGIS:

    CREATE EXTENSION postgis;
OR

### 2. Create database template for PostGIS
This is an old method of doing the same. Creating  a template for PostGIS will make it easy to enable PostGIS for every new database you create:

    createdb -E UTF8 template_postgis2.1
    psql -d postgres -c "UPDATE pg_database SET datistemplate='true' WHERE datname='template_postgis2.1'"
    
Now, we have to run an SQL script comes along with PostGIS in the template:

    psql -d template_postgis2.1 -f /usr/share/postgresql/9.3/extension/postgis--2.1.5.sql
    psql -d template_postgis2.1 -c "GRANT ALL ON geometry_columns TO PUBLIC;"
    psql -d template_postgis2.1 -c "GRANT ALL ON geography_columns TO PUBLIC;"
    psql -d template_postgis2.1 -c "GRANT ALL ON spatial_ref_sys TO PUBLIC;"

---

### Create a test database
Let’s test the PostGIS installation by creating a test database:

    createdb test_db -T template_postgis2.1

---
    
### Test the installation
In test_db you can run the following statement to make sure that you installed and configured PostGIS correctly:

    test_db=# select postgis_version();
    postgis_version---------------------------------------
    2.1 USE_GEOS=1 USE_PROJ=1 USE_STATS=1
    (1 row)

---
    
### Enable PostGIS for an existing Database
If you don’t want to use the `CREATE EXTENSION` statement and want to enable PostGIS for an already existing database. It is simple enough, you just need to run the PostGIS 2.1 script in your database:

    psql -d test_db -f /usr/share/postgresql/9.3/extension/postgis--2.1.5.sql

---

inspiration http://technobytz.com/install-postgis-postgresql-9-3-ubuntu.html

/********************************************
Summary
********************************************/
Select distinct rows by using DISTINCT operator.
Filter rows by using WHERE clause.
Sort rows by using the ORDER BY clause.
Select rows based on various operators such as BETWEEN, IN and LIKE.
Group rows into groups by using GROUP BY clause
Apply condition for groups by using HAVING clause.
Join to another table by using INNER JOIN, LEFT JOIN, RIGHT JOIN clauses.

/********************************************
Troubleshooting
********************************************/

//posgreSQl cannot set locale
export LANGUAGE="en_US.UTF-8"
echo 'LANGUAGE="en_US.UTF-8"' >> /etc/default/locale
echo 'LC_ALL="en_US.UTF-8"' >> /etc/default/locale

$ # next: logout and login

/*********************************************
Installation
*********************************************/
sudo apt-get update
sudo apt-get install postgresql postgresql-contrib


/*********************************************
Setup
*********************************************/
//login
sudo -i -u postgres
psql

//create a user
createuser --interactive

//create a db
CREATE DATABASE test1;

//change default password
sudo -u postgres psql postgres
\password postgres

//drop a user
dropuser test1




/*********************************************
CLI
*********************************************/
ALTER USER "huoshui" WITH PASSWORD 'huoshui';

//login
psql -h localhost -U postgres

/*********************************************
commands
*********************************************/
//list all database
\l

//connect to databse
\connect huoshui

//list all tables
\dt

//describe schema
\d+ tablename

/*********************************************
GUI
*********************************************/
//enable remote access
$ su - postgres
$ vi /etc/postgresql/8.2/main/pg_hba.conf
host all all 10.10.29.0/24 trust

# vi /etc/postgresql/8.2/main/postgresql.conf
listen_addresses='localhost' => listen_addresses='*'
# /etc/init.d/postgresql restart


/*********************************************
uninstall
*********************************************/
sudo apt-get purge postgr*
sudo apt-get autoremove

teradoc
=======

This repository is a help file for the most common queries one needs for accessing teradata databases.

# Introduction

Teradata is a commercial Relational Database Management Server/System (RDBMS) used by rich companies.
The most stricking fact is that the Masively Parallel Processing (MPP) support was included
in this product since 1979. It means that somebody predicted that the workload needs to be distributed
to multiple computers in order to achieve the high performance required by big enterprises.
Only recently the open source community created the Hadoop project which implements the MPP 
by sending the MapReduce jobs to individual nodes. The way Hadoop works is surprisingly similar to how the 
Parser Engine (PE) sends the queries to the Access Module Processors (AMP) in the teradata database.



# Why

Because I used the MySQL console and got so used to it that when I used the Basic Teradata Queries (BTEQ) 
console I was deeply disapointed about how cumbersome it is.

Problems that I still don't know how to solve:
* no history                             (no arrow UP)
* no autocomplete for table/column names (no TAB)


# BTEQ login/logout

Note that all commands in bteq start with a dot.

bteq
.logon 127.0.0.1/asura

Password:

 *** Logon successfully completed.
 *** Teradata Database Release is 14.00.00.01
 *** Teradata Database Version is 14.00.00.01
 *** Transaction Semantics are BTET.
 *** Session Character Set Name is 'ASCII'.

 *** Total elapsed time was 3 seconds.

 BTEQ -- Enter your SQL request or BTEQ command:


.quit
 *** You are now logged off from the DBC.
 *** Exiting BTEQ...
 *** RC (return code) = 8

# DBC is the `information_schema`

To see the list of databases read the `DBC` database:

_ SELECT databasename FROM dbc.databases;

To see the list of tables in a database:

_ SELECT tablename FROM dbc.tables WHERE databasename = 'asura';



# Creating an user




# Creating a database/table

_ CREATE DATABASE

_ CREATE TABLE 


# Inserting data

Surprise! It seems that it is not possible to insert more than one row at a time:

INSERT INTO Customer cusID, cusFirst, cusLast, cusMI, cusEmail 
VALUES 1, 'Tester', 'Test', 'A', 'test@tera.com'
;

INSERT INTO Customer cusID, cusFirst, cusLast, cusMI, cusEmail 
VALUES 2, 'Tester2', 'TzT', 'B', 'test2@tera.com'
;



# Where is my "LIMIT 10" clause?

IN teradata use the `SAMPLE 10` clause:

_ SELECT * FROM Customer WHERE cusID < 10 SAMPLE 1;



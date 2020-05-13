---
layout: note
title: Influx basics
category: DB
---

# Online documentation
[Offical documentation on InfuxData.com](https://www.docs.influxdata.com/influxdb)

# Command line interface
``` shell
SET HOME=.\
influx
```

# Basic commands

> Double quote all names (only strictly required if it contains [A-z,0-9,_]) Single quote all values, e.g. WHERE "tag1" = 'value1'

List database:

``` sql
show databases
```

Use database:
``` sql
use DATABASENAME    
```
Change way times are displayed to ISO format (as opposed to ticks):
``` sql
precision rfc3339
```
List all measurements in current database
``` sql
show measurements
```
Creating a database and a retention policy (below keep data for 50 days):
``` sql
create database "DB"
create retention policy "RP" on "DB" duration 1200h 
       replication 1 shard duration 24h default
```
# Queries

> Queries always return the time.

To query all fields in a measurement for the last minute
``` sql
select * from "measurement-name" where time > now() - 1m
```
To query a particular field
``` sql
select "field-name" from "measurement-name" where time > now() - 1m
```
``` sql
select "field-name" from "measurement-name" 
where "field-name2" = 'value' 
and time > now() - 1m
```
Using Regex in WHERE clause
``` sql
select "field-name" from "measurement-name" 
where "field-name2" ~= /value/
and time > now() - 1m
```

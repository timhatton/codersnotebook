---
layout: note
title: SQL Server backups and files
category: DB
---

# Backing and restoring by command
Backup to a file:
``` sql
BACKUP DATABASE DBNAME
TO DISK='C:\FILE.BAK'
WITH  INIT [, COMPRESSION]
```
Check the backup:
``` sql
RESTORE VERIFYONLY
FROM DISK='C:\FILE.BAK'
```
Restore:
``` sql
RESTORE DATABASE DBNAME
FROM DISK='C:\FILE.BAK'
```

# Copying databases
Make a copy of a database (using BACKUP/RESTORE which doesn't require SQL Server Agent and can use a backup from another machine):

(NB: can also use Copy Wizard in SQL SMS)

Backup to file as above.

List the logical files in the backup:
``` sql
RESTORE FILELISTONLY 
FROM DISK='C:\TEMP\FILE.BAK' 
```
Restore to new db:
``` sql
RESTORE DATABASE DBNAME_NEW 
FROM DISK='C:\TEMP\FILE.BAK' 
WITH 
MOVE 'DBNAME' TO 'C:\TEMP\DBNAME_NEW.mdf',           
MOVE 'DBNAME_Log' TO 'C:\TEMP\DBNAME_NEW_Log.ldf';    
```
NB: the logical filenames DBNAME and DBNAME_Log are obtained from the RESTORE FILELISTONLY command
Moving a database's files

Just detach the database, move the mdf and ldf files, and attach.

Or by command:
``` sql
sp_detach_db 'mydb'
move the mdf and ldf files 
sp_attach_db 'mydb','E:\Sqldata\mydbdata.mdf','E:\Sqldata\mydblog.ldf'
```
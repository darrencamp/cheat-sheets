---
tags:
  - sql-server
  - db
---

## Backup SQL server
```
-- Back up the AdventureWorks2012 database to new media set.  
BACKUP DATABASE <Database Name>
    TO DISK = '<backup filename>'   
    WITH FORMAT;  
GO
```

Reminder: If running sql server from a docker container the disk location is location in the container. Use docker cp command to grab the backup file and use it locally if required.

## use docker to host sqlserver

`docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<strong password>' -p 1433:1433 -v <host directory>/data:/var/opt/mssql/data -v <host directory>/log:/var/opt/mssql/log -v <host directory>/secrets:/var/opt/mssql/secrets --name <container name> -d mcr.microsoft.com/mssql/server:2019-latest`

## sqlpackage on the mac

./sqlpackage/sqlpackage /a:Export /tf:<export-name>.bacpac /ssn:"<server-name>" /sdn:"<database-name>" /sp:"<password>" /su:"<user-name>"

./sqlpackage/sqlpackage /a:Import /tsn:<target-server-name> /tdn:<target-database> /tu:<user-name> /tp:<password> /sf:<exported-bacpac>.bacpac

by specifying the server name default transport and port will be used

## on error something something
sp_configure 'contained database authentication', 1;
RECONFIGURE

## check full text search is installed

SELECT FULLTEXTSERVICEPROPERTY('IsFullTextInstalled')
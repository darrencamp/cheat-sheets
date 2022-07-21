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

`docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<strong password>' -p 1433:1433 -v <host directory>/data:/var/opt/mssql/data -v <host directory>/log:/var/opt/mssql/log -v <host directory>/secrets:/var/opt/mssql/secrets --name jjs-sqlserver -d mcr.microsoft.com/mssql/server:2019-latest`


---
title: "Azure SQL to AWS RDS SQL"
date: 2016-04-15 18:34:24
layout: post
author: "k2byew"
---
Wanted to move database from [Azure SQL Database](https://azure.microsoft.com/en-us/services/sql-database/) to [AWS RDS for SQL Server](https://aws.amazon.com/rds/sqlserver/), unfortunately currently [AWS DMS](https://aws.amazon.com/dms/) doesn't support this migration.


Exporting then importing a data tier application/BACPAC file can [cause issues](https://forums.aws.amazon.com/thread.jspa?messageID=446092), so better go read the AWS [migration instructions](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/SQLServer.Procedural.Importing.html).


Luckily [SQL Database Migration Wizard](http://sqlazuremw.codeplex.com/) makes things easy by creating the scripts required to repopulate the table structure, and then use Bulk Copy `bcp` to move the data. Make sure the database's master account's password does not contain characters that need escaping in a batch script, or else the process will fail.


Can login to AWS RDS SQL using SQL Server Management Studio, can use Putty to [port forward](https://esha.zendesk.com/hc/en-us/articles/202977089-Granting-Access-to-Additional-Users-with-SQL-Server-Management-Studio) if required. SQL Server Management Studio doesn't seem to understand `localhost:1234`, use `127.0.0.1,1234` instead. Use a comma instead of a colon before the port number!


Create new users, and give them the [correct permissions](https://esha.zendesk.com/hc/en-us/articles/202977089-Granting-Access-to-Additional-Users-with-SQL-Server-Management-Studio) to [access](https://technet.microsoft.com/en-us/library/ms189121(v=sql.90).aspx) the imported database.


Note [AWS RDS](https://www.mssqltips.com/sqlservertip/3270/running-sql-server-databases-in-the-amazon-cloud--rds-limitations-part-2/) limitations.

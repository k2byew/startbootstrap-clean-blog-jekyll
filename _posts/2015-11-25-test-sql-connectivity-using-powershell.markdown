---
title: "Test SQL connectivity using Powershell"
date: 2015-11-25 18:21:58
layout: post
author: "k2byew"
---
[Useful script from here!](http://www.systemcentercentral.com/powershell-how-to-connect-to-a-remote-sql-database-and-retrieve-a-data-set)

Adapted to use username and password to authenticate:
```
$SQLServer = "MySQLServer"
$SQLDBName = "MyDBName"
$SqlQuery = "select @@version"

$SqlConnection = New-Object System.Data.SqlClient.SqlConnection
$SqlConnection.ConnectionString = "Server = $SQLServer; Database = $SQLDBName; User ID = $Username; Password = $password"

$SqlCmd = New-Object System.Data.SqlClient.SqlCommand
$SqlCmd.CommandText = $SqlQuery
$SqlCmd.Connection = $SqlConnection

$SqlAdapter = New-Object System.Data.SqlClient.SqlDataAdapter
$SqlAdapter.SelectCommand = $SqlCmd

$DataSet = New-Object System.Data.DataSet
$SqlAdapter.Fill($DataSet)

$SqlConnection.Close()

clear

$DataSet.Tables[0]
```

Getting security errors about *.ps1 not signed?

`Set-ExecutionPolicy Unrestricted`

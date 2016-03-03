# CopyForce -- Copy an Instance of Salesforce to an RDBMS #

CopyForce is an application for copying full or partial Salesforce instances to a relational database. Several target databases are supported out of the box:
  * Microsoft SQL Server
  * H2
  * Oracle

Both incremental and complete copies are supported.

Are you looking for the commercial version?  The [CAPSTORM](http://www.capstorm.com) version is faster, has a secure GUI, and supports the latest Salesforce protocol.

To get started:
  * Download the CopyForce zip file that matches the RDBMS into which you want to copy Salesforce.
    * CopyForceSqlServer.zip will copy Salesforce into Microsoft [SQL Server](http://www.microsoft.com/sqlserver).
    * CopyForceH2.zip will copy Salesforce into [H2](http://www.h2database.com/html/main.html)
    * CopyForceOrace.zip will copy Salesforce into [Oracle](http://www.oracle.com/index.html)
  * Open the README.html file in the root directory.

## How Is CopyForce Used? ##
  * #1 - Make regular backups of a production Salesforce instance.
  * Support local analytical processing of Salesforce data.
  * Give updated slices of Salesforce data to non-Salesforce users.
  * Update Financial system meta data that links Salesforce to accounting.

## Examples ##
Example: Copy all tables from Salesforce to an empty SQL Server database.
```
java -jar CopyForceSqlServer.jar -schema -gui 
  -salesforce Production,myname@gmail.com,password,0908989token
  -sqlserver "//localhost;databaseName=sqlforcetest;username=me;password=caleb&noah;" 
```

Example: Update existing Account and Contact tables in SQL Server.
```
java -jar CopyForceSqlServer.jar -include "Account,Contact" -gui 
  -salesforce Production,myname@gmail.com,myPassword,SecurityToken  
  -sqlserver "//localhost;databaseName=sqlforcetest;username=me;password=caleb&noah;"
```

Example: Create a new H2 database that contains all Saleforce tables.
```
java -jar CopyForceH2.jar -schema -gui 
  -salesforce Production,myname@gmail.com,myPassword,SecurityToken 
  -h2 C:/tmp/SalesforceCopy -h2user sa -h2password aslan 
```

Example: Copy all Account records that have been created or modified this week.
```
java -jar CopyForceOracle -include Account -since last_week
  -salesforce Production,myname@gmail.com,myPassword
  -oracle "localhost:1521:xe" -orauser fred -orapassword joker
```

If it works for you and or you have suggestions please contact me at [mailto:gsmithfarmer@gmail.com](mailto:gsmithfarmer@gmail.com). If you need support for another database engine, I would be glad to help.
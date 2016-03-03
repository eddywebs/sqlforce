#Tutorial on how to use the SQLForce Jython update() method.

# How to Use the SQLForce.update() Jython method #

The _SQLForce.update()_ method is a Jython wrapper around the basic
```
UPDATE table SET col=value [,col=value]* [WHERE ...]
```
command that constructs and executes the _WHERE_ command from simple Jython structures. The _SQLForce.update()_ is useful when your code knows the Salesforce ID for the records to update.


# Details #

```
import SQLForce

session = SQLForce.Session("sandbox")

rowsToUpdate = [ 
              ["003A0000006H18SIAS", "CEO"], 
              ["003A0000006H18TIAS", "CFO"], 
              ["003A0000006H18UIAS", None]
             ]

status = session.update( "Contact", ["title"], rowsToUpdate )

```
The arguments to the _sesion.update()_ method are:
  * table -- the name of table whose records will be updated. In the example, we are updating records in the _Contact_ table.
  * columns -- list of columns to be updated.
  * rows -- one row of data for each row to be updated. The len() of each row MUST match (1 + len(columns)) and the first value of each row MUST be the Salesforce Id of the row update.

The _session.update()_ method returns _None_ if the update succeeds and an error string if the update fails.

# See Also #
  * SalesforceConnectionProfileRegistry
  * SQLForceForJython
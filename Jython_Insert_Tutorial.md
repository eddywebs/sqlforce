#Tutorial on how to use the SQLForce Jython insert() method.

# How to Use the SQLForce.insert() Jython method #

The SQLForce.insert() method is a Jython wrapper around the basic
```
INSERT INTO table(col [,col]*) VALUES(value [,value]*) [(value [,value]*)]*
```
command that constructs and executes the _INSERT_ command from simple Jython structures.


# Details #

```
import SQLForce

session = SQLForce.Session("sandbox")

rowsToInsert = [ 
              ["Gregory", "Smith", "CEO"], 
              ["Mary", "Smith", "CFO"], 
              ["Noah", "Smith", None],
              ["Sarah", "Smith", None]
             ]

recordIds = session.insert( "Contact", ["FirstName", "LastName", "Title"], rowsToInsert )

```
The arguments to the _sesion.insert()_ method are:
  * table -- the name of table to receive the records. In the example, we are inserting into the _Contact_ table.
  * columns -- list of columns into which database will be inserted.
  * rows -- one row of data for each row to be inserted. The len() of each row MUST match len(columns).

The _session.insert()_ method returns a list of the Salesforce Ids created for the inserted rows.
  * The number of records Ids returned will always be the same as the number of rows provided in the original call.
  * If one or more rows fails to insert then its corresponding records Id will be set to _None_.

# See Also #
  * SalesforceConnectionProfileRegistry
  * SQLForceForJython
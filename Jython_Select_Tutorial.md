#Jython SELECT Tutorial

# Jython SELECT Tutorial #

The Jython module, SQLForce, support two variations of select.
  * Select where each row is returned as an array of values.
  * Select where each row is returned as class where the class properties are named based on the column names.


# SELECT Where Each Row is an Array of Values #
## Example 1: Loop over rows ##
```
session = SQLForce.Session("sandbox")
for row in session.select( "SELECT id, FirstName, LastName FROM Contact LIMIT 3"):
    print "First Name: " + row[1]
    print "Last Name: " + row[2]
```
## Example 2: Invoked a User Defined Callback ##
```
session = SQLForce.Session("sandbox")
def callback( row ):
    print "First Name: " + row[1]
    print "Last Name: " + row[2]

session.select2("SELECT id, FirstName, LastName FROM Contact LIMIT 3", callback )
```

# SELECT Where Each Row is a Class with Attributes #
## Example 1: Loop over rows ##
```
session = SQLForce.Session("sandbox")
for row in session.selectRecords( "SELECT id, FirstName, LastName FROM Contact LIMIT 3"):
    print "First Name: " + row.FirstName
    print "Last Name: " + row.LastName
```
## Example 2: Invoked a User Defined Callback ##
```
session = SQLForce.Session("sandbox")
def callback( row ):
    print "First Name: " + row.FirstName
    print "Last Name: " + row.LastName

session.selectRecords2("SELECT id, FirstName, LastName FROM Contact LIMIT 3", callback )
```
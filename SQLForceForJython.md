# SQLForce for Jython -- a Jython module for SQLForce #

NOTE: The latest release (always free) can be found at [CAPSTORM](http://www.capstorm.com)

SQLForce for Jython  brings ANSI INSERT, UPDATE, DELETE, SELECT, SELECT UNION, and SELECT DISTINCT for Salesforce into Jython. The Jython module, SQLForce.py, is built on the core SQLForce project. We use it everyday.

Getting started is easy.:
  * Download the most recent sqlforce.zip distribution.
  * Open the README.html file in the root directory.
    * Add sqlforce.jar to your java CLASSPATH
    * Import the SQLForce module
  * Study the example code referenced by the README.html.


# Code Snippet: Select Rows into a Python Object #

```
import SQLForce

session = SQLForce.Session()
session.connect( "PRODUCTION", "gsmithfarmer@mail.com", "***", "securityToken" )

for rec in session.selectRecords("SELECT LastName, FirstName, MailingCountry FROM Contact"):
   print rec.LastName, rec.FirstName, rec.MailingCountry
```
# Code Snippet: Select Rows into an Array #

```
for c in session.select("SELECT LastName, FirstName, MailingCountry FROM Contact"):
    print "Last Name:", c[0], "First Name: ", c[1]
```



# Code Snippet: Selects Rows with a Callback #
```
def callback(rec):
    print rec.LastName, rec.FirstName
session.selectRecords2( "SELECT LastName, FirstName FROM Contact", callback )
```

# Code Snippet: Update Records #
```
session.runCommands("UPDATE Contact SET title='CEO' WHERE LastName='Smith'")
```

# Connecting to Salesforce #
There are two ways to connect to Salesforce using jython. You can connect using complete
credential information:
```
import SQLForce

session = SQLForce.Session()
session.connect( "PRODUCTION", "gsmithfarmer@mail.com", "***", "securityToken" )
```
or you can connect using a registered profile.
```
import SQLForce

session = SQLForce.Session("profileName")
```
See the SalesforceConnectionProfileRegistry page for instructions on setting up connection profiles.
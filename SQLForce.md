# SQLForce Classic - ANSI SQL for Salesforce #
NOTE: The latest release (always free) can be found at [CAPSTORM](http://www.capstorm.com)

<i>SQLForce Classic</i> is a command line interpreter that provides ANSI like extensions to SOQL and hides much of the governor limitations imposed by Salesforce.

In addition to SOQL, SQLForce Classic adds support for the full range of base ANSI SQL commands.

  * SELECT
  * SELECT DISTINCT
  * SELECT .. UNION SELECT
  * UPDATE
  * INSERT
  * DELETE
To get started:

  * Download the most recent sqlforce.zip distribution.
  * Type java -jar sqlforce.jar on a command line.
  * Type HELP on the command line prompt to get a list of available commands.
  * Type HELP CONNECT to learn how to connect to a Salesforce instance.
  * Explore the documentation for each command by typing HELP <Command Name>.

# Recommendations #
For most administration tasks [SQLForceForJython](SQLForceForJython.md) is the best tool to use. [SQLForceForJython](SQLForceForJython.md) combines all of the power of <i>SQLForce Classic</i> with Jython.
However, there are a few tasks where <i>SQLForce Classic</i> is extremely useful.
  * Quickly run and iteratively refine a bit of SOQL. Unlike the FORCE Eclipse plugin, <i>SQLForce Classic</i> shows the values from all columns in the order they appear in the SELECT statement.
  * Look up the Apex names for all columns in a table. See the DESCRIBE tableName command.

# Code Snippet - Find all Unique Country Names in Contacts and Accounts #

```
SELECT DISTINCT MailingCountry FROM Contact
  UNION SELECT OtherCountry FROM Contact
  UNION SELECT ShippingCountry FROM Account
  UNION SELECT BillingCountry FROM Account
  OUTPUT "/tmp/UniqueCountryNames.txt"
;
```

# Code Snippet - Normalize USA Spelling for Contacts #
```
UPDATE Contact SET MailingCountry='USA'
WHERE MailingCountry IN ('United States', 'US', 'United States of America', 'America');
```

# Code Snippet - Insert Account Records #
```
INSERT INTO Account (Name, BillingState, BillingCountry)
  VALUES( "Walmart", "Arkansas", "USA")
  , ("Monsanto", "Missouri", "USA")
  ;
```

# Code Snippet - Insert Contacts from Another Table #
```
INSERT INTO Contact (AccountId, FirstName, LastName) SELECT Acct, N1, N2 FROM CustomObject__c;
```
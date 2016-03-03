# What's New #

06-Aug-11
  * Upgrade to Summer'11 protocol (version 22.0).
  * Add support for column type DataCategoryGroupReference
  * Add command line specification of proxy info
  * Building MySQL version (email me if you are interested).

25-Mar-11
  * UTF-8 Support for all target databases. This is automatic based on your Salesforce setup.
  * Fixed problem with some VARCHAR columns being too long in target.
  * Tested against Spring'11

18-Feb-11
  * Reposted all CopyForce jars. None of the 20.2 jars worked -- my bad.

11-Feb-11
  * Change the version name convention. The second digit is now the Force protocol version used by the libraries. Currently, all at "20" (the current version).
  * Encrypted fields now work.
  * Fixed problem with Date/Time/DateTime fields being copies incorrectly. GMT vs Local time handling was not correct.

3-Jan-11
  * CopyForceOracle added.
  * All CopyForce variations use a lot less memory. A new flag, -querybatch, was add to control the number of rows returned by Salesforce in a batch. The default, 1000, caused very large memory usage.
  * All CopyForce variations have a new switch, -since SalesForceDateTime, that limits the copy/update to records modified since a specified date.
  * All CopyForce variations use common PreparedStatement logic for inserts and updates. This will make adding a new database very simple.

4-Dec-10
  * Discovered that non-admins could not extract two tables (example NewsFeed). Changed extraction code to ignore these tables if the user is not an administrator.
  * Changed build environment to Eclipse/Helios (about time!).

2-Dec-10
  * Made security token optional in all forms of connections.
  * In CopyForce, logic to that finds "LastModifiedDate" field cleaned up to look in more places.

27-Nov-10
  * Added JavaForce.zip -- core library used by all other tools.
  * Added CopyForce set of programs
  * Lots of usage documentation added to all components.

15-Oct-10
  * Upgrade to Winter'11 (version 20.0) protocol.

17-Sep-10
  * Fixed a problem with the Jython module when deep column references had non-ovelapping paths. Parser was not picking up the value from each path.

27-Aug-10
  * Fixed a problem with the Jython module when referencing more than 2 levels deep on columns and using the selectRecords() method.
  * Upgraded to version 19.0 of the partner WSDL.

03-Apr-10
  * Fixed date time parsers and made them generous wrt syntax (almost correct date or dateTime values will be patched on the fly to meet SOQL syntax requirements).

24-Mar-10
  * Upgrade to use Version 18.0 (Spring 10) version of the Salesforce protocol (the partner wsdl).

16-Mar-10
  * Add Jython support for selecting classes with attributes with a select statement. See [Jython\_Select\_Tutorial](Jython_Select_Tutorial.md).

20-Feb-10
  * Support return multi-line column data in the Jython module.
  * Add the SELECTX command -- return return of a SELECT statement as simple XML.

15-Feb-10
  * Extend UPDATE command syntax to support efficient updates where Salesforce IDs are known.
  * Add convenience methods (insert(), update(), delete()) to SQLForce.py.
  * Add ability to fetch Salesforce IDs of newly inserted rows.

6-Feb-10
  * Add support for Salesforce connection profiles. See SalesforceConnectionProfileRegistry

2-Feb-10
  * Update Jython module (I use this every week...more examples posted next weekend).
  * Fix NPE bug in Python module that occurred when a SELECT statement did not end in a semicolon.
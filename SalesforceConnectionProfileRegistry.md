#Salesforce Connection Profile Registry

# SQLForce Connection Profile Registry #

This page describes how to register Salesforce connection profiles so you can connect
to Salesforce using:
```
CONNECT PROFILE profileName
```
or if you are using SQLForce via the jython module:
```
import SQLForce

session = SQLForce.Session("profileName")
```


# Connection Profile Registry #

On initialize, SQLForce looks for a configuration file named _sqlforce.ini_ in the current
user's home directory.
  * %USERPROFILE%\sqlforce.ini on Windows
  * $HOME/sqlforce.ini on Linux

The _sqlforce.ini_ file must be an XML file in the following format:
```
<sqlforce>
	<connection 
		name="main"
		type="Production"
		username="gsmithfarmer@gmail.com"
		password="yourPassword"
		token="MGwH9RsGCgfUhwkd4iXfZZZZZ"
	/>
	<connection 
		name="test"
		type="Sandbox"
		username="gsmithfarmer@gmail.com.test"
		password="yourPassword"
		token="MGwH9RsGCgfUhwkd4iXfZZZZZZ"
	/>	
</sqlforce>
```
where the _connection_ attributes are:
| **Attribute Name** | **Description** |
|:-------------------|:----------------|
| name               | name that can be used to reference the profile |
| type               | PRODUCTION or SANDBOX |
|username            |Salesforce username|
|password            |Salesforce password|
|token               |Salesforce provide security token|

If this _sqlforce.ini_ was located in your home directory, then you could connect to
Salesforce using:
```
CONNECT PROFILE main
```
or if you are using SQLForce vi the jython module:
```
import SQLForce

session = SQLForce.Session("main")
```
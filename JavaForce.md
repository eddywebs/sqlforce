# JavaForce -- Java Bindings for Salesforce #

<i>JavaForce</i> is a java binding the to the Salesforce partner WSDL that hides much the SObject and governor limitations imposed by Salesforce. It is the core jar that the applications [SQLForce](SQLForce.md), [CopyForce](CopyForce.md), and [SQLForceForJython](SQLForceForJython.md) rely upon.

To get started:
  * Download the current version of sqlforce**.zip
  * Look at the README.html file in the root directory.
  * Review the sample code and javadoc referenced in the README.html file.**

# Code Snippet - SELECT with callback #

```
LoginCredentials credentials = LoginCredentialsRegistry.getInstance().getCredentials("javaforce");

ISObjectQuery2Callback callback = new DefaultSObjectQuery2Callback() {

  @Override
  public void addRow(int rowNumber, String[] data) {
    System.err.println("Callback: Row " + rowNumber + " : " + data[0] + ", " + data[1] );
  }
};

String sql = "SELECT id, name FROM User";

new SObjectQueryHelper().findRows( session, sql, callback);
```

# Code Snippet - INSERT an Account #
```
AccountRecord account = new AccountRecord();
		
account.setName("My Sample Account");
account.setBillingCountry("USA");
account.setStringField("ShippingCountry", "USA"); // Another way to set a field. Good technique for custom fields.
		

SaveResult result = new SObjectCreateHelper().create(session, account);
```

# Code Snippet - SELECT into a List #
```
String sql = "SELECT id, name FROM User";
		
List<String[]> results = new SObjectQueryHelper().runQuery2(session, sql);
		
for( String[] record : results ) {
  System.err.println("Array: Row: " + record[0] + "," + record[1] );
}
```
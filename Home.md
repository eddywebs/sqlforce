# Java, SQL, Jython, Backups & Salesforce #

This site contains source and distributions for several tools based on the <i>JavaForce<i>  library.<br>
<br>
What are you interest in doing?<br>
<table><thead><th> <b>Project</b> </th><th> Audience </th><th> Description </th></thead><tbody>
<tr><td> JavaForce      </td><td> Java Programmer </td><td> Core java library for communicating with Salesforce. </td></tr>
<tr><td> <a href='SQLForce.md'>SQLForce</a> </td><td> Salesforce Admin</td><td> Command line interpreter with ANSI SELECT/DELETE/MODIFY//INSERT commands that work with Salesforce. The <a href='SQLForceForJython.md'>SQLForceForJython</a> is a superset of this project</td></tr>
<tr><td> <a href='SQLForceForJython.md'>SQLForceForJython</a> </td><td> Salesforce Admin </td><td> Jython module with ANSI SELECT/DELETE/MODIFY/INSERT commands that work Salesforce </td></tr>
<tr><td> CopyForce      </td><td> Salesforce Admin </td><td> Copy a Salesforce instance to a local RDBMS </td></tr>
<tr><td> ConnectThruProxy</td><td>All       </td><td>Additional instructions if you have to connect thru a proxy server</td></tr></tbody></table>


All of these tools are part of the <b>SQLForce</b> project.<br>
<br>
<h1>Origins of <b>SQLForce</b></h1>

SQLForce was initially created for several reasons:<br>
<ul><li>We needed ANSI SELECT, SELECT DISTINCT, SELECT/UNION, DELETE, MODIFY, and INSERT commands that just worked.<br>
</li><li>SOQL and Salesforce's record limits made it just too hard to modify a lot of records.<br>
</li><li>We needed to change all occurences of "United States of America" to "USA" and wanted to use a SQL UPDATE statement.</li></ul>

Overtime, the base java libraries have been used to various other tools including a rich Jython module. We have used the tools, especially the Jython module, for production tasks since early 2009. The first time you write a script like:<br>
<pre><code>UPDATE Contact SET MailingCountry="USA" WHERE MailingCountry IN ("United States", "US")<br>
</code></pre>
you will be hooked. For any Salesforce administrator, SQLForce simply saves a lot of time.<br>
<br>
Later we started worrying about what would happen if a Salesforce user deleted a lot of data and emptied their recycle bin. <a href='CopyForce.md'>CopyForce</a> was born. <a href='CopyForce.md'>CopyForce</a> copies all or part<br>
of a Salesforce instance to a local RDBMS.<br>
<br>
The java libraries use the partner wsdl and are typically upgraded within a few weeks after Salesforce upgrades.
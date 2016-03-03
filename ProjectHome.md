# Java, SQL, Jython, Backups & Salesforce #

This site contains source and distributions for several tools based on the <i>JavaForce<i>  library.<br>
<br>
What are you interest in doing?<br>
<table><thead><th> <b>Project</b> </th><th> Audience </th><th> Description </th></thead><tbody>
<tr><td> JavaForce      </td><td> Java Programmer </td><td> Core java library for communicating with Salesforce. </td></tr>
<tr><td> <a href='SQLForce.md'>SQLForce</a> </td><td> Salesforce Admin</td><td> Command line interpreter with ANSI SELECT/DELETE/MODIFY//INSERT commands that work with Salesforce. The <a href='SQLForceForJython.md'>SQLForceForJython</a> is a superset of this project.  NOTE: The latest release (always free) can be found at <a href='http://www.capstorm.com'>CAPSTORM</a>.</td></tr>
<tr><td> <a href='SQLForceForJython.md'>SQLForceForJython</a> </td><td> Salesforce Admin </td><td> Jython module with ANSI SELECT/DELETE/MODIFY/INSERT commands that work Salesforce. NOTE: The latest release (always free) can be found at <a href='http://www.capstorm.com'>CAPSTORM</a>. The <a href='http://www.capstorm.com'>CAPSTORM</a> version supports the latest Salesforce protocol.</td></tr>
<tr><td> CopyForce      </td><td> Salesforce Admin </td><td> Copy a Salesforce instance to a local RDBMS, SQL Server, Oracle, and H2 are supported. NOTE: Work on this project has been migrated to <a href='http://www.capstorm.com/main'>CAPSTORM</a>. The <a href='http://www.capstorm.com'>CAPSTORM</a> version is faster and supports the latest Salesforce protocol.</td></tr></tbody></table>


All of these tools are part of the <b>SQLForce</b> project.<br>
<br>
<h1>Origins of <b>SQLForce</b></h1>

SQLForce was initially created for several reasons:<br>
<ul><li>We needed ANSI SELECT, SELECT DISTINCT, SELECT/UNION, DELETE, MODIFY, and INSERT commands that just worked.<br>
</li><li>SOQL and Salesforce's record limits made it just too hard to modify a lot of records.<br>
</li><li>We needed to change all occurences of "United States of America" to "USA" and wanted to use a SQL UPDATE statement.</li></ul>

Overtime, the base java libraries have been used to various other tools including a rich Jython module. We have used the tools, especially the Jython module, for production tasks since early 2009. The first time you write a script like:<br>
<pre><code>UPDATE Contact SET MailingCountry="USA" WHERE MailingCountry IN ("United States", "US")<br>
</code></pre>
you will be hooked. For any Salesforce administrator, SQLForce simply saves a lot of time.<br>
<br>
Later we started worrying about what would happen if a Salesforce user deleted a lot of data and emptied their recycle bin. <a href='CopyForce.md'>CopyForce</a> was born. <a href='CopyForce.md'>CopyForce</a> copies all or part<br>
of a Salesforce instance to a local RDBMS.<br>
<br>
The java libraries use the partner wsdl and are typically upgraded within a few weeks after Salesforce upgrades.<br>
<br>
<h1><b>SQLForce</b> as a Toddler</h1>
Once we starting using jython to manipulate Salesforce, we saw a huge potential risk.<br>
<ul><li>A disgruntled employee could download <b>SQLForce</b> and and destroy a lot of our Salesforce data in just a few minutes.<br>
What would you do if a employee downloaded <b>SQLForce</b> and ran something like:<br>
<pre><code>UPDATE Contact SET firstName='Bill', lastName='Clinton', email='bill@arkansas.com'<br>
</code></pre>
In a couple minutes this one line command would corrupt every contact record accessible  by the user.<br>
CopyForce was developed to provide insurance against such an event. Now we have local full and incremental backups!  As a bonus, we have found CopyForce to be an excellent tool for copying parts of Salesforce to a variety RDBMS.
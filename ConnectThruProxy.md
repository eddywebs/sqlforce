# Connecting thru a Proxy #

By default none of the SQL force tools can connect thru a proxy.
Good news! With a view command line options connecting thru a proxy is a simple task.

The key is to set the following java variables on the command line:
|**Java Variable**|**Notes**|
|:----------------|:--------|
|http.proxyHost   |See what your browser uses|
|http.proxyPort   |Ditto    |
|javax.net.ssl.trustStoreProvider|SunMSCAPI on Windows|
|javax.net.ssl.trustStoreType|Windows-ROOT on Windows|

See [Oracle](http://download.oracle.com/javase/6/docs/technotes/guides/net/proxies.html) for details on all proxy related system variables.

# Windows #
To use the proxy and certificate store used by your browser, you will need a command line like:
```
java -Dhttp.proxyHost=134.5.1.1 -Dhttp.proxyPort=8089 \
-Djavax.net.ssl.trustStoreProvider=SunMSCAPI \
-Djavax.net.ssl.trustStoreType=Windows-ROOT \
-jar CopyForceH2.jar
```

That's it! Once the variable are set up CopyForce, sqlforce, etc. will happily chat thru your proxy server.
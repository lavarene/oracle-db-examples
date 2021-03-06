# Connection Management Samples in JDBC 

Brief description of connection management related code samples.

|Author | Date |
|-------|------|
|nirmala.sundarappa|06/14/16|

----
Creating a connection is an expensive database operation which
involves several background operations such as network communication, reading 
connection strings, authentication, transaction enlistment, foreground process 
creation and memory allocation.  Each of these processes contributes to the 
amount of time and resources taken to create a connection object. Repeated 
connection creation and destruction will significantly impact Java application 
scalability.

"Connection Management" code samples explain various ways of connecting to an
Oracle Database and explain use-cases to be considered while choosing the 
connection management strategy. The section below provides more details on 
specific connection management strategy. 

----
## DataSourceSample.java:
This sample shows how to connect to a simple DataSource 
(oracle.jdbc.pool.OracleDataSource) and how to set connection related 
properties such as `defaultRowPrefetch`, `defaultBatchValue` etc., 

## InternalT2Driver.sql & InternalT2Driver.java: 
The server-side Type 2 (T2S) driver (aka KPRB driver) is for Java in the 
database. It uses database session directly for accessing local data. 
T2S driver is used for better performance because it cuts network traffic
between the Java code and the RDBMS SQL engine.

## InternalT4Driver.sql & InternalT4Driver.java:
The server side Type 4(T4S) driver (aka thin/T4 driver) is used for code 
running Java in database session needing access to another session either on
the same RDBMS instance/server or on a remote RDBMS instance/server.

## ProxySessionSample.java and ProxySessionSample.sql:
This sample shows connecting to the Oracle Database using Proxy 
authentication or N-tier authentication. Proxy authentication is the
process of using a middle tier for user authentication. Proxy connections
can be created using any one of the following options. 
(a) USER NAME: Done by supplying the user name or the password or both.
(b) DISTINGUISHED NAME: This is a global name in lieu of the password of
the user being proxied for.
(c) CERTIFICATE:More encrypted way of passing the credentials of the user,
 who is to be proxied, to the database.
    
## DRCPSample.java:
DRCP can be used with or without a client side connection pool. 
Either UCP or any other third party connection pool (eg., C3P0) can be used as
client side pool. Note that, when UCP is used, it takes care of attaching and 
releasing server connections. There is no need to explicitly call 
`attachServerConnection()`/`detachServerConnection()` with UCP. 

----


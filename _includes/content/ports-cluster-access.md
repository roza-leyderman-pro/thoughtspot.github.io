## Ports for inbound and outbound cluster access

ThoughtSpot uses static ports for inbound and outbound access to the cluster.

|Port|Protocol|Service Name|Direction|Source|Destination|Description|
|----|--------|------------|---------|------|-----|-----------|
|22|SCP|SSH|bidirectional|ThoughtSpot Support|All nodes|Secure shell access.|
|25 or 587|SMTP|SMTP or Secure SMTP|outbound|All nodes and SMTP relay (provided by customer)|All nodes|Allow outbound access for the IP address of whichever email relay server is in use. This is for sending alerts to ThoughtSpot Support. <br>In ThoughtSpot release 6.1.1 or later, and in release 6.0.5, you can specify a custom port to connect to the relay host, instead of port 25 or 587. Refer to <a href="{{ site.baseurl }}/admin/setup/set-up-relay-host.html">Set the relay host for SMTP</a>.|
|80|HTTP|HTTP|bidirectional|ThoughtSpot Support|All nodes|Hypertext Transfer Protocol for website traffic.|
|123|UDP|NTP service|bidirectional|ThoughtSpot Support|All nodes|Port used by NTP service.|
|389 or 636|TCP|LDAP or LDAPS|outbound|All nodes and LDAP server, provided by customer|All nodes|Allow outbound access for the IP address of the LDAP server in use.|
|443|HTTPS|HTTPS|bidirectional|ThoughtSpot Support|All nodes|Secure HTTP.|
|443|TCP|HTTPS|outbound|All nodes|208.83.110.20 |For transferring files to thoughtspot.egnyte.com.|
|443|TCP|HTTPS|outbound|All nodes|For transferring product usage data to mixpanel cloud.|outbound|
|443|TCP|HTTPS|outbound|All nodes|je8b47jfif.execute-api.us-east-2.amazonaws.com <br> s3.us-west-1.amazonaws.com <br> s3-us-west-1.amazonaws.com <br> s3.dualstack.us-west-1.amazonaws.com|For transferring monitoring data to InfluxCloud. (Given address will resolve to point to AWS instances).|
|587 or 25|SMTP|SMTP or Secure SMTP|outbound|All nodes and SMTP relay (provided by customer)|All nodes|Allow outbound access for the IP address of whichever email relay server is in use. This is for sending alerts to ThoughtSpot Support. <br>In ThoughtSpot release 6.1.1 or later, and in release 6.0.5, you can specify a custom port to connect to the relay host, instead of port 25 or 587. Refer to <a href="{{ site.baseurl }}/admin/setup/set-up-relay-host.html">Set the relay host for SMTP</a>.|
|636 or 389|TCP|LDAP or LDAPS|outbound|All nodes and LDAP server, provided by customer|All nodes|Allow outbound access for the IP address of the LDAP server in use.|
|2049|TCP|NFS: In case one needs to mount NFS share on TS node. |bidirectional|ThoughtSpot Support|All nodes|Port used by NFS.|
|9000|HTTP|DataFlow|bidirectional|All users’ IP address|Node that runs DataFlow|Port used for accessing DataFlow|
|12345|TCP|Simba|bidirectional|ThoughtSpot Support|All nodes|Port used by ODBC and JDBC drivers when connecting to ThoughtSpot.|
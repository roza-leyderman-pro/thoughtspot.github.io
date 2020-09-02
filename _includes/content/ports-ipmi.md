## Ports for Intelligent Platform Management Interface (IPMI)

ThoughtSpot uses static ports for out-of-band IPMI communications between the cluster and ThoughtSpot support.

|Port|Protocol|Service Name|Direction|Source|Dest.|Description|
|----|--------|------------|---------|------|-----|-----------|
|80|HTTP|HTTP|bidirectional|ThoughtSpot Support|All nodes|Hypertext Transfer Protocol for website traffic.|
|443|TCP|S-HTTP|bidirectional|ThoughtSpot Support|All nodes|IPMI GUI and for HTML5-based IPMI console access.|
|623|UDP|Serial-over-LAN|bidirectional|ThoughtSpot Support|All nodes|IPMI GUI and for HTML5-based IPMI console access.|
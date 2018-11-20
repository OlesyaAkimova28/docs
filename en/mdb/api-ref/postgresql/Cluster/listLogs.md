# Method listLogs
Retrieves logs for the specified PostgreSQL cluster.
For more information about logs, see the [Logs](/docs/yandex-mdb-guide/concepts/logs) section in the Developer's Guide.
 

 
## HTTP request {#https-request}
```
GET https://mdb.api.cloud.yandex.net/managed-postgresql/v1/clusters/{clusterId}:logs
```
 
## Path parameters {#path_params}
 
Parameter | Description
--- | ---
clusterId | Required. ID of the PostgreSQL cluster to request logs for. To get the PostgreSQL cluster ID use a [list](/docs/mdb/api-ref/postgresql/Cluster/list) request.  The maximum string length in characters is 50.
 
## Query parameters {#query_params}
 
Parameter | Description
--- | ---
columnFilter | Columns from the logs table to request. If no columns are specified, entire log records are returned.
serviceType | Type of the service to request logs about.
fromTime | Start timestamp for the logs request, in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format.
toTime | End timestamp for the logs request, in [RFC3339](https://www.ietf.org/rfc/rfc3339.txt) text format.
pageSize | The maximum number of results per page to return. If the number of available results is larger than [pageSize](/docs/mdb/api-ref/postgresql/Cluster/listLogs#query_params), the service returns a [nextPageToken](/docs/mdb/api-ref/postgresql/Cluster/listLogs#responses) that can be used to get the next page of results in subsequent list requests.  The maximum value is 1000.
pageToken | Page token. To get the next page of results, set [pageToken](/docs/mdb/api-ref/postgresql/Cluster/listLogs#query_params) to the [nextPageToken](/docs/mdb/api-ref/postgresql/Cluster/listLogs#responses) returned by a previous list request.  The maximum string length in characters is 100.
 
## Response {#responses}
**HTTP Code: 200 - OK**


 
Field | Description
--- | ---
logs | **object**<br><p>Requested log records.</p> 
logs.<br>timestamp | **string** (date-time)<br><p>Log record timestamp in <a href="https://www.ietf.org/rfc/rfc3339.txt">RFC3339</a> text format.</p> 
logs.<br>message | **object**<br><p>Contents of the log record.</p> 
nextPageToken | **string**<br><p>This token allows you to get the next page of results for list requests. If the number of results is larger than <a href="/docs/mdb/api-ref/postgresql/Cluster/listLogs#query_params">pageSize</a>, use the <a href="/docs/mdb/api-ref/postgresql/Cluster/listLogs#responses">nextPageToken</a> as the value for the <a href="/docs/mdb/api-ref/postgresql/Cluster/listLogs#query_params">pageToken</a> query parameter in the next list request. Each subsequent list request will have its own <a href="/docs/mdb/api-ref/postgresql/Cluster/listLogs#responses">nextPageToken</a> to continue paging through the results.</p> 
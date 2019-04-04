# Introduction to Alibaba Cloud API {#concept_dwx_cmf_ndb .concept}

Alibaba Cloud offers two different types of APIs: RPC APIs and REST APIs. The calling method is different for each API type.

For both API types, you must sign the API request when manually calling an API. However, if you use the Alibaba Cloud SDK to call APIs, the SDK will automatically sign the request according to the configured AccessKey.

## RPC APIs {#section_rn1_hmf_ndb .section}

A Remote Procedure Calling \(RPC\) is initiated by the client. The client sends a request with supplied parameters to call a method or function of the server to execute an operation.

In general, the API that requires the Action parameter belongs to the RPC type. The APIs of products like Elastic Compute Service, ApsaraDB for RDS, Server Load Balancer, CDN, and many other products are all RPC APIs.

The structure of an RPC request is as follows:

`http://Endpoint/?Action=xx&Parameters`

Where:

-   Endpointis the entry of the Alibaba Cloud service to call. For example, `ecs.aliyuncs.com`.
-   Action is the operation to perform. For example, useStartInstance to start an ECS instance.

-   Parameters are request parameters separated by ampersands \(&\).

    Request parameters consist of common parameters and API specific parameters. Common parameters include VPI version, credentials and more.


The following is a request example of StartInstance.

**Note:** To make examples easier to read, the request examples are displayed as follows in Alibaba Cloud documentations:

```
https://ecs.aliyuncs.com/?Action=StartInstance
&InstanceId=i-instance1
&CommonParameters
```

## REST APIs {#section_ijz_rmf_ndb .section}

Representational State Transfer \(REST\) is an architectural style for designing web applications. The APIs of products like Resource Orchestration Service and Container Service are REST APIs.

The structure of a REST request is as follows:

`HTTP_method/URI&parameters`

Where:

-   HTTP\_method is the HTTP method to use. For example: PUT, POST, GET, and DELETE.
-   URI is the identifier of the web resource to call. For example: `/cluster`.
-   Parameters are request parameters.

    Request parameters consist of common parameters and API specific parameters. Common parameters include VPI version, credentials and more.

-   
The following example is a request that searches all the clusters:

```
GET /clusters/C5b5e80b0b64a4bf6939d2d8fbbc5ded7 HTTP/1.1
CommonParameters
```


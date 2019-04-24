# 阿里云API介绍 {#concept_187755 .concept}

阿里云云产品的API分为RPC和RESTful两种类型，不同类型的API的调用方式也不同。

## RPC风格API {#section_wq3_5tm_o6r .section}

RPC \(Remote Procedure Calling\)，即从一台机器（客户端）上通过参数传递的方式调用另一台机器（服务器）上的一个函数或方法（可以统称为服务），并得到返回的结果。通常，API中有Action参数的是RPC API，大部分云产品都属于RPC风格，比如云服务器ECS、云数据库RDS、负载均衡SLB和CDN等云产品都提供RPC API。

RPC API的请求结构如下：

``` {#codeblock_fbj_3ci_zbl}
http://Endpoint/?Action=xx&Parameters
```

其中：

 Endpoint
 :   调用的云服务的接入点，如`ecs.aliyuncs.com`。

  Action
 :   要执行的操作，如使用StartInstance接口启动一个ECS实例。

  Prameters
 :   请求参数，每个参数之间用“&”分隔。

    请求参数由公共请求参数和API自定义参数组成。公共参数中包含API版本号、身份验证等信息。

 以下是ECS的StartInstance接口的请求示例：

``` {#codeblock_d32_qnu_uhx}
https://ecs.aliyuncs.com/?Action=StartInstance&InstanceId=i-instance1&公共请求参数
```

## RESTful API {#section_70r_qc6_ckl .section}

REST（Representational State Transfer）是在Web开发过程中的一种通过URL进行系统结构设计的新思维方式。资源编排、容器服务和批量计算等云产品提供RESTful API。

RESTful API的请求结构如下：

``` {#codeblock_svx_2ia_6z7}
HTTP_method/URI&parameters
```

其中：

 HTTP\_method
 :   请求使用的方法，包括PUT、 POST、 GET、 DELETE。

  URI
 :   请求要调用的资源标示符，如/cluster。

  Prameters
 :   请求参数由公共请求参数和API自定义参数组成。公共参数中包含API版本号、身份验证等信息。

 以下是一个查看集群实例的请求示例：

``` {#codeblock_z9h_z1c_08f}
GET /clusters/C5b5e80b0b64a4bf6939d2d8fbbc5ded7 HTTP/1.1公共请求头
```


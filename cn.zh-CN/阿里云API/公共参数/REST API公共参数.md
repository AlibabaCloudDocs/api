# REST API公共参数 {#reference_trt_bh3_ndb .reference}

在使用阿里云云产品API发起请求时，除了每个API特别要求的必须参数，您还需要提供签名、API版本等公共参数。

## 公共请求参数 {#section_xl4_2qf_ndb .section}

公共请求参数是每个接口调用都需要提供的请求参数。

|名称|类型|是否必须|描述|
|--|--|----|--|
|Accept|String|否|返回消息的格式。取值：application/json | application/xml 

|
|Content-MD5|String|是|HTTP协议消息体的128-bit MD5散列值转换成BASE64编码的结果。|
|Content-Type|String|是|RFC 2616中定义的HTTP请求内容类型。|
|Content-Length|String|是|RFC 2616中定义的HTTP请求内容长度。|
|Date|String|是|请求的构造时间，目前只支持 UTC 格式。例如：Wed, 05 Sep. 2012 23:00:00 UTC。|
|Host|String|是|请求域名，比如`diku.aliyuncs.com`。|
|Authorization|String|是|请求签名，格式为 `Authorization: acs *AccessKeyId*:*signature*`。|
|x-acs-signature-nonce|String|是|唯一随机数，用于防止网络重放攻击。在不同请求间要使用不同的随机数。|
|x-acs-signature-method|String|是|签名方式，目前只支持HMAC-SHA1。|
|x-acs-signature-version|String|是|签名版本，取值：1.0

|
|x-acs-version|String|是|API 版本号，以日期形式YYYY-MM-DD输入，例如： 2014-05-26。各产品的API版本号都不同，请参见具体的产品API文档获取API版本号。

|

**请求示例**

```
GET http://ros.aliyuncs.com/stacks HTTP/1.1
x-acs-signature-method: HMAC-SHA1
Authorization: acs ACSTQDkNtSMrZtwL:E9tMDBiLOywWyO1NJubGXV2Dq08=
Date: Fri, 11 Sep 2015 05:28:05 GMT
x-acs-signature-version: 1.0
x-sdk-client: Java/2.0.0
Accept: application/octet-stream
x-acs-version: 2015-09-01
Cache-Control: no-cache
Pragma: no-cache
Host: ros.aliyuncs.com
Connection: keep-alive
```

## 公共返回参数 {#section_km4_2qf_ndb .section}

API返回结果采用统一格式，返回2xx HTTP状态码代表调用成功；返回4xx或5xx HTTP状态码代表调用失败。调用成功返回的数据格式有XML和JSON两种，可以在发送请求时指定返回的数据格式，默认为JSON格式。

每次接口调用，无论成功与否，都会在Header中返回一个请求IDX-Acs-Request-Id。

**返回示例**

```
HTTP/1.1 200 OK
Date: Fri, 11 Sep 2015 05:28:06 GMT
Content-Type: application/json; charset=UTF-8
Content-Length: 945
Connection: close
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: POST, GET, OPTIONS
Access-Control-Allow-Headers: X-Requested-With, X-Sequence, _aop_secret, _aop_signature
Access-Control-Max-Age: 172800
X-Acs-Request-Id: 1DD1048F-0B74-48EB-9364-E509C5072964
/* 返回结果数据 */
```


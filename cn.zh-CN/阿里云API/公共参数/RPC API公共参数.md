# RPC API公共参数 {#reference_fb1_p4f_ndb .reference}

在使用阿里云云产品API发起请求时，除了每个API特别要求的必须参数，您还需要提供签名、API版本等公共参数。

## 公共请求参数 {#section_xl4_2qf_ndb .section}

公共请求参数是每个接口调用都需要提供的请求参数。

|名称|类型|是否必须|描述|
|:-|:-|----|--|
|Format|String|否|返回消息的格式。取值：JSON \(默认值\) | XML 

|
|Version|String|是|API 版本号，以日期形式YYYY-MM-DD输入，例如： 2014-05-26。各产品的API版本号都不同，请参见具体的产品API文档获取API版本号。

|
|AccessKeyId|String|是|访问服务使用的密钥ID。|
|Signature|String|是|签名结果串。|
|SignatureMethod|String|是|签名方式，取值：HMAC-SHA1

|
|Timestamp|String|是|请求的时间戳，为日期格式。使用UTC时间按照 ISO8601标，格式为`YYYY-MM-DDThh:mm:ssZ`。例如，北京时间2013年1月10日20点0分0秒，表示为2013-01-10T12:00:00Z。

|
|SignatureVersion|String|是|签名算法版本，取值：1.0

|
|SignatureNonce|String|是|唯一随机数，用于防止网络重放攻击。在不同请求间要使用不同的随机数值。

|

**示例**

```
https://ecs.aliyuncs.com/?Action=DescribeInstances
&Timestamp=2014-05-19T10%3A33%3A56Z
&Format=xml
&AccessKeyId=testid
&SignatureMethod=Hmac-SHA1
&SignatureNonce=NwDAxvLU6tFE0DVb
&Version=2014-05-15
&SignatureVersion=1.0
&Signature=Signature
&&RegionId=cn-hangzhou
```

## 公共返回参数 {#section_km4_2qf_ndb .section}

API返回结果采用统一格式，返回2xx HTTP状态码代表调用成功；返回4xx或5xx HTTP状态码代表调用失败。调用成功返回的数据格式有XML和JSON两种，可以在发送请求时指定返回的数据格式，默认为JSON格式。

每次接口调用，无论成功与否，系统都会返回一个唯一识别码RequestId。

-   XML格式

    ```
    <?xml version="1.0" encoding="utf-8"?> 
        <!—结果的根结点-->
        <接口名称+Response>
            <!—返回请求标签-->
            <RequestId>4C467B38-3910-447D-87BC-AC049166F216</RequestId>
            <!—返回结果数据-->
        </接口名称+Response>
    
    ```

-   JSON格式

    ```
    {
        "RequestId":"4C467B38-3910-447D-87BC-AC049166F216",
        /*返回结果数据*/
        }
    ```



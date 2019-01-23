# RAM鉴权 {#concept_xgm_5hj_ndb .concept}

在使用RAM账号调用阿里云API前，需要主账号通过创建授权策略对RAM账号进行授权。

## 资源授权 {#section_yrd_n3j_ndb .section}

默认子账号没有权限通过调用阿里云API去创建、修改云资源。使用子账号调用API时，您需要先创建一个授权策略，然后将这个授权策略关联给对应的子账号完成资源授权。

在创建授权策略时，您可以通过ARN \(Aliyun Resource Name\) 指定要授权的资源。ARN 是阿里云为每个资源定义的一个全局的阿里云资源名称。

ARN格式如下：

```
acs:*service-name*:*region*:*account-id*:*resource-relative-id*
```

其中：

-   acs：Alibaba Cloud Service的首字母缩写，表示阿里云的公共云平台。
-   service-name：阿里云云服务的名称，如ecs, oss, slb等。
-   region：地域信息。如果不支持该项，可以使用通配符星号（\*）来代替。

-   account-id：账号ID，比如 1234567890123456。

-   resource-relative-id：具体的资源描述，不同的云产品的资源描述也不同，详情参见各云产品的开发文档。

    比如`acs:oss::1234567890123456:sample_bucket/file1.txt`表示OSS服务中对象名称是sample\_bucket/file1.txt的资源，对象的所有者是UID为`1234567890123456`。


## 示例 {#section_y3y_y3j_ndb .section}

以下授权策略示例中，包含如下两条授权规则：

-   允许有对华东 1（杭州）地域所有ECS资源查看的权限（`ecs:Describe*`）。
-   允许有对OSS的mybucket存储桶中的对象的读和访问权限（`oss:ListObjects, oss:GetObject`），并限制请求者的IP来源必须是42.120.88.10或42.120.66.0/24。

```
"Version": "1",
      "Statement": [
          {
              "Effect": "Allow",
              "Action": "ecs:Describe*",
              "Resource": "acs:ecs:cn-hangzhou:*:*"
          },
          {
              "Effect": "Allow",
              "Action": [
                  "oss:ListObjects",
                  "oss:GetObject"
              ],
              "Resource": [
                  "acs:oss:*:*:mybucket",
                  "acs:oss:*:*:mybucket/*"
              ],
              "Condition":{
                  "IpAddress": {
                      "acs:SourceIp": ["42.120.88.10", "42.120.66.0/24"]
                  }
              }
          }
      ]
}
```


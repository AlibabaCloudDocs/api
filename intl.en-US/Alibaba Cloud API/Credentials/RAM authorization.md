# RAM authorization {#concept_xgm_5hj_ndb .concept}

Before calling Alibaba Cloud APIs using a RAM account, the primary account must grant the RAM user the corresponding permission by creating an authorization policy.

## Resource authorization {#section_yrd_n3j_ndb .section}

By default, a RAM user does not have the permission to call an Alibaba Cloud API to create or modify a cloud resource. To use a RAM account to call Alibaba Cloud APIs, you must first create an authorization policy and then attach the policy to the RAM account to make the account have the corresponding permission.

When creating an authorization policy, you can use Alibaba Resource Name \(ARN\) to specify the resource to authorize. Each resource has an ARN, which is its global resource name defined by Alibaba Cloud.

The ARN format is as follows:

`acs:*service-name*:*region*:*account-id*:*resource-relative-id*`

Where:

-   `acs` is abbreviation for Alibaba Cloud Service.

-   `service-name` is the service name such as ecs, oss, and slb.

-   `region` is the region of the service. Use an asterisk \(\*\) to replace it when it is not supported.

-   `account-id` is the ID of the resource owner, such as 1234567890123456.

-   `resource-relative-id` is the resource description. The description varies by product. See specific product API documentation for more information.

    For example, `acs:oss::1234567890123456:sample_bucket/file1.txt` refers to a resource named sample\_bucket/file1.txt and the resource owner ID is `1234567890123456`.


## Examples {#section_y3y_y3j_ndb .section}

The following policy contains two permissions:

-   Allow the RAM user to view all ECS instances in the China East 1 \(Hangzhou\) region \(`ecs:Describe*`\).

-   Allow the RAM user to read and access the objects in the mybucket bucket of OSS \(`oss:ListObjects, oss:GetObject`\), and the request must come from 42.120.88.10 or 42.120.66.0/24.


```
"Version": "1",
      "Statement ":[
          {
              "Effect": "Allow",
              "Action": "ECs: Describe *",
              "Resource": "ACS: ECs: CN-Hangzhou :*:*"
          },
          {
              "Effect": "allow ",
                          "Action": [
                  "Oss: maid ",
                  "Oss: GetObject"
              ],
              "Resource": [
                  "ACS: OSS: *: mybucket ",
                  "ACS: OSS: *: mybucket /*"
              ],
              "Condition":{
                  "IPaddress ":{
                      "ACS: sourceip": ["maid", "maid/24"]
                  }
              }
          }
      ]
}
```


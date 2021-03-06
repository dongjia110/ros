# ALIYUN::VPC::EIP

ALIYUN::VPC::EIP类型用于申请弹性公网IP。

## 语法

```
{
  "Type": "ALIYUN::VPC::EIP",
  "Properties": {
    "DeletionProtection": Boolean,
    "Name": String,
    "Tags": List,
    "Isp": String,
    "Netmode": String,
    "Period": Number,
    "ResourceGroupId": String,
    "AutoPay": Boolean,
    "InstanceChargeType": String,
    "PricingCycle": String,
    "Bandwidth": Number,
    "InternetChargeType": String,
    "Description": String
  }
}
```

## 属性

|属性名称|类型|必须|允许更新|描述|约束|
|----|--|--|----|--|--|
|DeletionProtection|Boolean|否|否|是否开启删除保护功能。|取值： -   true
-   false（默认值） |
|Name|String|否|是|弹性公网IP的名称。|长度为2~128个字符。以英文字母开头，不能以`http://`或`https://`开头。可包含英文字母、数字、英文句点（.）、下划线（\_）和短划线（-）。|
|ResourceGroupId|String|否|否|资源组ID。|无|
|Netmode|String|否|否|网络类型。|默认值：public。|
|Bandwidth|Number|否|是|带宽值。|如果不指定，则取默认值5Mbps。|
|InternetChargeType|String|否|否|EIP的计费方式。|取值： -   PayByBandwidth（默认值）：按带宽计费。
-   PayByTraffic：按流量计费。 |
|InstanceChargeType|String|否|否|EIP的付费方式。|取值： -   Prepaid：预付费。
-   Postpaid（默认值）：后付费。 |
|PricingCycle|String|否|否|预付费的计费周期。|取值： -   Month（默认值）：按月付费。
-   Year：按年付费。

**说明：** InstanceChargeType参数取值为Prepaid时，该参数必选。 |
|Period|Number|否|否|购买时长。|取值： -   选择按月付费时，取值范围： 1~9。
-   选择按年付费时，取值范围： 1~3。

默认值： 1。

**说明：** InstanceChargeType参数取值为Prepaid时，该参数必选。 |
|AutoPay|Boolean|否|否|是否自动付费。|取值： -   false：不开启自动付费，生成订单后需要到订单中心完成支付。订单中心详情，请参见[订单中心](https://expense.console.aliyun.com/?#/order/list/)。
-   true：开启自动付费，自动支付订单。

**说明：** InstanceChargeType参数取值为Prepaid时，该参数必选。 |
|Isp|String|否|否|用于金融云的ISP标签，仅对cn-hangzhou地域有效。|如果您不是金融云用户，该参数会被忽略。|
|Description|String|否|是|弹性公网IP的描述信息。|长度为2~256个字符。以英文字母开头，不能以`http://`或`https://`开头。|
|Tags|List|否|否|标签。|最多设置20个标签，每个标签由键值对组成。标签值可以为空。详情请参见[Tags属性](#section_de8_mzg_qyq)。 |

## Tags语法

```
"Tags": [
  {
    "Key": String,
    "Value": String
  }
]  
```

## Tags属性

|属性名称|类型|必须|允许更新|描述|约束|
|----|--|--|----|--|--|
|Key|String|是|否|标签键|长度为1~128个字符，不能以`aliyun`和`acs:`开头，不能包含`http://`或`https://` 。|
|Value|String|否|否|标签值|长度为0~128个字符，不能以`aliyun`和`acs:`开头，不能包含`http://`或`https://` 。|

## 返回值

Fn::GetAtt

-   EipAddress：分配的弹性公网IP。
-   AllocationId：弹性公网IP的实例ID。
-   OrderId：选择预付费时返回的订单号。

## 示例

`JSON`格式

```
{
  "ROSTemplateFormatVersion": "2015-09-01",
  "Parameters": {
    "Description": {
      "Type": "String",
      "Description": "Optional. The description of the EIP. The description must be 2 to 256 characters in length. It must start with a letter. It cannot start with http://  or https://."
    },
    "ResourceGroupId": {
      "Type": "String",
      "Description": "Resource group id."
    },
    "InstanceChargeType": {
      "Type": "String",
      "Description": "The resource charge type. Default value is Postpaid",
      "AllowedValues": [
        "Prepaid",
        "Postpaid"
      ],
      "Default": "Postpaid"
    },
    "PricingCycle": {
      "Type": "String",
      "Description": "Price cycle of the resource. This property has no default value. If ChargeType is specified as Postpaid, this value will be ignore.",
      "AllowedValues": [
        "Month",
        "Year"
      ],
      "Default": "Month"
    },
    "Isp": {
      "Type": "String",
      "Description": "ISP tag for finance cloud region. only for cn-hangzhou and cn-qingdao region), if you are not finance cloud user, this value will be ignore."
    },
    "Period": {
      "Type": "Number",
      "Description": "Prepaid time period. While choose by pay by month, it could be from 1 to 9. While choose pay by year, it could be from 1 to 3.",
      "MinValue": 1,
      "MaxValue": 9,
      "Default": 1
    },
    "DeletionProtection": {
      "Type": "Boolean",
      "Description": "Whether to enable deletion protection.\nDefault to False.",
      "AllowedValues": [
        "True",
        "true",
        "False",
        "false"
      ],
      "Default": false
    },
    "AutoPay": {
      "Type": "Boolean",
      "Description": "Automatic Payment. Default is false.",
      "AllowedValues": [
        "True",
        "true",
        "False",
        "false"
      ],
      "Default": false
    },
    "Name": {
      "Type": "String",
      "Description": "The name of the EIP. The name must be 2 to 128 characters in length. It must start with a letter. It can contain numbers, periods (.), underscores (_), and hyphens (-). It cannot start with http://  or https://"
    },
    "InternetChargeType": {
      "Type": "String",
      "Description": "The network charge type. Support 'PayByBandwidth' and 'PayByTraffic' only. Default is PayByBandwidth. PayByTraffic will charge by hour, PayByBandwidth will charge by day. ",
      "AllowedValues": [
        "PayByBandwidth",
        "PayByTraffic"
      ],
      "Default": "PayByBandwidth"
    },
    "Netmode": {
      "Type": "String",
      "Description": "The network type. Valid value: public (public network)."
    },
    "Bandwidth": {
      "Type": "Number",
      "Description": "Bandwidth for the output network. Default is 5MB.",
      "Default": 5
    },
    "Tags": {
      "Type": "Json",
      "Description": "Tags to attach to eip. Max support 20 tags to add during create eip. Each tag with two properties Key and Value, and Key is required.",
      "MaxLength": 20
    }
  },
  "Resources": {
    "ElasticIp": {
      "Type": "ALIYUN::VPC::EIP",
      "Properties": {
        "Description": {
          "Ref": "Description"
        },
        "ResourceGroupId": {
          "Ref": "ResourceGroupId"
        },
        "InstanceChargeType": {
          "Ref": "InstanceChargeType"
        },
        "PricingCycle": {
          "Ref": "PricingCycle"
        },
        "Isp": {
          "Ref": "Isp"
        },
        "Period": {
          "Ref": "Period"
        },
        "DeletionProtection": {
          "Ref": "DeletionProtection"
        },
        "AutoPay": {
          "Ref": "AutoPay"
        },
        "Name": {
          "Ref": "Name"
        },
        "InternetChargeType": {
          "Ref": "InternetChargeType"
        },
        "Netmode": {
          "Ref": "Netmode"
        },
        "Bandwidth": {
          "Ref": "Bandwidth"
        },
        "Tags": {
          "Ref": "Tags"
        }
      }
    }
  },
  "Outputs": {
    "AllocationId": {
      "Description": "ID that Aliyun assigns to represent the allocation of the address for use with VPC. Returned only for VPC elastic IP addresses.",
      "Value": {
        "Fn::GetAtt": [
          "ElasticIp",
          "AllocationId"
        ]
      }
    },
    "EipAddress": {
      "Description": "IP address of created EIP.",
      "Value": {
        "Fn::GetAtt": [
          "ElasticIp",
          "EipAddress"
        ]
      }
    },
    "OrderId": {
      "Description": "Order ID of prepaid EIP instance.",
      "Value": {
        "Fn::GetAtt": [
          "ElasticIp",
          "OrderId"
        ]
      }
    }
  }
}
```

`YAML`格式

```
ROSTemplateFormatVersion: '2015-09-01'
Parameters:
  Description:
    Type: String
    Description: >-
      Optional. The description of the EIP. The description must be 2 to 256
      characters in length. It must start with a letter. It cannot start with
      http://  or https://.
  ResourceGroupId:
    Type: String
    Description: Resource group id.
  InstanceChargeType:
    Type: String
    Description: The resource charge type. Default value is Postpaid
    AllowedValues:
      - Prepaid
      - Postpaid
    Default: Postpaid
  PricingCycle:
    Type: String
    Description: >-
      Price cycle of the resource. This property has no default value. If
      ChargeType is specified as Postpaid, this value will be ignore.
    AllowedValues:
      - Month
      - Year
    Default: Month
  Isp:
    Type: String
    Description: >-
      ISP tag for finance cloud region. only for cn-hangzhou and cn-qingdao
      region), if you are not finance cloud user, this value will be ignore.
  Period:
    Type: Number
    Description: >-
      Prepaid time period. While choose by pay by month, it could be from 1 to
      9. While choose pay by year, it could be from 1 to 3.
    MinValue: 1
    MaxValue: 9
    Default: 1
  DeletionProtection:
    Type: Boolean
    Description: |-
      Whether to enable deletion protection.
      Default to False.
    AllowedValues:
      - 'True'
      - 'true'
      - 'False'
      - 'false'
    Default: false
  AutoPay:
    Type: Boolean
    Description: Automatic Payment. Default is false.
    AllowedValues:
      - 'True'
      - 'true'
      - 'False'
      - 'false'
    Default: false
  Name:
    Type: String
    Description: >-
      The name of the EIP. The name must be 2 to 128 characters in length. It
      must start with a letter. It can contain numbers, periods (.), underscores
      (_), and hyphens (-). It cannot start with http://  or https://
  InternetChargeType:
    Type: String
    Description: >-
      The network charge type. Support 'PayByBandwidth' and 'PayByTraffic' only.
      Default is PayByBandwidth. PayByTraffic will charge by hour,
      PayByBandwidth will charge by day.
    AllowedValues:
      - PayByBandwidth
      - PayByTraffic
    Default: PayByBandwidth
  Netmode:
    Type: String
    Description: 'The network type. Valid value: public (public network).'
  Bandwidth:
    Type: Number
    Description: Bandwidth for the output network. Default is 5MB.
    Default: 5
  Tags:
    Type: Json
    Description: >-
      Tags to attach to eip. Max support 20 tags to add during create eip. Each
      tag with two properties Key and Value, and Key is required.
    MaxLength: 20
Resources:
  ElasticIp:
    Type: 'ALIYUN::VPC::EIP'
    Properties:
      Description:
        Ref: Description
      ResourceGroupId:
        Ref: ResourceGroupId
      InstanceChargeType:
        Ref: InstanceChargeType
      PricingCycle:
        Ref: PricingCycle
      Isp:
        Ref: Isp
      Period:
        Ref: Period
      DeletionProtection:
        Ref: DeletionProtection
      AutoPay:
        Ref: AutoPay
      Name:
        Ref: Name
      InternetChargeType:
        Ref: InternetChargeType
      Netmode:
        Ref: Netmode
      Bandwidth:
        Ref: Bandwidth
      Tags:
        Ref: Tags
Outputs:
  AllocationId:
    Description: >-
      ID that Aliyun assigns to represent the allocation of the address for use
      with VPC. Returned only for VPC elastic IP addresses.
    Value:
      'Fn::GetAtt':
        - ElasticIp
        - AllocationId
  EipAddress:
    Description: IP address of created EIP.
    Value:
      'Fn::GetAtt':
        - ElasticIp
        - EipAddress
  OrderId:
    Description: Order ID of prepaid EIP instance.
    Value:
      'Fn::GetAtt':
        - ElasticIp
        - OrderId
```


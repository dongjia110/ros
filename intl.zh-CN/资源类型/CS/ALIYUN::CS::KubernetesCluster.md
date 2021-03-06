# ALIYUN::CS::KubernetesCluster

ALIYUN::CS::KubernetesCluster类型用于创建Kubernetes专有版集群。

## 语法

```
{
  "Type": "ALIYUN::CS::KubernetesCluster",
  "Properties": {
    "MasterAutoRenew": Boolean,
    "CloudMonitorFlags": Boolean,
    "ProxyMode": String,
    "MasterInstanceTypes": List,
    "WorkerInstanceChargeType": String,
    "SnatEntry": Boolean,
    "WorkerPeriod": Number,
    "WorkerPeriodUnit": String,
    "WorkerSystemDiskCategory": String,
    "WorkerVSwitchIds": List,
    "MasterInstanceChargeType": String,
    "VpcId": String,
    "Tags": List,
    "MasterAutoRenewPeriod": Number,
    "CpuPolicy": String,
    "WorkerInstanceTypes": List,
    "WorkerDataDisks": List,
    "LoginPassword": String,
    "ContainerCidr": String,
    "NumOfNodes": Number,
    "Name": String,
    "WorkerSystemDiskSize": Number,
    "NodePortRange": String,
    "SshFlags": Boolean,
    "Taint": List,
    "MasterDataDisk": Boolean,
    "MasterSystemDiskCategory": String,
    "WorkerAutoRenewPeriod": Number,
    "WorkerDataDisk": Boolean,
    "WorkerAutoRenew": Boolean,
    "Addons": List,
    "DisableRollback": Boolean,
    "ServiceCidr": String,
    "KubernetesVersion": String,
    "MasterPeriod": Number,
    "SecurityGroupId": String,
    "KeyPair": String,
    "MasterVSwitchIds": List,
    "EndpointPublicAccess": Boolean,
    "MasterSystemDiskSize": Number,
    "MasterDataDisks": List,
    "MasterCount": Number,
    "TimeoutMins": Number,
    "MasterPeriodUnit": String
  }
}
```

## 属性

|属性名称|类型|必须|允许更新|描述|约束|
|----|--|--|----|--|--|
|MasterAutoRenew|Boolean|否|否|Master节点是否自动续费。|当MasterInstanceChargeType为PrePaid时，该参数生效。 取值：

-   true（默认值）
-   false |
|CloudMonitorFlags|Boolean|否|否|是否安装云监控插件。|取值： -   true
-   false（默认值） |
|ProxyMode|String|否|否|kube-proxy代理模式。|取值： -   iptables（默认值）
-   IPVS |
|MasterInstanceTypes|List|是|否|Master节点ECS实例规格。详情请参见[实例规格族](/intl.zh-CN/实例/实例规格族.md)。|必须填写3个ECS实例规格，ECS实例规格可以重复。|
|WorkerInstanceChargeType|String|否|否|Worker节点付费类型。|取值： -   PrePaid：预付费。
-   PostPaid（默认值）：按量付费。 |
|SnatEntry|Boolean|否|否|是否为网络配置SNAT。|取值： -   当已有专有网络可以访问公网环境时，取值：false。
-   当已有专有网络不能访问公网环境时，取值：
    -   true：配置SNAT，此时可以访问公网环境。
    -   false：不配置SNAT，此时不能访问公网环境。 |
|WorkerPeriod|Number|否|否|包年包月时长。|当WorkerInstanceChargeType取值为PrePaid时该参数生效且为必选参数，取值： -   WorkerPeriodUnit=Week时，WorkerPeriod取值：1、2、3、4。
-   当WorkerPeriodUnit=Month时，WorkerPeriod取值： 1、2、3、4、5、6、7、8、9、12、24、36、48、60。 |
|WorkerPeriodUnit|String|否|否|包年包月周期类型。|当WorkerInstanceChargeType取值为PrePaid时，需要指定周期类型。取值： -   Week
-   Month（默认值） |
|WorkerSystemDiskCategory|String|否|否|Worker节点系统盘类型。|取值： -   cloud\_efficiency（默认值）：高效云盘。
-   cloud\_ssd：SSD云盘。 |
|WorkerVSwitchIds|List|是|否|Worker节点的虚拟交换机ID。|最多支持设置5个VSwitchId。|
|MasterInstanceChargeType|String|否|否|Master节点付费类型。|取值： -   PrePaid：预付费。
-   PostPaid（默认值）：按量付费。 |
|VpcId|String|是|否|专有网络ID。|如果不设置，系统会自动创建专有网络，系统创建的专有网络网段为192.168.0.0/16。 VpcId和MasterVSwitchIds只能同时为空或者同时指定。 |
|Tags|List|否|否|集群标签。|最多可以设置20组标签。 详情请参见[Tags属性](#section_sao_4g8_748)。 |
|MasterAutoRenewPeriod|Number|否|否|Master节点自动续费周期。|当选择预付费和自动续费时该参数生效，且为必选值。 -   MasterPeriodUnit=Week时，取值：1、2、3。
-   MasterPeriodUnit=Month时，取值：1、2、3、6、12。

 默认值：1。 |
|CpuPolicy|String|否|否|CPU策略。|当集群版本为1.12.6及以上版本时，取值： -   static
-   none（默认值） |
|WorkerInstanceTypes|List|是|否|Worker节点ECS实例规格。详情请参见[实例规格族](/intl.zh-CN/实例/实例规格族.md)。|无|
|WorkerDataDisks|List|否|否|Worker数据盘类型、大小等配置。|只有在挂载Worker节点数据盘时有效。 详情请参见[WorkerDataDisks属性](#section_cka_mac_ug7)。 |
|LoginPassword|String|否|否|SSH登录密码。|长度为8~30个字符，必须同时包含大写英文字母、小写英文字母、数字和特殊字符其中三项。 该参数和KeyPair二选一。 |
|ContainerCidr|String|否|否|容器网段。|会与专有网络网段冲突。当选择系统自动创建专有网络时，默认使用172.16.0.0/16网段。|
|NumOfNodes|Number|否|否|Worker节点数。|取值范围：0~300。 默认值：3。 |
|Name|String|是|否|集群名称。|长度为1~63个字符。可包含写英文字母、汉字、数字和短划线（-）。|
|WorkerSystemDiskSize|Number|否|否|Worker节点系统盘大小。|默认值：120。 单位：GiB。 |
|NodePortRange|String|否|否|节点服务端口。|取值范围：30,000~65,535中的两个值，以短划线（-）分隔。 默认值：30,000-65,535。 |
|SshFlags|Boolean|否|否|是否开放公网SSH登录。|取值： -   true
-   false |
|Taint|List|否|否|给节点做污点标记，通常用于Pods的调度策略。|若Pods上有相对应的容忍（tolerance）标记，则可以将容忍节点上的污点调度到该节点。|
|MasterDataDisk|Boolean|否|否|Master节点是否挂载数据盘。|取值： -   true
-   false（默认值） |
|MasterSystemDiskCategory|String|否|否|Master节点系统盘类型。|取值： -   cloud\_efficiency：高效云盘。
-   cloud\_ssd：SSD云盘。 |
|WorkerAutoRenewPeriod|Number|否|否|自动续费周期。|当选择预付费和自动续费时该参数生效且为必选参数。 -   当WorkerPeriodUnit=Week时，取值：1、2、3。
-   当WorkerPeriodUnit=Month时，取值：1、2、3、6、12。 |
|WorkerDataDisk|Boolean|否|否|Worker节点是否挂载数据盘。|取值： -   true
-   false（默认值） |
|WorkerAutoRenew|Boolean|否|否|是否开启Worker节点自动续费。|取值： -   true（默认值）
-   false |
|Addons|List|否|否|Kubernetes集群的addon插件的组合。|详情请参见[Addons属性](#section_3nl_fca_4be)。|
|DisableRollback|Boolean|否|否|失败是否回滚。|取值： -   true（默认值）：失败不回滚。
-   false：失败回滚。

 如果选择失败回滚，则会释放创建过程中所生产的资源，不推荐使用。|
|ServiceCidr|String|否|否|服务网段。|不能和专有网络网段以及容器网段冲突。 当选择系统自动创建专有网络时，默认使用172.19.0.0/20网段。 |
|KubernetesVersion|String|否|否|Kubernetes 版本。|取值： -   1.12.6-aliyun.1
-   1.14.8-aliyun.1（默认值） |
|MasterPeriod|Number|否|否|包年包月时长。|当MasterInstanceChargeType取值为PrePaid时该参数生效且为必选参数。 取值：

-   当MasterPeriodUnit=Week时，MasterPeriod取值：1，2，3，4。
-   当MasterPeriodUnit=Month时，MasterPeriod取值： 1，2，3，4，5，6，7，8，9，12，24，36，48，60。

 默认值：1。|
|SecurityGroupId|String|否|否|集群ECS实例所属于的安全组ID。|无|
|KeyPair|String|否|否|密钥对名称。|和LoginPassword二选一。|
|MasterVSwitchIds|List|是|否|Master节点交换机ID。|必须指定3个交换机ID，交换机ID可以重复。为确保集群的高可用性，推荐您选择3个交换机。|
|EndpointPublicAccess|Boolean|否|否|是否开启公网APIServer。|取值： -   true：开放公网APIServer。
-   false（默认值）：仅创建私网APIServer。 |
|MasterSystemDiskSize|Number|否|否|Master节点系统盘大小。|默认值：120。 单位：GiB。 |
|MasterDataDisks|List|否|否|Master数据盘类型、大小等配置。|只有在挂载Master节点数据盘时有效。 详情请参见[MasterDataDisks属性](#section_sqy_mx3_wf0)。 |
|MasterCount|Number|否|否|Master实例个数。|取值： -   3（默认值）
-   5 |
|TimeoutMins|Number|否|否|集群资源栈创建超时时间。|默认值：60。 单位：分钟。 |
|MasterPeriodUnit|String|否|否|Master节点付费周期。|当MasterInstanceChargeType指定为PrePaid时，需要指定周期。 取值：

-   Week
-   Month（默认值） |

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
|Key|String|是|否|标签键|长度为1~64个字符，不能以`aliyun`、`acs:`、`https://`或`http://`开头。|
|Value|String|否|否|标签值|长度为0~63个字符，不能以`aliyun`、`acs:`、`https://`或`http://`开头。|

## MasterDataDisks语法

```
"MasterDataDisks": [
  {
    "Category": String,
    "Size": Number
  }
]
```

## MasterDataDisks属性

|属性名称|类型|必须|允许更新|描述|约束|
|----|--|--|----|--|--|
|Category|String|是|否|Master节点数据盘类型|取值： -   cloud：普通云盘。
-   cloud\_ssd：SSD云盘。
-   cloud\_efficiency：高效云盘。 |
|Size|Number|是|否|Master节点数据盘大小|取值范围：40~32,768。 单位：GiB。 |

## WorkerDataDisks语法

```
"WorkerDataDisks": [
  {
    "Category": String,
    "Size": Number
  }
]
```

## WorkerDataDisks属性

|属性名称|类型|必须|允许更新|描述|约束|
|----|--|--|----|--|--|
|Category|String|是|否|Worker节点数据盘类型|取值： -   cloud：普通云盘。
-   cloud\_ssd：SSD云盘。
-   cloud\_efficiency：高效云盘。 |
|Size|Number|是|否|数据盘大小|取值范围：40~32,768。 单位：GiB。 |

## Addons语法

```
"Addons": [
  {
    "Version": String,
    "Config": String,
    "Name": String
  }
]
```

## Addons属性

|属性名称|类型|必须|允许更新|描述|约束|
|----|--|--|----|--|--|
|Version|String|否|否|Addon插件的版本|取值为空时取最新版本。|
|Config|String|否|否|Addon插件的配置|取值为空时表示无需配置。|
|Name|String|是|否|Addon插件的名称|无|

## 返回值

Fn::GetAtt

-   ClusterId：集群ID。
-   TaskId：任务ID。系统自动分配，用户查询任务状态。
-   WorkerRamRoleName：Worker节点RAM角色名称。

## 示例

JSON示例

```
{
  "ROSTemplateFormatVersion": "2015-09-01",
  "Resources": {
    "KubernetesCluster": {
      "Type": "ALIYUN::CS::KubernetesCluster",
      "Properties": {
        "MasterAutoRenew": {
          "Ref": "MasterAutoRenew"
        },
        "CloudMonitorFlags": {
          "Ref": "CloudMonitorFlags"
        },
        "ProxyMode": {
          "Ref": "ProxyMode"
        },
        "MasterInstanceTypes": {
          "Fn::Split": [
            ",",
            {
              "Ref": "MasterInstanceTypes"
            }
          ]
        },
        "WorkerDataDisk": {
          "Ref": "WorkerDataDisk"
        },
        "SnatEntry": {
          "Ref": "SnatEntry"
        },
        "WorkerPeriod": {
          "Ref": "WorkerPeriod"
        },
        "WorkerPeriodUnit": {
          "Ref": "WorkerPeriodUnit"
        },
        "WorkerSystemDiskCategory": {
          "Ref": "WorkerSystemDiskCategory"
        },
        "WorkerVSwitchIds": {
          "Fn::Split": [
            ",",
            {
              "Ref": "WorkerVSwitchIds"
            }
          ]
        },
        "MasterInstanceChargeType": {
          "Ref": "MasterInstanceChargeType"
        },
        "VpcId": {
          "Ref": "VpcId"
        },
        "Tags": {
          "Ref": "Tags"
        },
        "MasterAutoRenewPeriod": {
          "Ref": "MasterAutoRenewPeriod"
        },
        "CpuPolicy": {
          "Ref": "CpuPolicy"
        },
        "WorkerInstanceTypes": {
          "Fn::Split": [
            ",",
            {
              "Ref": "WorkerInstanceTypes"
            }
          ]
        },
        "WorkerDataDisks": {
          "Ref": "WorkerDataDisks"
        },
        "LoginPassword": {
          "Ref": "LoginPassword"
        },
        "ContainerCidr": {
          "Ref": "ContainerCidr"
        },
        "NumOfNodes": {
          "Ref": "NumOfNodes"
        },
        "Name": {
          "Ref": "Name"
        },
        "NodePortRange": {
          "Ref": "NodePortRange"
        },
        "SshFlags": {
          "Ref": "SshFlags"
        },
        "Taint": {
          "Ref": "Taint"
        },
        "MasterDataDisk": {
          "Ref": "MasterDataDisk"
        },
        "MasterSystemDiskCategory": {
          "Ref": "MasterSystemDiskCategory"
        },
        "WorkerAutoRenewPeriod": {
          "Ref": "WorkerAutoRenewPeriod"
        },
        "WorkerInstanceChargeType": {
          "Ref": "WorkerInstanceChargeType"
        },
        "WorkerAutoRenew": {
          "Ref": "WorkerAutoRenew"
        },
        "Addons": {
          "Ref": "Addons"
        },
        "DisableRollback": {
          "Ref": "DisableRollback"
        },
        "ServiceCidr": {
          "Ref": "ServiceCidr"
        },
        "KubernetesVersion": {
          "Ref": "KubernetesVersion"
        },
        "MasterPeriod": {
          "Ref": "MasterPeriod"
        },
        "SecurityGroupId": {
          "Ref": "SecurityGroupId"
        },
        "KeyPair": {
          "Ref": "KeyPair"
        },
        "MasterCount": {
          "Ref": "MasterCount"
        },
        "MasterVSwitchIds": {
          "Fn::Split": [
            ",",
            {
              "Ref": "MasterVSwitchIds"
            }
          ]
        },
        "EndpointPublicAccess": {
          "Ref": "EndpointPublicAccess"
        },
        "MasterSystemDiskSize": {
          "Ref": "MasterSystemDiskSize"
        },
        "MasterPeriodUnit": {
          "Ref": "MasterPeriodUnit"
        },
        "WorkerSystemDiskSize": {
          "Ref": "WorkerSystemDiskSize"
        },
        "TimeoutMins": {
          "Ref": "TimeoutMins"
        },
        "MasterDataDisks": {
          "Ref": "MasterDataDisks"
        }
      }
    }
  },
  "Parameters": {
    "MasterAutoRenew": {
      "Default": true,
      "Type": "Boolean",
      "Description": "Whether the master node automatically renews. It takes effect when the value of MasterInstanceChargeType is PrePaid. The optional values are:\ntrue: automatic renewal\nfalse: do not renew automatically\nDefault to true.",
      "AllowedValues": [
        "True",
        "true",
        "False",
        "false"
      ]
    },
    "CloudMonitorFlags": {
      "Default": false,
      "Type": "Boolean",
      "Description": "Whether to install the cloud monitoring plugin:\ntrue: indicates installation\nfalse: Do not install\nDefault to false",
      "AllowedValues": [
        "True",
        "true",
        "False",
        "false"
      ]
    },
    "ProxyMode": {
      "Default": "iptables",
      "Type": "String",
      "Description": "kube-proxy proxy mode, supports both iptables and IPVS modes. The default is iptables.",
      "AllowedValues": [
        "iptables",
        "IPVS"
      ]
    },
    "MasterInstanceTypes": {
      "MinLength": 3,
      "Type": "CommaDelimitedList",
      "Description": "Master node ECS specification type code. For more details, see Instance Type Family. Each item correspond to MasterVSwitchIds.\nList size must be 3, Instance Type can be repeated.",
      "MaxLength": 3
    },
    "WorkerDataDisk": {
      "Default": false,
      "Type": "Boolean",
      "Description": "Whether to mount the data disk. The options are as follows:\ntrue: indicates that the worker node mounts data disks.\nfalse: indicates that the worker node does not mount data disks.\nDefault to false.",
      "AllowedValues": [
        "True",
        "true",
        "False",
        "false"
      ]
    },
    "SnatEntry": {
      "Default": true,
      "Type": "Boolean",
      "Description": "Whether to configure SNAT for the network.\nWhen a VPC can access the public network environment, set it to false.\nWhen an existing VPC cannot access the public network environment:\nWhen set to True, SNAT is configured and the public network environment can be accessed at this time.\nIf set to false, it means that SNAT is not configured and the public network environment cannot be accessed at this time.\nDefault to true.",
      "AllowedValues": [
        "True",
        "true",
        "False",
        "false"
      ]
    },
    "WorkerPeriod": {
      "Default": 1,
      "Type": "Number",
      "Description": "The duration of the annual and monthly subscription. It takes effect when the worker_instance_charge_type value is PrePaid and is required. The value range is:\nWhen PeriodUnit = Week, Period values are: {\"1\", \"2\", \"3\", \"4\"}\nWhen PeriodUnit = Month, Period values are: {\"1\", \"2\", \"3\", \"4\", \"5\", \"6\", \"7\", \"8\", \"9\", \"12\", \"24\", \"36\", \"48\", \"60\"}\nDefault to 1.",
      "AllowedValues": [
        1,
        2,
        3,
        4,
        5,
        6,
        7,
        8,
        9,
        12,
        24,
        36,
        48,
        60
      ]
    },
    "WorkerPeriodUnit": {
      "Default": "Month",
      "Type": "String",
      "Description": "When you specify PrePaid, you need to specify the period. The options are:\nWeek: Time is measured in weeks\nMonth: time in months\nDefault to Month.",
      "AllowedValues": [
        "Week",
        "Month"
      ]
    },
    "WorkerSystemDiskCategory": {
      "Default": "cloud_efficiency",
      "Type": "String",
      "Description": "Worker node system disk type. The value range is:\ncloud_efficiency: efficient cloud disk\ncloud_ssd: SSD cloud disk\nDefault to cloud_efficiency.",
      "AllowedValues": [
        "cloud_efficiency",
        "cloud_ssd"
      ]
    },
    "WorkerVSwitchIds": {
      "MinLength": 1,
      "Type": "CommaDelimitedList",
      "Description": "The virtual switch ID of the worker node."
    },
    "MasterInstanceChargeType": {
      "Default": "PostPaid",
      "Type": "String",
      "Description": "Master node payment type. The optional values are:\nPrePaid: prepaid\nPostPaid: Pay as you go\nDefault to PostPaid.",
      "AllowedValues": [
        "PrePaid",
        "PostPaid"
      ]
    },
    "VpcId": {
      "Type": "String",
      "Description": "VPC ID."
    },
    "Tags": {
      "Type": "Json",
      "Description": "Tag the cluster."
    },
    "MasterAutoRenewPeriod": {
      "Default": 1,
      "Type": "Number",
      "Description": "Automatic renewal cycle, which takes effect when prepaid and automatic renewal are selected, and is required:\nWhen PeriodUnit = Week, the values are: {\"1\", \"2\", \"3\"}\nWhen PeriodUnit = Month, the value is {\"1\", \"2\", \"3\", \"6\", \"12\"}\nDefault to 1.",
      "AllowedValues": [
        1,
        2,
        3,
        6,
        12
      ]
    },
    "CpuPolicy": {
      "Default": "none",
      "Type": "String",
      "Description": "CPU policy. The cluster version is 1.12.6 and above supports both static and none strategies. The default is none."
    },
    "WorkerInstanceTypes": {
      "MinLength": 1,
      "Type": "CommaDelimitedList",
      "Description": "Worker node ECS specification type code. For more details, see Instance Specification Family.",
      "MaxLength": 10
    },
    "WorkerDataDisks": {
      "Type": "Json",
      "Description": "A combination of configurations such as worker data disk type and size. This parameter is valid only when the worker node data disk is mounted."
    },
    "LoginPassword": {
      "Type": "String",
      "Description": "SSH login password. Password rules are 8-30 characters and contain three items (upper and lower case letters, numbers, and special symbols). Specify one of KeyPair or LoginPassword."
    },
    "ContainerCidr": {
      "Default": "172.16.0.0/16",
      "Type": "String",
      "Description": "The container network segment cannot conflict with the VPC network segment. When the system is selected to automatically create a VPC, the network segment 172.16.0.0/16 is used by default."
    },
    "NumOfNodes": {
      "Default": 3,
      "Type": "Number",
      "Description": "Number of worker nodes. The range is [0,300].\nDefault to 3.",
      "MaxValue": 300,
      "MinValue": 0
    },
    "Name": {
      "Type": "String",
      "Description": "The name of the cluster. The cluster name can use uppercase and lowercase letters, Chinese characters, numbers, and dashes."
    },
    "NodePortRange": {
      "Default": "30000-65535",
      "Type": "String",
      "Description": "Node service port. The value range is [30000, 65535].\nDefault to 30000-65535."
    },
    "SshFlags": {
      "Type": "Boolean",
      "Description": "Whether to enable public network SSH login:\ntrue: open\nfalse: not open",
      "AllowedValues": [
        "True",
        "true",
        "False",
        "false"
      ]
    },
    "Taint": {
      "Type": "Json",
      "Description": "It is used to mark nodes with taints. It is usually used for the scheduling strategy of Pods. The corresponding concept is: tolerance. If there is a corresponding tolerance mark on the Pods, the stain on the node can be tolerated and scheduled to the node."
    },
    "MasterDataDisk": {
      "Default": false,
      "Type": "Boolean",
      "Description": "Whether the master node mounts data disks can be selected as:\ntrue: mount the data disk\nfalse: no data disk is mounted, default is false",
      "AllowedValues": [
        "True",
        "true",
        "False",
        "false"
      ]
    },
    "MasterSystemDiskCategory": {
      "Default": "cloud_ssd",
      "Type": "String",
      "Description": "Master disk system disk type. The value range is:\ncloud_efficiency: efficient cloud disk\ncloud_ssd: SSD cloud disk\nDefault to cloud_ssd.",
      "AllowedValues": [
        "cloud_efficiency",
        "cloud_ssd"
      ]
    },
    "WorkerAutoRenewPeriod": {
      "Default": 1,
      "Type": "Number",
      "Description": "Automatic renewal cycle, which takes effect when prepaid and automatic renewal are selected, and is required:\nWhen PeriodUnit = Week, the values are: {\"1\", \"2\", \"3\"}\nWhen PeriodUnit = Month, the value is {\"1\", \"2\", \"3\", \"6\", \"12\"}\nDefault to 1.",
      "AllowedValues": [
        1,
        2,
        3,
        6,
        12
      ]
    },
    "WorkerInstanceChargeType": {
      "Default": "PostPaid",
      "Type": "String",
      "Description": "Worker node payment type. The optional values are:\nPrePaid: prepaid\nPostPaid: Pay as you go\nDefault to PostPaid.",
      "AllowedValues": [
        "PrePaid",
        "PostPaid"
      ]
    },
    "WorkerAutoRenew": {
      "Default": true,
      "Type": "Boolean",
      "Description": "Whether to enable automatic renewal of Worker nodes. The optional values are:\ntrue: automatic renewal\nfalse: do not renew automatically\nDefault to true.",
      "AllowedValues": [
        "True",
        "true",
        "False",
        "false"
      ]
    },
    "Addons": {
      "Type": "Json",
      "Description": "A combination of addon plugins for Kubernetes clusters.\nNetwork plug-in: including Flannel and Terway network plug-ins\nLog service: Optional. If the log service is not enabled, the cluster audit function cannot be used.\nIngress: The installation of the Ingress component is enabled by default."
    },
    "DisableRollback": {
      "Default": true,
      "Type": "Boolean",
      "Description": "Whether the failure was rolled back:\ntrue: indicates that it fails to roll back\nfalse: rollback failed\nThe default is true. If rollback fails, resources produced during the creation process will be released. False is not recommended.",
      "AllowedValues": [
        "True",
        "true",
        "False",
        "false"
      ]
    },
    "ServiceCidr": {
      "Default": "172.19.0.0/20",
      "Type": "String",
      "Description": "The service network segment cannot conflict with the VPC network segment and the container network segment. When the system is selected to automatically create a VPC, the network segment 172.19.0.0/20 is used by default."
    },
    "KubernetesVersion": {
      "Default": "1.14.8-aliyun.1",
      "Type": "String",
      "Description": "Kubernetes version. Default to 1.14.8-aliyun.1 .",
      "AllowedValues": [
        "1.12.6-aliyun.1",
        "1.14.8-aliyun.1"
      ]
    },
    "MasterPeriod": {
      "Default": 1,
      "Type": "Number",
      "Description": "The duration of the annual subscription and monthly subscription. It takes effect when the master_instance_charge_type value is PrePaid and is a required value. The value range is:\nWhen PeriodUnit = Week, Period values are: {\"1\", \"2\", \"3\", \"4\"}\nWhen PeriodUnit = Month, Period values are: {\"1\", \"2\", \"3\", \"4\", \"5\", \"6\", \"7\", \"8\", \"9\", \"12\", \"24\", \"36\", \"48\", \"60\"}\nDefault to 1.",
      "AllowedValues": [
        1,
        2,
        3,
        4,
        5,
        6,
        7,
        8,
        9,
        12,
        24,
        36,
        48,
        60
      ]
    },
    "SecurityGroupId": {
      "Type": "String",
      "Description": "Specifies the ID of the security group to which the cluster ECS instance belongs."
    },
    "KeyPair": {
      "Type": "String",
      "Description": "Key pair name. Specify one of KeyPair or LoginPassword."
    },
    "MasterCount": {
      "Default": 3,
      "Type": "Number",
      "Description": "Number of master instances. The value can be 3 or 5. The default value is 3.",
      "AllowedValues": [
        3,
        5
      ]
    },
    "MasterVSwitchIds": {
      "MinLength": 3,
      "Type": "CommaDelimitedList",
      "Description": "Master node switch ID. To ensure high availability of the cluster, it is recommended that you select 3 switches and distribute them in different Availability Zones.\nList size must be 3, VSwitchId can be repeated.",
      "MaxLength": 3
    },
    "EndpointPublicAccess": {
      "Default": false,
      "Type": "Boolean",
      "Description": "Whether to enable the public network API Server:\ntrue: The default is True, which means that the public network API Server is open.\nfalse: If set to false, the API server on the public network will not be created, only the API server on the private network will be created.Default to false.",
      "AllowedValues": [
        "True",
        "true",
        "False",
        "false"
      ]
    },
    "MasterSystemDiskSize": {
      "Default": 120,
      "Type": "Number",
      "Description": "Master disk system disk size in GiB.\nDefault to 120.",
      "MinValue": 1
    },
    "MasterPeriodUnit": {
      "Default": "Month",
      "Type": "String",
      "Description": "When you specify PrePaid, you need to specify the period. The options are:\nWeek: Time is measured in weeks\nMonth: time in months\nDefault to Month",
      "AllowedValues": [
        "Week",
        "Month"
      ]
    },
    "WorkerSystemDiskSize": {
      "Default": 120,
      "Type": "Number",
      "Description": "Worker disk system disk size, the unit is GiB.\nDefault to 120.",
      "MinValue": 1
    },
    "TimeoutMins": {
      "Default": 60,
      "Type": "Number",
      "Description": "Cluster resource stack creation timeout, in minutes. The default value is 60."
    },
    "MasterDataDisks": {
      "Type": "Json",
      "Description": "Master data disk type, size and other configuration combinations. This parameter is valid only when the master node data disk is mounted."
    }
  },
  "Outputs": {
    "ClusterId": {
      "Description": "Cluster instance ID.",
      "Value": {
        "Fn::GetAtt": [
          "KubernetesCluster",
          "ClusterId"
        ]
      }
    },
    "TaskId": {
      "Description": "Task ID. Automatically assigned by the system, the user queries the task status.",
      "Value": {
        "Fn::GetAtt": [
          "KubernetesCluster",
          "TaskId"
        ]
      }
    }
  }
}
```

YML示例

```
ROSTemplateFormatVersion: '2015-09-01'
Resources:
  KubernetesCluster:
    Type: 'ALIYUN::CS::KubernetesCluster'
    Properties:
      MasterAutoRenew:
        Ref: MasterAutoRenew
      CloudMonitorFlags:
        Ref: CloudMonitorFlags
      ProxyMode:
        Ref: ProxyMode
      MasterInstanceTypes:
        'Fn::Split':
          - ','
          - Ref: MasterInstanceTypes
      WorkerDataDisk:
        Ref: WorkerDataDisk
      SnatEntry:
        Ref: SnatEntry
      WorkerPeriod:
        Ref: WorkerPeriod
      WorkerPeriodUnit:
        Ref: WorkerPeriodUnit
      WorkerSystemDiskCategory:
        Ref: WorkerSystemDiskCategory
      WorkerVSwitchIds:
        'Fn::Split':
          - ','
          - Ref: WorkerVSwitchIds
      MasterInstanceChargeType:
        Ref: MasterInstanceChargeType
      VpcId:
        Ref: VpcId
      Tags:
        Ref: Tags
      MasterAutoRenewPeriod:
        Ref: MasterAutoRenewPeriod
      CpuPolicy:
        Ref: CpuPolicy
      WorkerInstanceTypes:
        'Fn::Split':
          - ','
          - Ref: WorkerInstanceTypes
      WorkerDataDisks:
        Ref: WorkerDataDisks
      LoginPassword:
        Ref: LoginPassword
      ContainerCidr:
        Ref: ContainerCidr
      NumOfNodes:
        Ref: NumOfNodes
      Name:
        Ref: Name
      NodePortRange:
        Ref: NodePortRange
      SshFlags:
        Ref: SshFlags
      Taint:
        Ref: Taint
      MasterDataDisk:
        Ref: MasterDataDisk
      MasterSystemDiskCategory:
        Ref: MasterSystemDiskCategory
      WorkerAutoRenewPeriod:
        Ref: WorkerAutoRenewPeriod
      WorkerInstanceChargeType:
        Ref: WorkerInstanceChargeType
      WorkerAutoRenew:
        Ref: WorkerAutoRenew
      Addons:
        Ref: Addons
      DisableRollback:
        Ref: DisableRollback
      ServiceCidr:
        Ref: ServiceCidr
      KubernetesVersion:
        Ref: KubernetesVersion
      MasterPeriod:
        Ref: MasterPeriod
      SecurityGroupId:
        Ref: SecurityGroupId
      KeyPair:
        Ref: KeyPair
      MasterCount:
        Ref: MasterCount
      MasterVSwitchIds:
        'Fn::Split':
          - ','
          - Ref: MasterVSwitchIds
      EndpointPublicAccess:
        Ref: EndpointPublicAccess
      MasterSystemDiskSize:
        Ref: MasterSystemDiskSize
      MasterPeriodUnit:
        Ref: MasterPeriodUnit
      WorkerSystemDiskSize:
        Ref: WorkerSystemDiskSize
      TimeoutMins:
        Ref: TimeoutMins
      MasterDataDisks:
        Ref: MasterDataDisks
Parameters:
  MasterAutoRenew:
    Default: true
    Type: Boolean
    Description: >-
      Whether the master node automatically renews. It takes effect when the
      value of MasterInstanceChargeType is PrePaid. The optional values are:

      true: automatic renewal

      false: do not renew automatically

      Default to true.
    AllowedValues:
      - 'True'
      - 'true'
      - 'False'
      - 'false'
  CloudMonitorFlags:
    Default: false
    Type: Boolean
    Description: |-
      Whether to install the cloud monitoring plugin:
      true: indicates installation
      false: Do not install
      Default to false
    AllowedValues:
      - 'True'
      - 'true'
      - 'False'
      - 'false'
  ProxyMode:
    Default: iptables
    Type: String
    Description: >-
      kube-proxy proxy mode, supports both iptables and IPVS modes. The default
      is iptables.
    AllowedValues:
      - iptables
      - IPVS
  MasterInstanceTypes:
    MinLength: 3
    Type: CommaDelimitedList
    Description: >-
      Master node ECS specification type code. For more details, see Instance
      Type Family. Each item correspond to MasterVSwitchIds.

      List size must be 3, Instance Type can be repeated.
    MaxLength: 3
  WorkerDataDisk:
    Default: false
    Type: Boolean
    Description: |-
      Whether to mount the data disk. The options are as follows:
      true: indicates that the worker node mounts data disks.
      false: indicates that the worker node does not mount data disks.
      Default to false.
    AllowedValues:
      - 'True'
      - 'true'
      - 'False'
      - 'false'
  SnatEntry:
    Default: true
    Type: Boolean
    Description: >-
      Whether to configure SNAT for the network.

      When a VPC can access the public network environment, set it to false.

      When an existing VPC cannot access the public network environment:

      When set to True, SNAT is configured and the public network environment
      can be accessed at this time.

      If set to false, it means that SNAT is not configured and the public
      network environment cannot be accessed at this time.

      Default to true.
    AllowedValues:
      - 'True'
      - 'true'
      - 'False'
      - 'false'
  WorkerPeriod:
    Default: 1
    Type: Number
    Description: >-
      The duration of the annual and monthly subscription. It takes effect when
      the worker_instance_charge_type value is PrePaid and is required. The
      value range is:

      When PeriodUnit = Week, Period values are: {"1", "2", "3", "4"}

      When PeriodUnit = Month, Period values are: {"1", "2", "3", "4", "5", "6",
      "7", "8", "9", "12", "24", "36", "48", "60"}

      Default to 1.
    AllowedValues:
      - 1
      - 2
      - 3
      - 4
      - 5
      - 6
      - 7
      - 8
      - 9
      - 12
      - 24
      - 36
      - 48
      - 60
  WorkerPeriodUnit:
    Default: Month
    Type: String
    Description: |-
      When you specify PrePaid, you need to specify the period. The options are:
      Week: Time is measured in weeks
      Month: time in months
      Default to Month.
    AllowedValues:
      - Week
      - Month
  WorkerSystemDiskCategory:
    Default: cloud_efficiency
    Type: String
    Description: |-
      Worker node system disk type. The value range is:
      cloud_efficiency: efficient cloud disk
      cloud_ssd: SSD cloud disk
      Default to cloud_efficiency.
    AllowedValues:
      - cloud_efficiency
      - cloud_ssd
  WorkerVSwitchIds:
    MinLength: 1
    Type: CommaDelimitedList
    Description: The virtual switch ID of the worker node.
  MasterInstanceChargeType:
    Default: PostPaid
    Type: String
    Description: |-
      Master node payment type. The optional values are:
      PrePaid: prepaid
      PostPaid: Pay as you go
      Default to PostPaid.
    AllowedValues:
      - PrePaid
      - PostPaid
  VpcId:
    Type: String
    Description: VPC ID.
  Tags:
    Type: Json
    Description: Tag the cluster.
  MasterAutoRenewPeriod:
    Default: 1
    Type: Number
    Description: >-
      Automatic renewal cycle, which takes effect when prepaid and automatic
      renewal are selected, and is required:

      When PeriodUnit = Week, the values are: {"1", "2", "3"}

      When PeriodUnit = Month, the value is {"1", "2", "3", "6", "12"}

      Default to 1.
    AllowedValues:
      - 1
      - 2
      - 3
      - 6
      - 12
  CpuPolicy:
    Default: none
    Type: String
    Description: >-
      CPU policy. The cluster version is 1.12.6 and above supports both static
      and none strategies. The default is none.
  WorkerInstanceTypes:
    MinLength: 1
    Type: CommaDelimitedList
    Description: >-
      Worker node ECS specification type code. For more details, see Instance
      Specification Family.
    MaxLength: 10
  WorkerDataDisks:
    Type: Json
    Description: >-
      A combination of configurations such as worker data disk type and size.
      This parameter is valid only when the worker node data disk is mounted.
  LoginPassword:
    Type: String
    Description: >-
      SSH login password. Password rules are 8-30 characters and contain three
      items (upper and lower case letters, numbers, and special symbols).
      Specify one of KeyPair or LoginPassword.
  ContainerCidr:
    Default: 172.16.0.0/16
    Type: String
    Description: >-
      The container network segment cannot conflict with the VPC network
      segment. When the system is selected to automatically create a VPC, the
      network segment 172.16.0.0/16 is used by default.
  NumOfNodes:
    Default: 3
    Type: Number
    Description: |-
      Number of worker nodes. The range is [0,300].
      Default to 3.
    MaxValue: 300
    MinValue: 0
  Name:
    Type: String
    Description: >-
      The name of the cluster. The cluster name can use uppercase and lowercase
      letters, Chinese characters, numbers, and dashes.
  NodePortRange:
    Default: 30000-65535
    Type: String
    Description: |-
      Node service port. The value range is [30000, 65535].
      Default to 30000-65535.
  SshFlags:
    Type: Boolean
    Description: |-
      Whether to enable public network SSH login:
      true: open
      false: not open
    AllowedValues:
      - 'True'
      - 'true'
      - 'False'
      - 'false'
  Taint:
    Type: Json
    Description: >-
      It is used to mark nodes with taints. It is usually used for the
      scheduling strategy of Pods. The corresponding concept is: tolerance. If
      there is a corresponding tolerance mark on the Pods, the stain on the node
      can be tolerated and scheduled to the node.
  MasterDataDisk:
    Default: false
    Type: Boolean
    Description: |-
      Whether the master node mounts data disks can be selected as:
      true: mount the data disk
      false: no data disk is mounted, default is false
    AllowedValues:
      - 'True'
      - 'true'
      - 'False'
      - 'false'
  MasterSystemDiskCategory:
    Default: cloud_ssd
    Type: String
    Description: |-
      Master disk system disk type. The value range is:
      cloud_efficiency: efficient cloud disk
      cloud_ssd: SSD cloud disk
      Default to cloud_ssd.
    AllowedValues:
      - cloud_efficiency
      - cloud_ssd
  WorkerAutoRenewPeriod:
    Default: 1
    Type: Number
    Description: >-
      Automatic renewal cycle, which takes effect when prepaid and automatic
      renewal are selected, and is required:

      When PeriodUnit = Week, the values are: {"1", "2", "3"}

      When PeriodUnit = Month, the value is {"1", "2", "3", "6", "12"}

      Default to 1.
    AllowedValues:
      - 1
      - 2
      - 3
      - 6
      - 12
  WorkerInstanceChargeType:
    Default: PostPaid
    Type: String
    Description: |-
      Worker node payment type. The optional values are:
      PrePaid: prepaid
      PostPaid: Pay as you go
      Default to PostPaid.
    AllowedValues:
      - PrePaid
      - PostPaid
  WorkerAutoRenew:
    Default: true
    Type: Boolean
    Description: >-
      Whether to enable automatic renewal of Worker nodes. The optional values
      are:

      true: automatic renewal

      false: do not renew automatically

      Default to true.
    AllowedValues:
      - 'True'
      - 'true'
      - 'False'
      - 'false'
  Addons:
    Type: Json
    Description: >-
      A combination of addon plugins for Kubernetes clusters.

      Network plug-in: including Flannel and Terway network plug-ins

      Log service: Optional. If the log service is not enabled, the cluster
      audit function cannot be used.

      Ingress: The installation of the Ingress component is enabled by default.
  DisableRollback:
    Default: true
    Type: Boolean
    Description: >-
      Whether the failure was rolled back:

      true: indicates that it fails to roll back

      false: rollback failed

      The default is true. If rollback fails, resources produced during the
      creation process will be released. False is not recommended.
    AllowedValues:
      - 'True'
      - 'true'
      - 'False'
      - 'false'
  ServiceCidr:
    Default: 172.19.0.0/20
    Type: String
    Description: >-
      The service network segment cannot conflict with the VPC network segment
      and the container network segment. When the system is selected to
      automatically create a VPC, the network segment 172.19.0.0/20 is used by
      default.
  KubernetesVersion:
    Default: 1.14.8-aliyun.1
    Type: String
    Description: Kubernetes version. Default to 1.14.8-aliyun.1 .
    AllowedValues:
      - 1.12.6-aliyun.1
      - 1.14.8-aliyun.1
  MasterPeriod:
    Default: 1
    Type: Number
    Description: >-
      The duration of the annual subscription and monthly subscription. It takes
      effect when the master_instance_charge_type value is PrePaid and is a
      required value. The value range is:

      When PeriodUnit = Week, Period values are: {"1", "2", "3", "4"}

      When PeriodUnit = Month, Period values are: {"1", "2", "3", "4", "5", "6",
      "7", "8", "9", "12", "24", "36", "48", "60"}

      Default to 1.
    AllowedValues:
      - 1
      - 2
      - 3
      - 4
      - 5
      - 6
      - 7
      - 8
      - 9
      - 12
      - 24
      - 36
      - 48
      - 60
  SecurityGroupId:
    Type: String
    Description: >-
      Specifies the ID of the security group to which the cluster ECS instance
      belongs.
  KeyPair:
    Type: String
    Description: Key pair name. Specify one of KeyPair or LoginPassword.
  MasterCount:
    Default: 3
    Type: Number
    Description: >-
      Number of master instances. The value can be 3 or 5. The default value is
      3.
    AllowedValues:
      - 3
      - 5
  MasterVSwitchIds:
    MinLength: 3
    Type: CommaDelimitedList
    Description: >-
      Master node switch ID. To ensure high availability of the cluster, it is
      recommended that you select 3 switches and distribute them in different
      Availability Zones.

      List size must be 3, VSwitchId can be repeated.
    MaxLength: 3
  EndpointPublicAccess:
    Default: false
    Type: Boolean
    Description: >-
      Whether to enable the public network API Server:

      true: The default is True, which means that the public network API Server
      is open.

      false: If set to false, the API server on the public network will not be
      created, only the API server on the private network will be
      created.Default to false.
    AllowedValues:
      - 'True'
      - 'true'
      - 'False'
      - 'false'
  MasterSystemDiskSize:
    Default: 120
    Type: Number
    Description: |-
      Master disk system disk size in GiB.
      Default to 120.
    MinValue: 1
  MasterPeriodUnit:
    Default: Month
    Type: String
    Description: |-
      When you specify PrePaid, you need to specify the period. The options are:
      Week: Time is measured in weeks
      Month: time in months
      Default to Month
    AllowedValues:
      - Week
      - Month
  WorkerSystemDiskSize:
    Default: 120
    Type: Number
    Description: |-
      Worker disk system disk size, the unit is GiB.
      Default to 120.
    MinValue: 1
  TimeoutMins:
    Default: 60
    Type: Number
    Description: >-
      Cluster resource stack creation timeout, in minutes. The default value is
      60.
  MasterDataDisks:
    Type: Json
    Description: >-
      Master data disk type, size and other configuration combinations. This
      parameter is valid only when the master node data disk is mounted.
Outputs:
  ClusterId:
    Description: Cluster instance ID.
    Value:
      'Fn::GetAtt':
        - KubernetesCluster
        - ClusterId
  TaskId:
    Description: >-
      Task ID. Automatically assigned by the system, the user queries the task
      status.
    Value:
      'Fn::GetAtt':
        - KubernetesCluster
        - TaskId
```


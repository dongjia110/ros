# ALIYUN::CS::KubernetesCluster

ALIYUN::CS::KubernetesCluster is used to create a cluster of the Container Service for Kubernetes \(ACK\) Proprietary Edition.

## Syntax

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

## Properties

|Property|Type|Required|Editable|Description|Constraint|
|--------|----|--------|--------|-----------|----------|
|MasterAutoRenew|Boolean|No|No|Specifies whether to enable auto-renewal for master nodes.|This parameter takes effect only when the MasterInstanceChargeType parameter is set to PrePaid. Default value: true. Valid values:

-   true
-   false |
|CloudMonitorFlags|Boolean|No|No|Specifies whether to install the Cloud Monitor agent.|Default value: false. Valid values: -   true
-   false |
|ProxyMode|String|No|No|The kube-proxy mode.|Default value: iptables. Valid values: -   iptables
-   IPVS |
|MasterInstanceTypes|List|Yes|No|The instance types of ECS instances that are set as master nodes. For more information, see [Instance families](/intl.en-US/Instance/Instance families.md).|You must specify three ECS instances types. The types can be the same.|
|WorkerInstanceChargeType|String|No|No|The billing method of worker nodes.|Default value: PostPaid. Valid values: -   PrePaid: subscription
-   PostPaid: pay-as-you-go |
|SnatEntry|Boolean|No|No|Specifies whether to configure the Source Network Address Translation \(SNAT\) rules for the network.|-   Set the value to false when the VPC that you select for the cluster can access the Internet.
-   Valid values when the VPC that you select for the cluster cannot access the Internet:
    -   true: ACK creates SNAT rules to enable Internet access for the VPC.
    -   false: ACK does not create SNAT entries. In this case, the VPC cannot access the Internet. |
|WorkerPeriod|Number|No|No|The subscription period.|This parameter is available and required only when the InstanceChargeType parameter is set to PrePaid. -   Valid values when the WorkerPeriodUnit parameter is set to Week: 1, 2, 3, and 4.
-   Valid values when the WorkerPeriodUnit parameter is set to Month: 1, 2, 3, 4, 5, 6, 7, 8, 9, 12, 24, 36, 48, and 60. |
|WorkerPeriodUnit|String|No|No|The unit of the subscription period.|This parameter is required only when the WorkerInstanceChargeType parameter is set to PrePaid. Default value: Month. Valid values: -   Week
-   Month |
|WorkerSystemDiskCategory|String|No|No|The system disk type of worker nodes.|Default value: cloud\_efficiency. Valid values: -   cloud\_efficiency: ultra disk
-   cloud\_ssd: standard SSD |
|WorkerVSwitchIds|List|Yes|No|The VSwitch IDs of worker nodes.|You can specify a maximum of five VSwitch IDs.|
|MasterInstanceChargeType|String|No|No|The billing method of master nodes.|Default value: PostPaid. Valid values: -   PrePaid: subscription
-   PostPaid: pay-as-you-go |
|VpcId|String|Yes|No|The ID of the VPC.|If this parameter is not specified, the system automatically creates a VPC whose CIDR block is 192.168.0.0/16. You must specify both the VpcId and MasterVSwitchIds parameters or leave both parameters empty. |
|Tags|List|No|No|The tags of the cluster.|A maximum of 20 tags can be specified. For more information, see [Tags properties](#section_sao_4g8_748). |
|MasterAutoRenewPeriod|Number|No|No|The auto-renewal period for master nodes.|This parameter is available and required only when the MasterInstanceChargeType parameter is set to PrePaid and the MasterAutoRenew parameter is set to true. -   Valid values when the MasterPeriodUnit parameter is set to Week: 1, 2, and 3.
-   Valid values when the MasterPeriodUnit parameter is set to Month: 1, 2, 3, 6, and 12.

 Default value: 1. |
|CpuPolicy|String|No|No|The CPU policy.|Default value: none. Valid values for Kubernetes v1.12.6 or later: -   static
-   none |
|WorkerInstanceTypes|List|Yes|No|The instance types of ECS instances that are set as worker nodes. For more information, see [Instance families](/intl.en-US/Instance/Instance families.md).|None|
|WorkerDataDisks|List|No|No|The data disk configurations of worker nodes, such as the disk type and disk size.|This parameter takes effect only when data disks are attached to the worker nodes. For more information, see [WorkerDataDisks properties](#section_cka_mac_ug7). |
|LoginPassword|String|No|No|The password that is used to connect to nodes over SSH.|The password must be 8 to 30 characters in length. It must contain at least three of the following character types: uppercase letters, lowercase letters, digits, and special characters. You must specify one of the LoginPassword and KeyPair parameters. |
|ContainerCidr|String|No|No|The container CIDR block.|The CIDR block may overlap with that of the VPC. If the VPC is automatically created by the system, the container CIDR block is set to 172.16.0.0/16 by default.|
|NumOfNodes|Number|No|No|The number of worker nodes.|Valid values: 0 to 300. Default value: 3. |
|Name|String|Yes|No|The name of the cluster.|The name must be 1 to 63 characters in length. It can contain letters, digits, and hyphens \(-\).|
|WorkerSystemDiskSize|Number|No|No|The system disk size of worker nodes.|Default value: 120. Unit: GiB. |
|NodePortRange|String|No|No|The service port range of nodes.|Valid values: two values within the range of 30,000 to 65,535. Separate the two values with a hyphen \(-\). Default value: 30,000-65,535. |
|SshFlags|Boolean|No|No|Specifies whether to allow Internet access over SSH.|Valid values: -   true
-   false |
|Taint|List|No|No|The taints that are added to nodes to ensure appropriate scheduling of pods.|If a pod has a toleration that matches the taint on a node, the taint can be tolerated and scheduled to the node.|
|MasterDataDisk|Boolean|No|No|Specifies whether to attach data disks to master nodes.|Default value: false. Valid values: -   true
-   false |
|MasterSystemDiskCategory|String|No|No|The system disk type of master nodes.|Valid values: -   cloud\_efficiency: ultra disk
-   cloud\_ssd: standard SSD |
|WorkerAutoRenewPeriod|Number|No|No|The auto-renewal period of worker nodes.|This parameter is available and required when the WorkerInstanceChargeType parameter is set to PrePaid and the WorkerAutoRenew parameter is set to true. -   Valid values when the WorkerPeriodUnit parameter is set to Week: 1, 2, and 3.
-   Valid values when the WorkerPeriodUnit parameter is set to Month: 1, 2, 3, 6, and 12. |
|WorkerDataDisk|Boolean|No|No|Specifies whether to attach data disks to worker nodes.|Default value: false. Valid values: -   true
-   false |
|WorkerAutoRenew|Boolean|No|No|Specifies whether to enable auto-renewal for worker nodes.|Default value: true. Valid values: -   true
-   false |
|Addons|List|No|No|The add-ons to be installed for the cluster.|For more information, see [Addons properties](#section_3nl_fca_4be).|
|DisableRollback|Boolean|No|No|Specifies whether to roll back resources if the operation fails.|Default value: true. Valid values: -   true: disables rollback upon failure.
-   false: enables rollback upon failure.

 If you choose to enable rollback when the operation fails, resources that are created during the operation are released. We recommend that you set this parameter to true.|
|ServiceCidr|String|No|No|The CIDR block of the service.|The CIDR block cannot overlap with that of the VPC or container. If the VPC is automatically created by the system, the service CIDR block is set to 172.19.0.0/20 by default. |
|KubernetesVersion|String|No|No|The version of Kubernetes.|Default value: 1.14.8-aliyun.1. Valid values: -   1.12.6-aliyun.1
-   1.14.8-aliyun.1 |
|MasterPeriod|Number|No|No|The subscription period.|This parameter is available and required only when the MasterInstanceChargeType parameter is set to PrePaid. -   Valid values when the MasterPeriodUnit parameter is set to Week: 1, 2, 3, and 4.
-   Valid values when the MasterPeriodUnit parameter is set to Month: 1, 2, 3, 4, 5, 6, 7, 8, 9, 12, 24, 36, 48, and 60.

 Default value: 1.|
|SecurityGroupId|String|No|No|The ID of the security group to which the ECS instances in the cluster belong.|None|
|KeyPair|String|No|No|The name of the key pair.|You must specify one of the LoginPassword and KeyPair parameters.|
|MasterVSwitchIds|List|Yes|No|The VSwitch IDs of master nodes.|You must specify three VSwitch IDs. The specified IDs can be the same. We recommend that you specify three different VSwitches to ensure high availability.|
|EndpointPublicAccess|Boolean|No|No|Specifies whether to enable Internet access to the API server.|Default value: false. Valid values: -   true: enables access to the API server over the Internet.
-   false: disables access to the API server over the Internet. The API server allows only access over the internal network. |
|MasterSystemDiskSize|Number|No|No|The system disk size of master nodes.|Default value: 120. Unit: GiB. |
|MasterDataDisks|List|No|No|The data disk configurations of master nodes, such as the disk type and disk size.|This parameter takes effect only when data disks are attached to the master nodes. For more information, see [MasterDataDisks properties](#section_sqy_mx3_wf0). |
|MasterCount|Number|No|No|The number of master nodes.|Default value: 3. Valid values: -   3
-   5 |
|TimeoutMins|Number|No|No|The timeout period for the system to create a cluster stack.|Default value: 60. Unit: minutes. |
|MasterPeriodUnit|String|No|No|The unit of the billing cycle for master nodes.|This parameter is required when the MasterInstanceChargeType parameter is set to PrePaid. Default value: Month. Valid values:

-   Week
-   Month |

## Tags syntax

```
"Tags": [
  {
    "Key": String,
    "Value": String
  }
]
```

## Tags properties

|Property|Type|Required|Editable|Description|Constraint|
|--------|----|--------|--------|-----------|----------|
|Key|String|Yes|No|The tag key.|The tag key must be 1 to 64 characters in length and cannot start with `aliyun`, `acs:`, `http://`, or `https://`.|
|Value|String|No|No|The tag value.|The tag value must be 0 to 63 characters in length and cannot start with `aliyun`, `acs:`, `http://`, or `https://`.|

## MasterDataDisks syntax

```
"MasterDataDisks": [
  {
    "Category": String,
    "Size": Number
  }
]
```

## MasterDataDisks properties

|Property|Type|Required|Editable|Description|Constraint|
|--------|----|--------|--------|-----------|----------|
|Category|String|Yes|No|The data disk type of master nodes.|Valid values: -   cloud: basic disk
-   cloud\_ssd: standard SSD
-   cloud\_efficiency: ultra disk |
|Size|Number|Yes|No|The data disk size of master nodes.|Valid values: 40 to 32768. Unit: GiB. |

## WorkerDataDisks syntax

```
"WorkerDataDisks": [
  {
    "Category": String,
    "Size": Number
  }
]
```

## WorkerDataDisks properties

|Property|Type|Required|Editable|Description|Constraint|
|--------|----|--------|--------|-----------|----------|
|Category|String|Yes|No|The data disk type of worker nodes.|Valid values: -   cloud: basic disk
-   cloud\_ssd: standard SSD
-   cloud\_efficiency: ultra disk |
|Size|Number|Yes|No|The size of the data disk.|Valid values: 40 to 32768. Unit: GiB. |

## Addons syntax

```
"Addons": [
  {
    "Version": String,
    "Config": String,
    "Name": String
  }
]
```

## Addons properties

|Property|Type|Required|Editable|Description|Constraint|
|--------|----|--------|--------|-----------|----------|
|Version|String|No|No|The version of the add-on.|If you do not specify this parameter, the latest version is used.|
|Config|String|No|No|The configuration of the add-on.|If this parameter is empty, no configuration is required.|
|Name|String|Yes|No|The name of the add-on.|None|

## Response parameters

Fn::GetAtt

-   ClusterId: the ID of the cluster.
-   TaskId: the ID of the task. The task ID is automatically assigned by the system and can be used to query the task status.
-   WorkerRamRoleName: the RAM role name of the worker node.

## Examples

JSON format

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

YML format

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


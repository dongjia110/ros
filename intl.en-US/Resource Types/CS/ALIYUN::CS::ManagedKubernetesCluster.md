# ALIYUN::CS::ManagedKubernetesCluster

ALIYUN::CS::ManagedKubernetesCluster is used to create a managed Container Service for Kubernetes \(ACK\) cluster.

## Syntax

```
{
  "Type": "ALIYUN::CS::ManagedKubernetesCluster",
  "Properties": {
    "CloudMonitorFlags": Boolean,
    "ProxyMode": String,
    "WorkerDataDisk": Boolean,
    "SnatEntry": Boolean,
    "VSwitchIds": List,
    "WorkerPeriod": Number,
    "WorkerPeriodUnit": String,
    "WorkerSystemDiskCategory": String,
    "VpcId": String,
    "Tags": List,
    "WorkerSystemDiskSize": Number,
    "WorkerInstanceTypes": List,
    "WorkerDataDisks": List,
    "LoginPassword": String,
    "ContainerCidr": String,
    "NumOfNodes": Number,
    "Name": String,
    "Taint": List,
    "KeyPair": String,
    "WorkerAutoRenewPeriod": Number,
    "WorkerInstanceChargeType": String,
    "WorkerAutoRenew": Boolean,
    "Addons": List,
    "DisableRollback": Boolean,
    "ServiceCidr": String,
    "KubernetesVersion": String,
    "SecurityGroupId": String,
    "EndpointPublicAccess": Boolean,
    "TimeoutMins": Number
  }
}
```

## Properties

|Property|Type|Required|Editable|Description|Constraint|
|--------|----|--------|--------|-----------|----------|
|CloudMonitorFlags|Boolean|No|No|Specifies whether to install the Cloud Monitor agent.|Default value: false. Valid values:-   true
-   false |
|ProxyMode|String|No|No|The kube-proxy mode.|Default value: iptables. Valid values:-   iptables
-   IPVS |
|WorkerInstanceChargeType|String|No|No|The billing method of worker nodes.|Default value: PostPaid. Valid values:-   PrePaid: subscription
-   PostPaid: pay-as-you-go |
|SnatEntry|Boolean|No|No|Specifies whether to configure Source Network Address Translation \(SNAT\) rules for the network.|-   Set the value to false when the VPC that you select for the cluster can access the Internet.
-   Valid values when the VPC that you select for the cluster cannot access the Internet:
    -   true: ACK creates SNAT rules to enable Internet access for the VPC.
    -   false: ACK does not create SNAT rules. In this case, the VPC cannot access the Internet. |
|WorkerPeriod|Number|No|No|The subscription period.|This parameter is available and required when the WorkerInstanceChargeType parameter is set to PrePaid.-   Valid values when the WorkerPeriodUnit parameter is set to Week: 1, 2, 3, and 4.
-   Valid values when the WorkerPeriodUnit parameter is set to Month: 1, 2, 3, 4, 5, 6, 7, 8, 9, 12, 24, 36, 48, and 60. |
|WorkerPeriodUnit|String|No|No|The unit of the subscription period.|This parameter is required when the WorkerInstanceChargeType parameter is set to PrePaid. Default value: Month. Valid values:-   Week
-   Month |
|WorkerSystemDiskCategory|String|No|No|The system disk type of worker nodes.|Default value: cloud\_efficiency. Valid values:-   cloud\_efficiency: ultra disk
-   cloud\_ssd: standard SSD |
|VpcId|String|Yes|No|The ID of the VPC.|If this parameter is not specified, the system automatically creates a VPC whose CIDR block is 192.168.0.0/16.You must specify both the VpcId and MasterVSwitchIds parameters or leave both parameters empty. |
|Tags|List|No|No|The tags of the cluster.|A maximum of 20 tags can be specified.For more information, see [Tags properties](#section_sao_4g8_748). |
|WorkerInstanceTypes|List|Yes|No|The instance types of ECS instances that are set as worker nodes. For more information, see [Instance families](/intl.en-US/Instance/Instance families.md).|None|
|WorkerDataDisks|List|No|No|The data disk configurations of worker nodes, such as the disk type and disk size.|This parameter takes effect only when data disks are attached to the worker nodes.For more information, see [WorkerDataDisks properties](#section_cka_mac_ug7). |
|LoginPassword|String|No|No|The password that is used to connect to nodes over SSH.|The password must be 8 to 30 characters in length. It must contain at least three of the following character types: uppercase letters, lowercase letters, digits, and special characters.You must specify one of the LoginPassword and KeyPair parameters. |
|ContainerCidr|String|No|No|The container CIDR block.|The CIDR block may overlap with that of the VPC. If the VPC is automatically created by the system, the container CIDR block is set to 172.16.0.0/16 by default.|
|NumOfNodes|Number|No|No|The number of worker nodes.|Valid values: 0 to 300.Default value: 3. |
|Name|String|Yes|No|The name of the cluster.|The name must be 1 to 63 characters in length and can contain letters, digits, and hyphens \(-\).|
|WorkerSystemDiskSize|Number|No|No|The system disk size of a worker node.|Default value: 120.Unit: GB. |
|Taint|List|No|No|The taints that are added to nodes to ensure appropriate scheduling of pods.|If a pod has a toleration that matches the taint on a node, the taint can be tolerated and scheduled to the node.|
|WorkerAutoRenewPeriod|Number|No|No|The auto-renewal period for worker nodes. This parameter is available and required only when WorkerInstanceChargeType is set to PrePaid and WorkerAutoRenew is set to true.|-   Valid values when the WorkerPeriodUnit parameter is set to Week: 1, 2, and 3.
-   Valid values when the WorkerPeriodUnit parameter is set to Month: 1, 2, 3, 6, and 12. |
|WorkerDataDisk|Boolean|No|No|Specifies whether to attach data disks to the worker nodes.|Default value: false. Valid values:-   true
-   false |
|WorkerAutoRenew|Boolean|No|No|Specifies whether to enable auto-renewal for worker nodes.|Default value: false. Valid values:-   true
-   false |
|Addons|List|No|No|The add-ons to be installed for the cluster.|For more information, see [Addons properties](#section_3nl_fca_4be).|
|DisableRollback|Boolean|No|No|Specifies whether to roll back resources if the operation fails.|Default value: true. Valid values:-   true: disables rollback upon failure.
-   false: enables rollback upon failure.

If you choose to enable rollback when the operation fails, resources that are created during the operation are released. We recommend that you set this parameter to true.|
|ServiceCidr|String|No|No|The CIDR block of the service.|The CIDR block cannot overlap with that of the VPC network or container. If the VPC is automatically created by the system, the service CIDR block is set to 172.19.0.0/20 by default.|
|KubernetesVersion|String|No|No|The version of Kubernetes.|Default value: 1.16.9-aliyun.1. Valid values:-   1.14.8-aliyun.1
-   1.16.9-aliyun.1 |
|SecurityGroupId|String|No|No|The ID of the security group to which the ECS instances in the cluster belong.|None|
|KeyPair|String|No|No|The name of the key pair.|You must specify one of the LoginPassword and KeyPair parameters.|
|EndpointPublicAccess|Boolean|No|No|Specifies whether to enable Internet access to the API server.|Default value: false. Valid values:-   true: enables access to the API server over the Internet.
-   false: disables access to the API server over the Internet. The API server allows only access over the internal network. |
|TimeoutMins|Number|No|No|The timeout period for the system to create a cluster stack.|Default value: 60.Unit: minutes. |
|VSwitchIds|List|Yes|No|The VSwitch IDs of worker nodes.|One to three VSwitches can be specified.|

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
|Value|String|No|No|The tag value.|The tag value must be 0 to 128 characters in length and cannot start with `aliyun`, `acs:`, `http://`, or `https://`.|

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
|Category|String|Yes|No|The data disk type of worker nodes.|Valid values:-   cloud: basic disk
-   cloud\_ssd: standard SSD
-   cloud\_efficiency: ultra disk |
|Size|Number|Yes|No|The size of the data disk.|Valid values: 40 to 32768.Unit: GB. |

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
|Config|String|No|No|The configurations of the add-on.|If this parameter is empty, no configuration is required.|
|Name|String|Yes|No|The name of the add-on.|None|

## Response parameters

Fn::GetAtt

-   ClusterId: the ID of the cluster.
-   TaskId: the ID of the task. The task ID is automatically assigned by the system and can be used to query the task status.
-   WorkerRamRoleName: the RAM role name of the worker node.

## Examples

`JSON` format

```
{
  "ROSTemplateFormatVersion": "2015-09-01",
  "Parameters": {
    "EndpointPublicAccess": {
      "Type": "Boolean",
      "Description": "Whether to enable the public network API Server:\ntrue: which means that the public network API Server is open.\nfalse: If set to false, the API server on the public network will not be created, only the API server on the private network will be created.Default to false.",
      "AllowedValues": [
        "true",
        "false"
      ],
      "Default": false
    },
    "WorkerPeriod": {
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
      ],
      "Default": 1
    },
    "WorkerPeriodUnit": {
      "Type": "String",
      "Description": "When you specify PrePaid, you need to specify the period. The options are:\nWeek: Time is measured in weeks\nMonth: time in months\nDefault to Month.",
      "AllowedValues": [
        "Week",
        "Month"
      ],
      "Default": "Month"
    },
    "Addons": {
      "Type": "Json",
      "Description": "A combination of addon plugins for Kubernetes clusters.\nNetwork plug-in: including Flannel and Terway network plug-ins\nLog service: Optional. If the log service is not enabled, the cluster audit function cannot be used.\nIngress: The installation of the Ingress component is enabled by default."
    },
    "WorkerSystemDiskCategory": {
      "Type": "String",
      "Description": "Worker node system disk type. The value range is:\ncloud_efficiency: efficient cloud disk\ncloud_ssd: SSD cloud disk\nDefault to cloud_efficiency.",
      "AllowedValues": [
        "cloud_efficiency",
        "cloud_ssd"
      ],
      "Default": "cloud_efficiency"
    },
    "WorkerSystemDiskSize": {
      "Type": "Number",
      "Description": "Worker disk system disk size, the unit is GiB.\nDefault to 120.",
      "MinValue": 1,
      "Default": 120
    },
    "Name": {
      "Type": "String",
      "Description": "The name of the cluster. The cluster name can use uppercase and lowercase letters, Chinese characters, numbers, and dashes."
    },
    "Taint": {
      "Type": "Json",
      "Description": "It is used to mark nodes with taints. It is usually used for the scheduling strategy of Pods. The corresponding concept is: tolerance. If there is a corresponding tolerance mark on the Pods, the stain on the node can be tolerated and scheduled to the node."
    },
    "CloudMonitorFlags": {
      "Type": "Boolean",
      "Description": "Whether to install the cloud monitoring plugin:\ntrue: indicates installation\nfalse: Do not install\nDefault to false",
      "AllowedValues": [
        "true",
        "false"
      ],
      "Default": false
    },
    "ServiceCidr": {
      "Type": "String",
      "Description": "The service network segment cannot conflict with the VPC network segment and the container network segment. When the system is selected to automatically create a VPC, the network segment 172.19.0.0/20 is used by default.",
      "Default": "172.19.0.0/20"
    },
    "WorkerAutoRenew": {
      "Type": "Boolean",
      "Description": "Whether to enable automatic renewal of Worker nodes. The optional values are:\ntrue: automatic renewal\nfalse: do not renew automatically\nDefault to true.",
      "AllowedValues": [
        "true",
        "false"
      ],
      "Default": true
    },
    "ProxyMode": {
      "Type": "String",
      "Description": "kube-proxy proxy mode, supports both iptables and IPVS modes. The default is iptables.",
      "AllowedValues": [
        "iptables",
        "IPVS"
      ],
      "Default": "iptables"
    },
    "Tags": {
      "Type": "Json",
      "Description": "Tag the cluster."
    },
    "DisableRollback": {
      "Type": "Boolean",
      "Description": "Whether the failure was rolled back:\ntrue: indicates that it fails to roll back\nfalse: rollback failed\nThe default is true. If rollback fails, resources produced during the creation process will be released. False is not recommended.",
      "AllowedValues": [
        "true",
        "false"
      ],
      "Default": true
    },
    "WorkerInstanceTypes": {
      "Type": "CommaDelimitedList",
      "Description": "Worker node ECS specification type code. For more details, see Instance Specification Family.",
      "MinLength": 1,
      "MaxLength": 5
    },
    "LoginPassword": {
      "Type": "String",
      "Description": "SSH login password. Password rules are 8-30 characters and contain three items (upper and lower case letters, numbers, and special symbols). Specify one of KeyPair or LoginPassword."
    },
    "KubernetesVersion": {
      "Type": "String",
      "Description": "Kubernetes version.  Default to 1.16.9-aliyun.1, 1.14.8-aliyun.1 and so on.",
      "Default": "1.14.8-aliyun.1"
    },
    "ContainerCidr": {
      "Type": "String",
      "Description": "The container network segment cannot conflict with the VPC network segment. When the system is selected to automatically create a VPC, the network segment 172.16.0.0/16 is used by default.",
      "Default": "172.16.0.0/16"
    },
    "KeyPair": {
      "Type": "String",
      "Description": "Key pair name. Specify one of KeyPair or LoginPassword."
    },
    "WorkerInstanceChargeType": {
      "Type": "String",
      "Description": "Worker node payment type. The optional values are:\nPrePaid: prepaid\nPostPaid: Pay as you go\nDefault to PostPaid.",
      "AllowedValues": [
        "PrePaid",
        "PostPaid"
      ],
      "Default": "PostPaid"
    },
    "VSwitchIds": {
      "Type": "CommaDelimitedList",
      "Description": "The virtual switch ID of the worker node.",
      "MinLength": 1
    },
    "WorkerDataDisks": {
      "Type": "Json",
      "Description": "A combination of configurations such as worker data disk type and size. This parameter is valid only when the worker node data disk is mounted."
    },
    "SecurityGroupId": {
      "Type": "String",
      "Description": "Specifies the ID of the security group to which the cluster ECS instance belongs."
    },
    "TimeoutMins": {
      "Type": "Number",
      "Description": "Cluster resource stack creation timeout, in minutes. The default value is 60.",
      "Default": 60
    },
    "WorkerDataDisk": {
      "Type": "Boolean",
      "Description": "Whether to mount the data disk. The options are as follows:\ntrue: indicates that the worker node mounts data disks.\nfalse: indicates that the worker node does not mount data disks.\nDefault to false.",
      "AllowedValues": [
        "true",
        "false"
      ],
      "Default": false
    },
    "VpcId": {
      "Type": "String",
      "Description": "VPC ID."
    },
    "NumOfNodes": {
      "Type": "Number",
      "Description": "Number of worker nodes. The range is [0,300].\nDefault to 3.",
      "MinValue": 2,
      "MaxValue": 300,
      "Default": 3
    },
    "WorkerAutoRenewPeriod": {
      "Type": "Number",
      "Description": "Automatic renewal cycle, which takes effect when prepaid and automatic renewal are selected, and is required:\nWhen PeriodUnit = Week, the values are: {\"1\", \"2\", \"3\"}\nWhen PeriodUnit = Month, the value is {\"1\", \"2\", \"3\", \"6\", \"12\"}\nDefault to 1.",
      "AllowedValues": [
        1,
        2,
        3,
        6,
        12
      ],
      "Default": 1
    },
    "SnatEntry": {
      "Type": "Boolean",
      "Description": "Whether to configure SNAT for the network.\nWhen a VPC can access the public network environment, set it to false.\nWhen an existing VPC cannot access the public network environment:\nWhen set to True, SNAT is configured and the public network environment can be accessed at this time.\nIf set to false, it means that SNAT is not configured and the public network environment cannot be accessed at this time.\nDefault to true.",
      "AllowedValues": [
        "true",
        "false"
      ],
      "Default": true
    }
  },
  "Resources": {
    "ManagedKubernetesCluster": {
      "Type": "ALIYUN::CS::ManagedKubernetesCluster",
      "Properties": {
        "EndpointPublicAccess": {
          "Ref": "EndpointPublicAccess"
        },
        "WorkerPeriod": {
          "Ref": "WorkerPeriod"
        },
        "WorkerPeriodUnit": {
          "Ref": "WorkerPeriodUnit"
        },
        "Addons": {
          "Ref": "Addons"
        },
        "WorkerSystemDiskCategory": {
          "Ref": "WorkerSystemDiskCategory"
        },
        "WorkerSystemDiskSize": {
          "Ref": "WorkerSystemDiskSize"
        },
        "Name": {
          "Ref": "Name"
        },
        "Taint": {
          "Ref": "Taint"
        },
        "CloudMonitorFlags": {
          "Ref": "CloudMonitorFlags"
        },
        "ServiceCidr": {
          "Ref": "ServiceCidr"
        },
        "WorkerAutoRenew": {
          "Ref": "WorkerAutoRenew"
        },
        "ProxyMode": {
          "Ref": "ProxyMode"
        },
        "Tags": {
          "Ref": "Tags"
        },
        "DisableRollback": {
          "Ref": "DisableRollback"
        },
        "WorkerInstanceTypes": {
          "Ref": "WorkerInstanceTypes"
        },
        "LoginPassword": {
          "Ref": "LoginPassword"
        },
        "KubernetesVersion": {
          "Ref": "KubernetesVersion"
        },
        "ContainerCidr": {
          "Ref": "ContainerCidr"
        },
        "KeyPair": {
          "Ref": "KeyPair"
        },
        "WorkerInstanceChargeType": {
          "Ref": "WorkerInstanceChargeType"
        },
        "VSwitchIds": {
          "Ref": "VSwitchIds"
        },
        "WorkerDataDisks": {
          "Ref": "WorkerDataDisks"
        },
        "SecurityGroupId": {
          "Ref": "SecurityGroupId"
        },
        "TimeoutMins": {
          "Ref": "TimeoutMins"
        },
        "WorkerDataDisk": {
          "Ref": "WorkerDataDisk"
        },
        "VpcId": {
          "Ref": "VpcId"
        },
        "NumOfNodes": {
          "Ref": "NumOfNodes"
        },
        "WorkerAutoRenewPeriod": {
          "Ref": "WorkerAutoRenewPeriod"
        },
        "SnatEntry": {
          "Ref": "SnatEntry"
        }
      }
    }
  },
  "Outputs": {
    "TaskId": {
      "Description": "Task ID. Automatically assigned by the system, the user queries the task status.",
      "Value": {
        "Fn::GetAtt": [
          "ManagedKubernetesCluster",
          "TaskId"
        ]
      }
    },
    "ClusterId": {
      "Description": "Cluster instance ID.",
      "Value": {
        "Fn::GetAtt": [
          "ManagedKubernetesCluster",
          "ClusterId"
        ]
      }
    },
    "WorkerRamRoleName": {
      "Description": "Worker ram role name.",
      "Value": {
        "Fn::GetAtt": [
          "ManagedKubernetesCluster",
          "WorkerRamRoleName"
        ]
      }
    }
  }
}
```

`YAML` format

```
ROSTemplateFormatVersion: '2015-09-01'
Parameters:
  EndpointPublicAccess:
    Type: Boolean
    Description: >-
      Whether to enable the public network API Server:
      true: which means that the public network API Server is open.
      false: If set to false, the API server on the public network will not be
      created, only the API server on the private network will be
      created.Default to false.
    AllowedValues:
      - 'true'
      - 'false'
    Default: false
  WorkerPeriod:
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
    Default: 1
  WorkerPeriodUnit:
    Type: String
    Description: |-
      When you specify PrePaid, you need to specify the period. The options are:
      Week: Time is measured in weeks
      Month: time in months
      Default to Month.
    AllowedValues:
      - Week
      - Month
    Default: Month
  Addons:
    Type: Json
    Description: >-
      A combination of addon plugins for Kubernetes clusters.
      Network plug-in: including Flannel and Terway network plug-ins
      Log service: Optional. If the log service is not enabled, the cluster
      audit function cannot be used.
      Ingress: The installation of the Ingress component is enabled by default.
  WorkerSystemDiskCategory:
    Type: String
    Description: |-
      Worker node system disk type. The value range is:
      cloud_efficiency: efficient cloud disk
      cloud_ssd: SSD cloud disk
      Default to cloud_efficiency.
    AllowedValues:
      - cloud_efficiency
      - cloud_ssd
    Default: cloud_efficiency
  WorkerSystemDiskSize:
    Type: Number
    Description: |-
      Worker disk system disk size, the unit is GiB.
      Default to 120.
    MinValue: 1
    Default: 120
  Name:
    Type: String
    Description: >-
      The name of the cluster. The cluster name can use uppercase and lowercase
      letters, Chinese characters, numbers, and dashes.
  Taint:
    Type: Json
    Description: >-
      It is used to mark nodes with taints. It is usually used for the
      scheduling strategy of Pods. The corresponding concept is: tolerance. If
      there is a corresponding tolerance mark on the Pods, the stain on the node
      can be tolerated and scheduled to the node.
  CloudMonitorFlags:
    Type: Boolean
    Description: |-
      Whether to install the cloud monitoring plugin:
      true: indicates installation
      false: Do not install
      Default to false
    AllowedValues:
      - 'true'
      - 'false'
    Default: false
  ServiceCidr:
    Type: String
    Description: >-
      The service network segment cannot conflict with the VPC network segment
      and the container network segment. When the system is selected to
      automatically create a VPC, the network segment 172.19.0.0/20 is used by
      default.
    Default: 172.19.0.0/20
  WorkerAutoRenew:
    Type: Boolean
    Description: >-
      Whether to enable automatic renewal of Worker nodes. The optional values
      are:
      true: automatic renewal
      false: do not renew automatically
      Default to true.
    AllowedValues:
      - 'true'
      - 'false'
    Default: true
  ProxyMode:
    Type: String
    Description: >-
      kube-proxy proxy mode, supports both iptables and IPVS modes. The default
      is iptables.
    AllowedValues:
      - iptables
      - IPVS
    Default: iptables
  Tags:
    Type: Json
    Description: Tag the cluster.
  DisableRollback:
    Type: Boolean
    Description: >-
      Whether the failure was rolled back:
      true: indicates that it fails to roll back
      false: rollback failed
      The default is true. If rollback fails, resources produced during the
      creation process will be released. False is not recommended.
    AllowedValues:
      - 'true'
      - 'false'
    Default: true
  WorkerInstanceTypes:
    Type: CommaDelimitedList
    Description: >-
      Worker node ECS specification type code. For more details, see Instance
      Specification Family.
    MinLength: 1
    MaxLength: 5
  LoginPassword:
    Type: String
    Description: >-
      SSH login password. Password rules are 8-30 characters and contain three
      items (upper and lower case letters, numbers, and special symbols).
      Specify one of KeyPair or LoginPassword.
  KubernetesVersion:
    Type: String
    Description: Kubernetes version.  Default to 1.16.9-aliyun.1, 1.14.8-aliyun.1 and so on.
    Default: 1.14.8-aliyun.1
  ContainerCidr:
    Type: String
    Description: >-
      The container network segment cannot conflict with the VPC network
      segment. When the system is selected to automatically create a VPC, the
      network segment 172.16.0.0/16 is used by default.
    Default: 172.16.0.0/16
  KeyPair:
    Type: String
    Description: Key pair name. Specify one of KeyPair or LoginPassword.
  WorkerInstanceChargeType:
    Type: String
    Description: |-
      Worker node payment type. The optional values are:
      PrePaid: prepaid
      PostPaid: Pay as you go
      Default to PostPaid.
    AllowedValues:
      - PrePaid
      - PostPaid
    Default: PostPaid
  VSwitchIds:
    Type: CommaDelimitedList
    Description: The virtual switch ID of the worker node.
    MinLength: 1
  WorkerDataDisks:
    Type: Json
    Description: >-
      A combination of configurations such as worker data disk type and size.
      This parameter is valid only when the worker node data disk is mounted.
  SecurityGroupId:
    Type: String
    Description: >-
      Specifies the ID of the security group to which the cluster ECS instance
      belongs.
  TimeoutMins:
    Type: Number
    Description: >-
      Cluster resource stack creation timeout, in minutes. The default value is
      60.
    Default: 60
  WorkerDataDisk:
    Type: Boolean
    Description: |-
      Whether to mount the data disk. The options are as follows:
      true: indicates that the worker node mounts data disks.
      false: indicates that the worker node does not mount data disks.
      Default to false.
    AllowedValues:
      - 'true'
      - 'false'
    Default: false
  VpcId:
    Type: String
    Description: VPC ID.
  NumOfNodes:
    Type: Number
    Description: |-
      Number of worker nodes. The range is [0,300].
      Default to 3.
    MinValue: 2
    MaxValue: 300
    Default: 3
  WorkerAutoRenewPeriod:
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
    Default: 1
  SnatEntry:
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
      - 'true'
      - 'false'
    Default: true
Resources:
  ManagedKubernetesCluster:
    Type: 'ALIYUN::CS::ManagedKubernetesCluster'
    Properties:
      EndpointPublicAccess:
        Ref: EndpointPublicAccess
      WorkerPeriod:
        Ref: WorkerPeriod
      WorkerPeriodUnit:
        Ref: WorkerPeriodUnit
      Addons:
        Ref: Addons
      WorkerSystemDiskCategory:
        Ref: WorkerSystemDiskCategory
      WorkerSystemDiskSize:
        Ref: WorkerSystemDiskSize
      Name:
        Ref: Name
      Taint:
        Ref: Taint
      CloudMonitorFlags:
        Ref: CloudMonitorFlags
      ServiceCidr:
        Ref: ServiceCidr
      WorkerAutoRenew:
        Ref: WorkerAutoRenew
      ProxyMode:
        Ref: ProxyMode
      Tags:
        Ref: Tags
      DisableRollback:
        Ref: DisableRollback
      WorkerInstanceTypes:
        Ref: WorkerInstanceTypes
      LoginPassword:
        Ref: LoginPassword
      KubernetesVersion:
        Ref: KubernetesVersion
      ContainerCidr:
        Ref: ContainerCidr
      KeyPair:
        Ref: KeyPair
      WorkerInstanceChargeType:
        Ref: WorkerInstanceChargeType
      VSwitchIds:
        Ref: VSwitchIds
      WorkerDataDisks:
        Ref: WorkerDataDisks
      SecurityGroupId:
        Ref: SecurityGroupId
      TimeoutMins:
        Ref: TimeoutMins
      WorkerDataDisk:
        Ref: WorkerDataDisk
      VpcId:
        Ref: VpcId
      NumOfNodes:
        Ref: NumOfNodes
      WorkerAutoRenewPeriod:
        Ref: WorkerAutoRenewPeriod
      SnatEntry:
        Ref: SnatEntry
Outputs:
  TaskId:
    Description: >-
      Task ID. Automatically assigned by the system, the user queries the task
      status.
    Value:
      'Fn::GetAtt':
        - ManagedKubernetesCluster
        - TaskId
  ClusterId:
    Description: Cluster instance ID.
    Value:
      'Fn::GetAtt':
        - ManagedKubernetesCluster
        - ClusterId
  WorkerRamRoleName:
    Description: Worker ram role name.
    Value:
      'Fn::GetAtt':
        - ManagedKubernetesCluster
        - WorkerRamRoleName
```


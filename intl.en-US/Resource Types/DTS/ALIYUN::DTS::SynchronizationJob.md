# ALIYUN::DTS::SynchronizationJob

ALIYUN::DTS::SynchronizationJob is used to purchase a synchronization instance and configure a synchronization task.

## Syntax

```
{
  "Type": "ALIYUN::DTS::SynchronizationJob",
  "Properties": {
    "SynchronizationJobClass": String,
    "SourceEndpoint": Map,
    "PayType": String,
    "DataInitialization": Boolean,
    "Period": String,
    "DestRegion": String,
    "SourceRegion": String,
    "UsedTime": Integer,
    "SynchronizationObjects": List,
    "NetworkType": String,
    "DestinationEndpoint": Map,
    "StructureInitialization": Boolean,
    "Topology": String
  }
}
```

## Properties

|Property|Type|Required|Editable|Description|Constraint|
|--------|----|--------|--------|-----------|----------|
|SynchronizationJobClass|String|Yes|No|The type of the synchronization instance.|Default value: small. Valid values: -   micro
-   small
-   medium
-   large |
|SourceEndpoint|Map|Yes|No|The configurations of the source instance.|For more information, see [SourceEndpoint properties](#section_tl7_rc8_up0).|
|PayType|String|No|No|The billing method.|Valid values: -   Postpaid
-   Prepaid |
|DataInitialization|Boolean|No|No|Specifies whether to initialize full data before synchronization.|Default value: true. Valid values: -   true:
-   false |
|Period|String|No|No|The billing cycle of the subscription instance.|Valid values: -   Year
-   Month

This parameter takes effect only when PayType is set to Prepaid.|
|DestRegion|String|Yes|No|The region where the destination instance is deployed.|None|
|SourceRegion|String|Yes|No|The region where the source instance is deployed.|None|
|UsedTime|Integer|No|No|The subscription duration of the subscription instance.|This parameter takes effect only when PayType is set to Prepaid.|
|SynchronizationObjects|List|No|No|The objects to be synchronized.|For more information, see [SynchronizationObjects properties](#section_zyp_t3h_v84).|
|NetworkType|String|No|No|The type of the data transmission network that is used for cross-region synchronization.|Default value: Internet. Valid values: -   Internet
-   Intranet |
|DestinationEndpoint|Map|Yes|No|The synchronization channel configurations.|For more information, see [DestinationEndpoint properties](#section_eup_ujp_2te).|
|StructureInitialization|Boolean|No|No|Specifies whether to initialize the schema before synchronization.|Default value: true. Valid values: -   true
-   false |
|Topology|String|No|No|The synchronization topology.|Default value: oneway. Valid values: -   oneway
-   bidirectional

This parameter can be set to bidirectional only for synchronization between two MySQL instances.|

## SourceEndpoint syntax

```
"SourceEndpoint": {
  "UserName": String,
  "InstanceId": String,
  "IP": String,
  "Port": String,
  "Role": String,
  "OwnerID": String,
  "Password": String,
  "InstanceType": String,
  "InstanceTypeForCreation": String
}
```

## SourceEndpoint properties

|Property|Type|Required|Editable|Description|Constraint|
|--------|----|--------|--------|-----------|----------|
|UserName|String|No|No|The username that is used to connect to the source instance.|This parameter is required when the source instance is an ECS instance or an on-premises database that is connected over an Express Connect circuit. You do not need to specify this parameter when the source instance is an ApsaraDB for Redis instance.|
|InstanceId|String|No|No|The ID of the source instance.|None|
|IP|String|No|No|The IP address of the source instance.|This parameter is required when the source instance is an on-premises database that is connected over an Express Connect circuit.|
|Port|String|No|No|The port on which the source instance is listening.|This parameter is required when the source instance is an ECS instance or an on-premises database that is connected over an Express Connect circuit.|
|Role|String|No|No|The RAM role that the Alibaba Cloud account of the source instance assigns to the Alibaba Cloud account of the destination instance. This parameter is available if the source and destination instances belong to different Alibaba Cloud accounts. For more information about role permissions and how to grant permissions to a role, see [Instance types supported by cross-account data migration and synchronization]().|None|
|OwnerID|String|No|No|The ID of the Alibaba Cloud account to which the source instance belongs. This parameter is available if the source and destination instances belong to different Alibaba Cloud accounts.|None|
|Password|String|No|No|The password that is used to connect to the source instance.|This parameter is required when the source instance is an ECS instance or an on-premises database that is connected over an Express Connect circuit.|
|InstanceType|String|Yes|No|The type of the source instance.|Valid values: -   Redis: ApsaraDB for Redis instance
-   RDS: ApsaraDB RDS instance
-   POLARDB: PolarDB for MySQL cluster
-   ECS: self-managed database that is hosted on ECS
-   Express: self-managed database that is connected over Express Connect
-   dg: self-managed database that is connected over Database Gateway
-   cen: self-managed database that is connected over Cloud Enterprise Network \(CEN\) |
|InstanceTypeForCreation|String|No|No|The type of the source instance for synchronization channel configurations.|Valid values:-   MySQL
-   PolarDB
-   Redis
-   SQLServer
-   PostgreSQL
-   PolarDB-X \(formerly known as DRDS\) |

## SynchronizationObjects syntax

```
"SynchronizationObjects": [
  {
    "TableExcludes": List,
    "NewSchemaName": String,
    "NewDBName": String,
    "TableIncludes": List,
    "SchemaName": String,
    "DBName": String
  }
]
```

## SynchronizationObjects properties

|Property|Type|Required|Editable|Description|Constraint|
|--------|----|--------|--------|-----------|----------|
|TableExcludes|List|No|No|The names of tables not to be synchronized from the source database.|None|
|NewSchemaName|String|No|No|The mapped name of the source schema in the destination instance.|None|
|NewDBName|String|No|No|The mapped name of the source database in the destination instance.|None|
|TableIncludes|List|No|No|The table to be synchronized.|None|
|SchemaName|String|No|No|The name of the schema to be synchronized.|None|
|DBName|String|No|No|The name of the database to be synchronized.|None|

## TableExcludes syntax

```
"TableExcludes": [
  {
    "TableName": String
  }
]
```

## TableExcludes properties

|Property|Type|Required|Editable|Description|Constraint|
|--------|----|--------|--------|-----------|----------|
|TableName|String|No|No|The name of the table.|None|

## TableIncludes syntax

```
"TableIncludes": [
  {
    "TableName": String,
    "FilterCondition": String,
    "ColumnExcludes": List,
    "ColumnIncludes": List,
    "NewTableName": String
  }
]
```

## TableIncludes properties

|Property|Type|Required|Editable|Description|Constraint|
|--------|----|--------|--------|-----------|----------|
|TableName|String|No|No|The name of the table to be synchronized.|None|
|FilterCondition|String|No|No|The filter condition.|None|
|ColumnExcludes|List|No|No|The name of the column not to be synchronized.|None|
|ColumnIncludes|List|No|No|The name of the column to be synchronized.|None|
|NewTableName|String|No|No|The mapped name of the source table in the destination instance.|None|

## ColumnExcludes syntax

```
"ColumnExcludes": [
  {
    "ColumnName": String
  }
]
```

## ColumnExcludes properties

|Property|Type|Required|Editable|Description|Constraint|
|--------|----|--------|--------|-----------|----------|
|ColumnName|String|No|No|The name of the column not to be synchronized.|None|

## ColumnIncludes syntax

```
"ColumnIncludes": [
  {
    "NewColumnName": String,
    "ColumnName": String
  }
]
```

## ColumnIncludes properties

|Property|Type|Required|Editable|Description|Constraint|
|--------|----|--------|--------|-----------|----------|
|NewColumnName|String|No|No|The mapped name of the source column in the destination instance.|None|
|ColumnName|String|No|No|The name of the column to be synchronized.|None|

## DestinationEndpoint syntax

```
"DestinationEndpoint": {
  "UserName": String,
  "InstanceId": String,
  "IP": String,
  "InstanceType": String,
  "Password": String,
  "InstanceTypeForCreation": String,
  "Port": String
}
```

## DestinationEndpoint properties

|Property|Type|Required|Editable|Description|Constraint|
|--------|----|--------|--------|-----------|----------|
|UserName|String|No|No|The username that is used to connect to the destination instance.|This parameter is required when the destination instance is an ECS instance or an on-premises database that is connected over an Express Connect circuit. You do not need to specify this parameter when the source instance is an ApsaraDB for Redis instance.|
|InstanceId|String|No|No|The ID of the destination instance.|-   If the destination instance is a MaxCompute project, set the parameter to the name of the MaxCompute project.
-   If the destination instance is an AnalyticDB for MySQL cluster, set the parameter to the ID of the AnalyticDB for MySQL cluster.
-   If the destination instance is a DataHub project, set the parameter to the name of the DataHub project. |
|IP|String|No|No|The IP address of the destination instance.|This parameter is required when the destination instance is an on-premises database that is connected over an Express Connect circuit.|
|InstanceType|String|Yes|No|The type of the destination instance.|Default values: RDS. Valid values: -   Redis: ApsaraDB for Redis instance
-   RDS: ApsaraDB RDS instance
-   POLARDB: PolarDB for MySQL cluster
-   ECS: self-managed database that is hosted on ECS
-   Express: user-created database that is connected over Express Connect
-   MaxCompute: MaxCompute project
-   DataHub: DataHub project
-   AnalyticDB: AnalyticDB for MySQL V2.0 cluster
-   AnalyticDB30: AnalyticDB for MySQL V3.0 cluster |
|InstanceTypeForCreation|String|No|No|The type of the destination instance for synchronization channel configurations.|Valid values:-   MySQL
-   PolarDB
-   Redis
-   MaxCompute
-   DataHub
-   Kafka
-   Elasticsearch
-   Tablestore |
|Password|String|No|No|The password that is used to connect to the destination instance.|This parameter is required when the destination instance is an ECS instance or an on-premises database that is connected over an Express Connect circuit.|
|Port|String|No|No|The port on which the destination instance is listening.|This parameter is required when the destination instance is an ECS instance or an on-premises database that is connected over an Express Connect circuit.|

## Response parameters

Fn::GetAtt

SynchronizationJobId: the ID of the synchronization instance.

## Examples

`JSON` format

```
{
  "ROSTemplateFormatVersion": "2015-09-01",
  "Parameters": {
    "SynchronizationObjects": {
      "Type": "Json",
      "Description": "Objects that need to be synchronized"
    },
    "Period": {
      "Type": "String",
      "Description": "If prepaid payment type, then the parameters specified in the purchase package instance or instances as examples of a monthly subscription, which can be:\nYear: Annual, Month: monthly",
      "AllowedValues": [
        "Year",
        "Month"
      ]
    },
    "PayType": {
      "Type": "String",
      "Description": "Payment type, which include:\nPostpaid: postpaid type, Prepaid: Prepaid type. Default is Postpaid",
      "AllowedValues": [
        "Postpaid",
        "Prepaid"
      ],
      "Default": "Postpaid"
    },
    "Topology": {
      "Type": "String",
      "Description": "Synchronous topology, the value includes: oneway, bidirectional.the default value is: oneway, only MySQL-> MySQL synchronization, this parameter can receive the value bidirectional"
    },
    "SourceRegion": {
      "Type": "String",
      "Description": "Region where the synchronization source instance is located."
    },
    "DataInitialization": {
      "Type": "Boolean",
      "Description": "Whether to perform full data initialization before synchronization. The values include:true: means full data initialization\nfalse: no full data initialization\nThe default value is: true",
      "AllowedValues": [
        "true",
        "false"
      ],
      "Default": true
    },
    "NetworkType": {
      "Type": "String",
      "Description": "When synchronization geographies, the type of data transmission network used. Value include: Internet, Intranet. The default value is: Internet",
      "AllowedValues": [
        "Internet",
        "Intranet"
      ]
    },
    "DestinationEndpoint": {
      "Type": "Json",
      "Description": "Migration target configuration"
    },
    "SourceEndpoint": {
      "Type": "Json",
      "Description": "Migration source configuration"
    },
    "UsedTime": {
      "Type": "Number",
      "Description": "f the payment type is prepaid, then this parameter is the length of the purchase, and parameters such as 1, 2, 3 can be passed in as needed"
    },
    "StructureInitialization": {
      "Type": "Boolean",
      "Description": "Whether to initialize the structure object before synchronization. The values include:true: indicates that the structure object is initialized\nfalse: no result object initialization\nThe default value is: true",
      "AllowedValues": [
        "true",
        "false"
      ],
      "Default": true
    },
    "SynchronizationJobClass": {
      "Type": "String",
      "Description": "Synchronous instance specifications, which can be:\nmicro, small, medium, large and so on. The default value is: small"
    },
    "DestRegion": {
      "Type": "String",
      "Description": "Region where the synchronization target instance is located."
    }
  },
  "Resources": {
    "SynchronizationJob": {
      "Type": "ALIYUN::DTS::SynchronizationJob",
      "Properties": {
        "SynchronizationObjects": {
          "Ref": "SynchronizationObjects"
        },
        "Period": {
          "Ref": "Period"
        },
        "PayType": {
          "Ref": "PayType"
        },
        "Topology": {
          "Ref": "Topology"
        },
        "SourceRegion": {
          "Ref": "SourceRegion"
        },
        "DataInitialization": {
          "Ref": "DataInitialization"
        },
        "NetworkType": {
          "Ref": "NetworkType"
        },
        "DestinationEndpoint": {
          "Ref": "DestinationEndpoint"
        },
        "SourceEndpoint": {
          "Ref": "SourceEndpoint"
        },
        "UsedTime": {
          "Ref": "UsedTime"
        },
        "StructureInitialization": {
          "Ref": "StructureInitialization"
        },
        "SynchronizationJobClass": {
          "Ref": "SynchronizationJobClass"
        },
        "DestRegion": {
          "Ref": "DestRegion"
        }
      }
    }
  },
  "Outputs": {
    "SynchronizationJobId": {
      "Description": "Synchronization instance ID",
      "Value": {
        "Fn::GetAtt": [
          "SynchronizationJob",
          "SynchronizationJobId"
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
  SynchronizationObjects:
    Type: Json
    Description: Objects that need to be synchronized
  Period:
    Type: String
    Description: >-
      If prepaid payment type, then the parameters specified in the purchase
      package instance or instances as examples of a monthly subscription, which
      can be:

      Year: Annual, Month: monthly
    AllowedValues:
      - Year
      - Month
  PayType:
    Type: String
    Description: |-
      Payment type, which include:
      Postpaid: postpaid type, Prepaid: Prepaid type. Default is Postpaid
    AllowedValues:
      - Postpaid
      - Prepaid
    Default: Postpaid
  Topology:
    Type: String
    Description: >-
      Synchronous topology, the value includes: oneway, bidirectional.the
      default value is: oneway, only MySQL-> MySQL synchronization, this
      parameter can receive the value bidirectional
  SourceRegion:
    Type: String
    Description: Region where the synchronization source instance is located.
  DataInitialization:
    Type: Boolean
    Description: >-
      Whether to perform full data initialization before synchronization. The
      values include:true: means full data initialization

      false: no full data initialization

      The default value is: true
    AllowedValues:
      - 'true'
      - 'false'
    Default: true
  NetworkType:
    Type: String
    Description: >-
      When synchronization geographies, the type of data transmission network
      used. Value include: Internet, Intranet. The default value is: Internet
    AllowedValues:
      - Internet
      - Intranet
  DestinationEndpoint:
    Type: Json
    Description: Migration target configuration
  SourceEndpoint:
    Type: Json
    Description: Migration source configuration
  UsedTime:
    Type: Number
    Description: >-
      f the payment type is prepaid, then this parameter is the length of the
      purchase, and parameters such as 1, 2, 3 can be passed in as needed
  StructureInitialization:
    Type: Boolean
    Description: >-
      Whether to initialize the structure object before synchronization. The
      values include:true: indicates that the structure object is initialized

      false: no result object initialization

      The default value is: true
    AllowedValues:
      - 'true'
      - 'false'
    Default: true
  SynchronizationJobClass:
    Type: String
    Description: |-
      Synchronous instance specifications, which can be:
      micro, small, medium, large and so on. The default value is: small
  DestRegion:
    Type: String
    Description: Region where the synchronization target instance is located.
Resources:
  SynchronizationJob:
    Type: 'ALIYUN::DTS::SynchronizationJob'
    Properties:
      SynchronizationObjects:
        Ref: SynchronizationObjects
      Period:
        Ref: Period
      PayType:
        Ref: PayType
      Topology:
        Ref: Topology
      SourceRegion:
        Ref: SourceRegion
      DataInitialization:
        Ref: DataInitialization
      NetworkType:
        Ref: NetworkType
      DestinationEndpoint:
        Ref: DestinationEndpoint
      SourceEndpoint:
        Ref: SourceEndpoint
      UsedTime:
        Ref: UsedTime
      StructureInitialization:
        Ref: StructureInitialization
      SynchronizationJobClass:
        Ref: SynchronizationJobClass
      DestRegion:
        Ref: DestRegion
Outputs:
  SynchronizationJobId:
    Description: Synchronization instance ID
    Value:
      'Fn::GetAtt':
        - SynchronizationJob
        - SynchronizationJobId
```


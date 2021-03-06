# ALIYUN::POLARDB::DBCluster

ALIYUN::POLARDB::DBCluster is used to create a PolarDB cluster.

## Syntax

```
{
  "Type": "ALIYUN::POLARDB::DBCluster",
  "Properties": {
    "VpcId": String,
    "DBClusterDescription": String,
    "DBType": String,
    "ClusterNetworkType": String,
    "RenewalStatus": String,
    "AutoRenewPeriod": Integer,
    "Period": Integer,
    "ZoneId": String,
    "SourceResourceId": String,
    "MaintainTime": String,
    "DBVersion": String,
    "CreationOption": String,
    "DBNodeClass": String,
    "VSwitchId": String,
    "SecurityIPList": String,
    "CloneDataPoint": String,
    "PayType": String,
    "CreationCategory": String,
    "BackupRetentionPolicyOnClusterDeletion": String,
    "ResourceGroupId": String,
    "DefaultTimeZone": String,
    "GDNId": String,
    "LowerCaseTableNames": Integer,
    "TDEStatus": Boolean
  }
}
```

## Properties

|Property|Type|Required|Editable|Description|Constraint|
|--------|----|--------|--------|-----------|----------|
|VpcId|String|No|No|The ID of the VPC.|None|
|DBClusterDescription|String|No|Yes|The description of the cluster.|The description must be 2 to 256 characters in length and can contain letters, digits, commas \(,\), and hyphens \(-\). It must start with a letter and cannot start with `http://` or `https://`.|
|DBType|String|Yes|No|The type of the database engine.|Valid values:-   MySQL
-   PostgreSQL
-   Oracle |
|ClusterNetworkType|String|No|No|The network type of the cluster.|Set the value to VPC.|
|RenewalStatus|String|No|Yes|The auto-renewal status of the cluster.|Default value: Normal. Valid values:-   AutoRenewal: The cluster is automatically renewed.
-   Normal: The cluster is manually renewed.
-   NotRenewal: The cluster is no longer renewed.

**Note:** If this parameter is set to NotRenewal, the system does not send a reminder for expiration, but sends an SMS message three days before the cluster expires to remind you that the cluster is not renewed. |
|AutoRenewPeriod|Integer|No|Yes|The auto-renewal period of the cluster.|Default value: 1. Valid values:-   1
-   2
-   3
-   6
-   12
-   24
-   36

Unit: months. |
|Period|Integer|No|No|The auto-renewal period of the subscription cluster when the PayType parameter is set to Prepaid.|Valid values:-   1
-   2
-   3
-   4
-   5
-   6
-   7
-   8
-   9
-   12
-   24
-   36

Unit: months. |
|ZoneId|String|No|No|The ID of the zone.|You can call the [DescribeRegions](/intl.en-US/API Reference/Other operations/DescribeRegions.md) operation to query the zone ID.|
|SourceResourceId|String|No|No|The ID of the source ApsaraDB RDS instance or PolarDB cluster.|This parameter takes effect only when the DBType parameter is set to MySQL and the DBVersion parameter is set to 5.6. This parameter is required when the CreationOption parameter is not set to Normal.|
|MaintainTime|String|No|Yes|The maintenance window of the cluster.|Specify the window in the HH:mmZ-HH:mmZ format. For example, a value of 16:00Z-17:00Z indicates that the cluster can be maintained from 00:00 to 01:00 \(UTC+8\).|
|DBVersion|String|Yes|No|The version of the database engine that the cluster runs.|Valid values: -   Value values when DBType is set to MySQL: 5.6 and 8.0.
-   Set the value to 11 when DBType is set to PostgreSQL.
-   Set the value to 11 when DBType is set to Oracle. |
|CreationOption|String|No|No|The method to create the cluster.|Default value: Normal. Valid values:-   Normal: creates a PolarDB cluster.
-   CloneFromPolarDB: clones data from an existing PolarDB cluster to a new PolarDB cluster.
-   CloneFromRDS: clones data from an existing ApsaraDB RDS instance to a new PolarDB cluster.
-   MigrationFromRDS: migrates data from an existing ApsaraDB RDS instance to a new PolarDB cluster.

This parameter can be set to CloneFromRDS or MigrationFromRDS when the DBType parameter is set to MySQL and the DBVersion parameter is set to 5.6.|
|DBNodeClass|String|Yes|No|The node specifications of the cluster.|For more information, see [Specifications and pricing](/intl.en-US/Pricing/Specifications and pricing.md). |
|VSwitchId|String|No|No|The ID of the VSwitch.|None|
|SecurityIPList|String|No|No|The IP address whitelist.|None|
|CloneDataPoint|String|No|No|The point in time at which to clone data.|Default value: LATEST. Valid values:-   LATEST: the latest point in time.

**Note:** You must set this parameter to LATEST if the CreationOption parameter is set to CloneFromRDS.

-   BackupID: the ID of the historical backup set.
-   Timestamp: the historical point in time. Specify the time in the yyyy-MM-ddTHH:mm:ssZ format. The time must be in UTC.

This parameter takes effect only when the DBType parameter is set to MySQL, the DBVersion parameter is set to 5.6, and the CreationOption parameter is set to CloneFromRDS or CloneFromPolarDB.|
|PayType|String|Yes|No|The billing method of the cluster.|Valid values:-   Postpaid: pay-as-you-go
-   Prepaid: subscription |
|CreationCategory|String|No|No|The edition of the cluster.|Set the value to Normal, which indicates the Standard Edition.|
|BackupRetentionPolicyOnClusterDeletion|String|No|No|The backup retention policy that you apply when you delete a cluster.|Default value: NONE. Valid values:-   ALL: All backups are permanently retained.
-   LATEST: The latest backup is permanently retained. A backup for the cluster is automatically created before the cluster is deleted.
-   NONE: No backup is retained when the cluster is deleted.

**Note:** This parameter takes effect only when the DBType parameter is set to MySQL. |
|ResourceGroupId|String|No|No|The ID of the resource group to which the PolarDB cluster belongs.|None|
|DefaultTimeZone|String|No|No|The time zone of the cluster. The time zone must be in UTC.|The default value is SYSTEM, which is the same as the time zone of the region.

You can select a time zone on the hour from -12:00 to +13:00. Example: 00:00.

**Note:** This parameter takes effect only when the DBType parameter is set to MySQL. |
|GDNId|String|No|No|The ID of the global database network \(GDN\).|This parameter is required when the CreationOption parameter is set to CreateGdnStandby.|
|LowerCaseTableNames|Integer|No|No|Specifies whether table names are case-sensitive.|Default value: 1. Valid values:-   1: Table names are case-insensitive.
-   0: Table names are case-sensitive. |
|TDEStatus|Boolean|No|No|Specifies whether to enable transparent data encryption \(TDE\).|Default value: false. Valid values:-   true: enables TDE.

**Note:** You cannot disable TDE after it is enabled.

-   false: disables TDE.

**Note:** The parameter takes effect only when the DBType parameter is set to PostgreSQL or Oracle. |

## Response parameters

Fn::GetAtt

-   DBClusterId: the ID of the cluster.
-   OrderId: the order ID of the cluster.
-   DBNodeIds: the node IDs of the cluster.
-   PrimaryEndpointId: the primary endpoint ID.
-   CustomEndpointIds: the custom cluster endpoint IDs.
-   CustomConnectionStrings: the custom connection strings of the cluster.
-   PrimaryConnectionString: the primary connection string of the cluster.
-   ClusterConnectionString: the custom connection string of the cluster.
-   ClusterEndpointId: the cluster endpoint ID.

## Examples

`JSON` format

```
{
  "ROSTemplateFormatVersion": "2015-09-01",
  "Parameters": {
    "AutoRenewPeriod": {
      "Type": "Number",
      "Description": "Set the cluster auto renewal time. Valid values: 1, 2, 3, 6, 12, 24, 36. Default to 1.",
      "AllowedValues": [
        1,
        2,
        3,
        6,
        12,
        24,
        36
      ],
      "Default": 1
    },
    "DefaultTimeZone": {
      "Type": "String",
      "Description": "Set up a time zone (UTC), the value range is as follows:\nSystem:  The default time zone is the same as the time zone where the region is located. This is default value.\nOther pickable value range is from -12:00 to +13:00, for example, 00:00.\nNote: This parameter takes effect only when DBType is MySQL."
    },
    "TDEStatus": {
      "Type": "Boolean",
      "Description": "Specifies whether to enable Transparent Data Encryption (TDE). Valid values:\ntrue: enable TDE\nfalse: disable TDE (default)\nNote: The parameter takes effect only when DBType is PostgreSQL or Oracle. You cannot disable TDE after it is enabled.",
      "AllowedValues": [
        "True",
        "true",
        "False",
        "false"
      ]
    },
    "CloneDataPoint": {
      "Type": "String",
      "Description": "The time point of data to be cloned. Valid values:\nLATEST: clones data of the latest time point.\n<BackupID>: clones historical backup data. Specify the ID of the specific backup set.\n<Timestamp>: clones data of a historical time point. Specify the specific time in\nthe yyyy-MM-ddTHH:mm:ssZ format. The time must be in UTC.\nDefault value: LATEST.\nNote\nThis parameter takes effect only when the DBType parameter is set to MySQL, the DBVersion parameter is set to 5.6, and the CreationOption parameter is set to CloneFromRDS or CloneFromPolarDB.\nIf the CreationOption parameter is set to CloneFromRDS, the value of this parameter must be LATEST.",
      "Default": "LATEST"
    },
    "GDNId": {
      "Type": "String",
      "Description": "The ID of the Global Database Network (GDN).\nNote: This parameter is required when the CreationOption is CreateGdnStandby."
    },
    "ResourceGroupId": {
      "Type": "String",
      "Description": "The ID of the resource group."
    },
    "ZoneId": {
      "Type": "String",
      "Description": "The zone ID of the cluster. You can call the DescribeRegions operation to query available zones."
    },
    "VSwitchId": {
      "Type": "String",
      "Description": "The ID of the VSwitch to connect to."
    },
    "BackupRetentionPolicyOnClusterDeletion": {
      "Type": "String",
      "Description": "The backup set retention policy when deleting a cluster, the value range is as follows:\nALL: Keep all backups permanently.\nLATEST: Permanently keep the last backup (automatic backup before deletion).\nNONE: The backup set is not retained when the cluster is deleted.\nWhen creating a cluster, the default value is NONE, that is, the backup set is not retained when the cluster is deleted.\nNote: This parameter takes effect only when the value of DBType is MySQL.",
      "AllowedValues": [
        "ALL",
        "LATEST",
        "NONE"
      ]
    },
    "RenewalStatus": {
      "Type": "String",
      "Description": "The auto renewal status of the cluster Valid values:\nAutoRenewal: automatically renews the cluster.\nNormal: manually renews the cluster.\nNotRenewal: does not renew the cluster.\nDefault value: Normal.\nNote If this parameter is set to NotRenewal, the system does not send a reminder for expiration,\nbut only sends an SMS message three days before the cluster expires to remind you\nthat the cluster is not renewed.",
      "AllowedValues": [
        "AutoRenewal",
        "Normal",
        "NotRenewal"
      ],
      "Default": "Normal"
    },
    "DBClusterDescription": {
      "Type": "String",
      "Description": "The description of the cluster. The description must comply with the following rules:\nIt must start with a Chinese character or an English letter.\nIt can contain Chinese and English characters, digits, underscores (_), and hyphens (-).\nIt cannot start with http:// or https://.\nIt must be 2 to 256 characters in length.",
      "MinLength": 2,
      "MaxLength": 256
    },
    "Period": {
      "Type": "Number",
      "Description": "The subscription period of the cluster in month. Valid values: 1, 2, 3, 4, 5, 6, 7, 8, 9, 12, 24, 36.",
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
        36
      ]
    },
    "SourceResourceId": {
      "Type": "String",
      "Description": "The ID of the source RDS instance or source POLARDB cluster.\nNote\nThis parameter takes effect only when the DBType parameter is set to MySQL and the DBVersion parameter is set to 5.6.\nThis parameter is required if the CreationOption parameter is not set to Normal."
    },
    "DBType": {
      "Type": "String",
      "Description": "Database type, value:\nMySQL\nPostgreSQL\nOracle",
      "AllowedValues": [
        "MySQL",
        "Oracle",
        "PostgreSQL"
      ]
    },
    "PayType": {
      "Type": "String",
      "Description": "The billing method of the cluster. Valid values:\nPostpaid: pay-as-you-go\nPrepaid: subscription",
      "AllowedValues": [
        "Postpaid",
        "Prepaid"
      ]
    },
    "CreationCategory": {
      "Type": "String",
      "Description": "Cluster series. The value could be Normal (standard version)."
    },
    "DBNodeClass": {
      "Type": "String",
      "Description": "The node specifications of the cluster. For more information, see Specifications and pricing."
    },
    "CreationOption": {
      "Type": "String",
      "Description": "The method for creating an ApsaraDB for POLARDB cluster. Valid values:\nNormal: creates an ApsaraDB for POLARDB cluster.\nCloneFromPolarDB: clones data from an existing ApsaraDB for POLARDB cluster to a new ApsaraDB for POLARDB cluster.\nCloneFromRDS: clones data from an existing ApsaraDB for RDS instance to a new ApsaraDB\nfor POLARDB cluster.\nMigrationFromRDS: migrates data from an existing ApsaraDB for RDS instance to a new ApsaraDB for POLARDB cluster. The created ApsaraDB for POLARDB cluster is in read-only mode and has binary logs enabled by default.\nCreateGdnStandby: Create a secondary cluster.\nDefault value: Normal.\nNote:\nWhen DBType is MySQL and DBVersion is 5.6, this parameter can be specified as CloneFromRDS or MigrationFromRDS.\nWhen DBType is MySQL and DBVersion is 8.0, this parameter can be specified as CreateGdnStandby.",
      "AllowedValues": [
        "CloneFromPolarDB",
        "CloneFromRDS",
        "MigrationFromRDS",
        "Normal",
        "CreateGdnStandby"
      ],
      "Default": "Normal"
    },
    "DBVersion": {
      "Type": "String",
      "Description": "The version of the database. Valid values:\nMySQL: 5.6, 5.7 or 8.0\nPostgreSQL: 11\nOracle: 11"
    },
    "ClusterNetworkType": {
      "Type": "String",
      "Description": "The network type of the cluster. Currently, only VPC is supported. Default value: VPC.",
      "AllowedValues": [
        "VPC"
      ],
      "Default": "VPC"
    },
    "VpcId": {
      "Type": "String",
      "Description": "The ID of the VPC to connect to."
    },
    "SecurityIPList": {
      "Type": "String",
      "Description": "The whitelist of the Apsara PolarDB cluster."
    },
    "MaintainTime": {
      "Type": "String",
      "Description": "The maintainable time of the cluster:\nFormat: HH: mmZ- HH: mmZ.\nExample: 16:00Z-17:00Z, which means 0 to 1 (UTC+08:00) for routine maintenance."
    },
    "LowerCaseTableNames": {
      "Type": "Number",
      "Description": "Whether the table name is case sensitive, the value range is as follows:\n1: Not case sensitive0: case sensitive\nThe default value is 1.\nNote: This parameter takes effect only when the value of DBType is MySQL.",
      "AllowedValues": [
        0,
        1
      ]
    }
  },
  "Resources": {
    "DBCluster": {
      "Type": "ALIYUN::POLARDB::DBCluster",
      "Properties": {
        "AutoRenewPeriod": {
          "Ref": "AutoRenewPeriod"
        },
        "DefaultTimeZone": {
          "Ref": "DefaultTimeZone"
        },
        "TDEStatus": {
          "Ref": "TDEStatus"
        },
        "CloneDataPoint": {
          "Ref": "CloneDataPoint"
        },
        "GDNId": {
          "Ref": "GDNId"
        },
        "ResourceGroupId": {
          "Ref": "ResourceGroupId"
        },
        "ZoneId": {
          "Ref": "ZoneId"
        },
        "VSwitchId": {
          "Ref": "VSwitchId"
        },
        "BackupRetentionPolicyOnClusterDeletion": {
          "Ref": "BackupRetentionPolicyOnClusterDeletion"
        },
        "RenewalStatus": {
          "Ref": "RenewalStatus"
        },
        "DBClusterDescription": {
          "Ref": "DBClusterDescription"
        },
        "Period": {
          "Ref": "Period"
        },
        "SourceResourceId": {
          "Ref": "SourceResourceId"
        },
        "DBType": {
          "Ref": "DBType"
        },
        "PayType": {
          "Ref": "PayType"
        },
        "CreationCategory": {
          "Ref": "CreationCategory"
        },
        "DBNodeClass": {
          "Ref": "DBNodeClass"
        },
        "CreationOption": {
          "Ref": "CreationOption"
        },
        "DBVersion": {
          "Ref": "DBVersion"
        },
        "ClusterNetworkType": {
          "Ref": "ClusterNetworkType"
        },
        "VpcId": {
          "Ref": "VpcId"
        },
        "SecurityIPList": {
          "Ref": "SecurityIPList"
        },
        "MaintainTime": {
          "Ref": "MaintainTime"
        },
        "LowerCaseTableNames": {
          "Ref": "LowerCaseTableNames"
        }
      }
    }
  },
  "Outputs": {
    "DBNodeIds": {
      "Description": "The ID list of cluster nodes.",
      "Value": {
        "Fn::GetAtt": [
          "DBCluster",
          "DBNodeIds"
        ]
      }
    },
    "PrimaryConnectionString": {
      "Description": "The primary connection string of the db cluster.",
      "Value": {
        "Fn::GetAtt": [
          "DBCluster",
          "PrimaryConnectionString"
        ]
      }
    },
    "ClusterConnectionString": {
      "Description": "The cluster connection string of the db cluster.",
      "Value": {
        "Fn::GetAtt": [
          "DBCluster",
          "ClusterConnectionString"
        ]
      }
    },
    "ClusterEndpointId": {
      "Description": "The cluster endpoint ID of the db cluster.",
      "Value": {
        "Fn::GetAtt": [
          "DBCluster",
          "ClusterEndpointId"
        ]
      }
    },
    "DBClusterId": {
      "Description": "The ID of the ApsaraDB for POLARDB cluster.",
      "Value": {
        "Fn::GetAtt": [
          "DBCluster",
          "DBClusterId"
        ]
      }
    },
    "CustomEndpointIds": {
      "Description": "The custom endpoint IDs of the db cluster.",
      "Value": {
        "Fn::GetAtt": [
          "DBCluster",
          "CustomEndpointIds"
        ]
      }
    },
    "PrimaryEndpointId": {
      "Description": "The primary endpoint ID of the db cluster.",
      "Value": {
        "Fn::GetAtt": [
          "DBCluster",
          "PrimaryEndpointId"
        ]
      }
    },
    "OrderId": {
      "Description": "The Order ID.",
      "Value": {
        "Fn::GetAtt": [
          "DBCluster",
          "OrderId"
        ]
      }
    },
    "CustomConnectionStrings": {
      "Description": "The custom connection strings of the db cluster.",
      "Value": {
        "Fn::GetAtt": [
          "DBCluster",
          "CustomConnectionStrings"
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
  AutoRenewPeriod:
    Type: Number
    Description: >-
      Set the cluster auto renewal time. Valid values: 1, 2, 3, 6, 12, 24, 36.
      Default to 1.
    AllowedValues:
      - 1
      - 2
      - 3
      - 6
      - 12
      - 24
      - 36
    Default: 1
  DefaultTimeZone:
    Type: String
    Description: >-
      Set up a time zone (UTC), the value range is as follows:

      System:  The default time zone is the same as the time zone where the
      region is located. This is default value.

      Other pickable value range is from -12:00 to +13:00, for example, 00:00.

      Note: This parameter takes effect only when DBType is MySQL.
  TDEStatus:
    Type: Boolean
    Description: >-
      Specifies whether to enable Transparent Data Encryption (TDE). Valid
      values:

      true: enable TDE

      false: disable TDE (default)

      Note: The parameter takes effect only when DBType is PostgreSQL or Oracle.
      You cannot disable TDE after it is enabled.
    AllowedValues:
      - 'True'
      - 'true'
      - 'False'
      - 'false'
  CloneDataPoint:
    Type: String
    Description: >-
      The time point of data to be cloned. Valid values:

      LATEST: clones data of the latest time point.

      <BackupID>: clones historical backup data. Specify the ID of the specific
      backup set.

      <Timestamp>: clones data of a historical time point. Specify the specific
      time in

      the yyyy-MM-ddTHH:mm:ssZ format. The time must be in UTC.

      Default value: LATEST.

      Note

      This parameter takes effect only when the DBType parameter is set to
      MySQL, the DBVersion parameter is set to 5.6, and the CreationOption
      parameter is set to CloneFromRDS or CloneFromPolarDB.

      If the CreationOption parameter is set to CloneFromRDS, the value of this
      parameter must be LATEST.
    Default: LATEST
  GDNId:
    Type: String
    Description: >-
      The ID of the Global Database Network (GDN).

      Note: This parameter is required when the CreationOption is
      CreateGdnStandby.
  ResourceGroupId:
    Type: String
    Description: The ID of the resource group.
  ZoneId:
    Type: String
    Description: >-
      The zone ID of the cluster. You can call the DescribeRegions operation to
      query available zones.
  VSwitchId:
    Type: String
    Description: The ID of the VSwitch to connect to.
  BackupRetentionPolicyOnClusterDeletion:
    Type: String
    Description: >-
      The backup set retention policy when deleting a cluster, the value range
      is as follows:

      ALL: Keep all backups permanently.

      LATEST: Permanently keep the last backup (automatic backup before
      deletion).

      NONE: The backup set is not retained when the cluster is deleted.

      When creating a cluster, the default value is NONE, that is, the backup
      set is not retained when the cluster is deleted.

      Note: This parameter takes effect only when the value of DBType is MySQL.
    AllowedValues:
      - ALL
      - LATEST
      - NONE
  RenewalStatus:
    Type: String
    Description: >-
      The auto renewal status of the cluster Valid values:

      AutoRenewal: automatically renews the cluster.

      Normal: manually renews the cluster.

      NotRenewal: does not renew the cluster.

      Default value: Normal.

      Note If this parameter is set to NotRenewal, the system does not send a
      reminder for expiration,

      but only sends an SMS message three days before the cluster expires to
      remind you

      that the cluster is not renewed.
    AllowedValues:
      - AutoRenewal
      - Normal
      - NotRenewal
    Default: Normal
  DBClusterDescription:
    Type: String
    Description: >-
      The description of the cluster. The description must comply with the
      following rules:

      It must start with a Chinese character or an English letter.

      It can contain Chinese and English characters, digits, underscores (_),
      and hyphens (-).

      It cannot start with http:// or https://.

      It must be 2 to 256 characters in length.
    MinLength: 2
    MaxLength: 256
  Period:
    Type: Number
    Description: >-
      The subscription period of the cluster in month. Valid values: 1, 2, 3, 4,
      5, 6, 7, 8, 9, 12, 24, 36.
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
  SourceResourceId:
    Type: String
    Description: >-
      The ID of the source RDS instance or source POLARDB cluster.

      Note

      This parameter takes effect only when the DBType parameter is set to MySQL
      and the DBVersion parameter is set to 5.6.

      This parameter is required if the CreationOption parameter is not set to
      Normal.
  DBType:
    Type: String
    Description: |-
      Database type, value:
      MySQL
      PostgreSQL
      Oracle
    AllowedValues:
      - MySQL
      - Oracle
      - PostgreSQL
  PayType:
    Type: String
    Description: |-
      The billing method of the cluster. Valid values:
      Postpaid: pay-as-you-go
      Prepaid: subscription
    AllowedValues:
      - Postpaid
      - Prepaid
  CreationCategory:
    Type: String
    Description: Cluster series. The value could be Normal (standard version).
  DBNodeClass:
    Type: String
    Description: >-
      The node specifications of the cluster. For more information, see
      Specifications and pricing.
  CreationOption:
    Type: String
    Description: >-
      The method for creating an ApsaraDB for POLARDB cluster. Valid values:

      Normal: creates an ApsaraDB for POLARDB cluster.

      CloneFromPolarDB: clones data from an existing ApsaraDB for POLARDB
      cluster to a new ApsaraDB for POLARDB cluster.

      CloneFromRDS: clones data from an existing ApsaraDB for RDS instance to a
      new ApsaraDB

      for POLARDB cluster.

      MigrationFromRDS: migrates data from an existing ApsaraDB for RDS instance
      to a new ApsaraDB for POLARDB cluster. The created ApsaraDB for POLARDB
      cluster is in read-only mode and has binary logs enabled by default.

      CreateGdnStandby: Create a secondary cluster.

      Default value: Normal.

      Note:

      When DBType is MySQL and DBVersion is 5.6, this parameter can be specified
      as CloneFromRDS or MigrationFromRDS.

      When DBType is MySQL and DBVersion is 8.0, this parameter can be specified
      as CreateGdnStandby.
    AllowedValues:
      - CloneFromPolarDB
      - CloneFromRDS
      - MigrationFromRDS
      - Normal
      - CreateGdnStandby
    Default: Normal
  DBVersion:
    Type: String
    Description: |-
      The version of the database. Valid values:
      MySQL: 5.6, 5.7 or 8.0
      PostgreSQL: 11
      Oracle: 11
  ClusterNetworkType:
    Type: String
    Description: >-
      The network type of the cluster. Currently, only VPC is supported. Default
      value: VPC.
    AllowedValues:
      - VPC
    Default: VPC
  VpcId:
    Type: String
    Description: The ID of the VPC to connect to.
  SecurityIPList:
    Type: String
    Description: The whitelist of the Apsara PolarDB cluster.
  MaintainTime:
    Type: String
    Description: >-
      The maintainable time of the cluster:

      Format: HH: mmZ- HH: mmZ.

      Example: 16:00Z-17:00Z, which means 0 to 1 (UTC+08:00) for routine
      maintenance.
  LowerCaseTableNames:
    Type: Number
    Description: |-
      Whether the table name is case sensitive, the value range is as follows:
      1: Not case sensitive0: case sensitive
      The default value is 1.
      Note: This parameter takes effect only when the value of DBType is MySQL.
    AllowedValues:
      - 0
      - 1
Resources:
  DBCluster:
    Type: 'ALIYUN::POLARDB::DBCluster'
    Properties:
      AutoRenewPeriod:
        Ref: AutoRenewPeriod
      DefaultTimeZone:
        Ref: DefaultTimeZone
      TDEStatus:
        Ref: TDEStatus
      CloneDataPoint:
        Ref: CloneDataPoint
      GDNId:
        Ref: GDNId
      ResourceGroupId:
        Ref: ResourceGroupId
      ZoneId:
        Ref: ZoneId
      VSwitchId:
        Ref: VSwitchId
      BackupRetentionPolicyOnClusterDeletion:
        Ref: BackupRetentionPolicyOnClusterDeletion
      RenewalStatus:
        Ref: RenewalStatus
      DBClusterDescription:
        Ref: DBClusterDescription
      Period:
        Ref: Period
      SourceResourceId:
        Ref: SourceResourceId
      DBType:
        Ref: DBType
      PayType:
        Ref: PayType
      CreationCategory:
        Ref: CreationCategory
      DBNodeClass:
        Ref: DBNodeClass
      CreationOption:
        Ref: CreationOption
      DBVersion:
        Ref: DBVersion
      ClusterNetworkType:
        Ref: ClusterNetworkType
      VpcId:
        Ref: VpcId
      SecurityIPList:
        Ref: SecurityIPList
      MaintainTime:
        Ref: MaintainTime
      LowerCaseTableNames:
        Ref: LowerCaseTableNames
Outputs:
  DBNodeIds:
    Description: The ID list of cluster nodes.
    Value:
      'Fn::GetAtt':
        - DBCluster
        - DBNodeIds
  PrimaryConnectionString:
    Description: The primary connection string of the db cluster.
    Value:
      'Fn::GetAtt':
        - DBCluster
        - PrimaryConnectionString
  ClusterConnectionString:
    Description: The cluster connection string of the db cluster.
    Value:
      'Fn::GetAtt':
        - DBCluster
        - ClusterConnectionString
  ClusterEndpointId:
    Description: The cluster endpoint ID of the db cluster.
    Value:
      'Fn::GetAtt':
        - DBCluster
        - ClusterEndpointId
  DBClusterId:
    Description: The ID of the ApsaraDB for POLARDB cluster.
    Value:
      'Fn::GetAtt':
        - DBCluster
        - DBClusterId
  CustomEndpointIds:
    Description: The custom endpoint IDs of the db cluster.
    Value:
      'Fn::GetAtt':
        - DBCluster
        - CustomEndpointIds
  PrimaryEndpointId:
    Description: The primary endpoint ID of the db cluster.
    Value:
      'Fn::GetAtt':
        - DBCluster
        - PrimaryEndpointId
  OrderId:
    Description: The Order ID.
    Value:
      'Fn::GetAtt':
        - DBCluster
        - OrderId
  CustomConnectionStrings:
    Description: The custom connection strings of the db cluster.
    Value:
      'Fn::GetAtt':
        - DBCluster
        - CustomConnectionStrings
```


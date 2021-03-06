# ALIYUN::ApiGateway::Group

ALIYUN::ApiGateway::Group is used to create an API group.

## Syntax

```
{
  "Type": "ALIYUN::ApiGateway::Group",
  "Properties": {
    "GroupName": String,
    "Description": String,
    "InstanceId": String,
    "PassthroughHeaders": String,
    "Tags": List
  }
}   
```

## Properties

|Property|Type|Required|Editable|Description|Constraint|
|--------|----|--------|--------|-----------|----------|
|GroupName|String|Yes|Yes|The name of the API group.|The name must be unique. The name must be 4 to 50 characters in length. The name must start with a letter and can contain letters, digits, and underscores \(\_\). |
|Description|String|No|Yes|The description of the API group.|The description can be up to 180 characters in length.|
|InstanceId|String|No|No|The instance type of the API Gateway.|Valid values: -   api-shared-vpc-001: VPC.
-   api-shared-classic-001: classic network. |
|PassthroughHeaders|String|No|No|Configure the pass-through mode.|Set the value to host.|
|Tags|List|No|Yes|Tags of the API.|You can set up to 20 tags for an API. For more information, see [Tags properties](#section_g6e_w2h_g40). |

## Tags syntax

```
"Tags": [
  {
    "Value": String,
    "Key": String
  }
]  
```

## Tags properties

|Property|Type|Required|Editable|Description|Constraint|
|--------|----|--------|--------|-----------|----------|
|Key|String|Yes|No|The tag key.|The tag key can be up to 128 characters in length and cannot start with `acs:` or `aliyun`. It cannot contain `http://` or `https://`.|
|Value|String|No|No|The tag value.|The tag value can be up to 128 characters in length and cannot start with `acs:` or `aliyun`. It cannot contain `http://` or `https://`.|

## Response parameters

Fn::GetAtt

-   SubDomain: the second-level domain name that the system binds to the group. The domain name is used to test API calls.
-   GroupId: the ID of the API group. This ID is a globally unique identifier \(GUID\) generated by the system.
-   Tags: tags of the API group.

## Examples

`JSON` format

```
{
  "ROSTemplateFormatVersion": "2015-09-01",
  "Parameters": {
    "GroupName": {
      "Type": "String",
      "Description": "The name of the Group.Need [4, 50] Chinese\\English\\Number characters or \"_\",and should start with Chinese/English character."
    },
    "Description": {
      "Type": "String",
      "Description": "Description of the Group, less than 180 characters."
    },
    "InstanceId": {
      "Type": "String",
      "Description": "API gateway instance ID. For example, \"api-shared-vpc-001\" means vpc instance, while \"api-shared-classic-001\" means classic instance."
    },
    "Tags": {
      "Type": "Json",
      "Description": "Tags to attach to group. Max support 20 tags to add during create group. Each tag with two properties Key and Value, and Key is required.",
      "MaxLength": 20
    }
  },
  "Resources": {
    "Group": {
      "Type": "ALIYUN::ApiGateway::Group",
      "Properties": {
        "GroupName": {
          "Ref": "GroupName"
        },
        "Description": {
          "Ref": "Description"
        },
        "InstanceId": {
          "Ref": "InstanceId"
        },
        "Tags": {
          "Ref": "Tags"
        }
      }
    }
  },
  "Outputs": {
    "SubDomain": {
      "Description": "The sub domain assigned to the Group by the system",
      "Value": {
        "Fn::GetAtt": [
          "Group",
          "SubDomain"
        ]
      }
    },
    "Tags": {
      "Description": "Tags of app",
      "Value": {
        "Fn::GetAtt": [
          "Group",
          "Tags"
        ]
      }
    },
    "GroupId": {
      "Description": "The id of the created Group resource",
      "Value": {
        "Fn::GetAtt": [
          "Group",
          "GroupId"
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
  GroupName:
    Type: String
    Description: >-
      The name of the Group.Need [4, 50] Chinese\English\Number characters or
      "_",and should start with Chinese/English character.
  Description:
    Type: String
    Description: 'Description of the Group, less than 180 characters.'
  InstanceId:
    Type: String
    Description: >-
      API gateway instance ID. For example, "api-shared-vpc-001" means vpc
      instance, while "api-shared-classic-001" means classic instance.
  Tags:
    Type: Json
    Description: >-
      Tags to attach to group. Max support 20 tags to add during create group.
      Each tag with two properties Key and Value, and Key is required.
    MaxLength: 20
Resources:
  Group:
    Type: 'ALIYUN::ApiGateway::Group'
    Properties:
      GroupName:
        Ref: GroupName
      Description:
        Ref: Description
      InstanceId:
        Ref: InstanceId
      Tags:
        Ref: Tags
Outputs:
  SubDomain:
    Description: The sub domain assigned to the Group by the system
    Value:
      'Fn::GetAtt':
        - Group
        - SubDomain
  Tags:
    Description: Tags of app
    Value:
      'Fn::GetAtt':
        - Group
        - Tags
  GroupId:
    Description: The id of the created Group resource
    Value:
      'Fn::GetAtt':
        - Group
        - GroupId
```


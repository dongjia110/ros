# PreviewStack {#doc_api_ROS_PreviewStack .reference}

预览指定模板将要创建的资源栈信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=ROS&api=PreviewStack&type=RPC&version=2019-09-10)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|PreviewStack|系统规定参数。取值：PreviewStack。

 |
|RegionId|String|是|cn-beijing|堆栈所属的地域ID。您可以调用[DescribeRegions](https://help.aliyun.com/document_detail/131035.htm)查看最新的阿里云地域列表。

 |
|StackName|String|是|MyStack|堆栈名称。资源栈名称可以包含数字、字母（大小写敏感）、连字符、下划线。必须以数字或字母开头，且长度不超过255个字符。

 |
|TimeoutInMinutes|Long|是|10|堆栈的超时时间，以分钟为单位。

 默认值为 10。

 |
|Parameters.N.ParameterValue|String|否|ecs.cm4.6xlarge|参数的值。

 N最大值为200。

 |
|Parameters.N.ParameterKey|String|否|InstanceType|参数的名称。 如果未指定特定参数的名称和值，则ROS将使用模板中指定的默认值。

 N最大值为200。

 |
|DisableRollback|Boolean|否|false|当创建堆栈失败时，是否禁用回滚策略，默认为false。

 -   true 表示禁用回滚，即在创建堆栈失败时不会进行回滚；
-   false 表示不禁用回滚，即在创建堆栈失败时会进行回滚。

 |
|TemplateBody|String|否|\{ "ROSTemplateFormatVersion": "2015-09-01" \}|包含模板体的结构，最小长度为1个字节，最大长度为51,200个字节。

 您必须指定TemplateBody或TemplateURL参数，但不能同时指定两者。

 |
|StackPolicyURL|String|否|oss://ros-stack-policy/demo|包含堆栈策略的文件的位置。 URL必须指向位于Web服务器（http，https）中的策略（最大大小：16384字节）,或与堆栈在同一地域的阿里云OSS存储桶（例如oss：// ros-stack-policy / demo）。URL最大长度为1350字节。

 您可以指定StackPolicyBody或StackPolicyURL参数，但不能同时指定两者。

 |
|StackPolicyBody|String|否|\{"Statement": \[\{"Action": "Update:\*", "Resource": "\*", "Effect": "Allow", "Principal": "\*"\}\]\}|包含堆栈策略主体的结构，最小长度为1个字节，最大长度为16384个字节。

 您可以指定StackPolicyBody或StackPolicyURL参数，但不能同时指定两者。

 |
|TemplateURL|String|否|oss://ros-template/demo|包含模板主体的文件的位置。 URL必须指向位于http Web服务器（http，https），或与堆栈在同一地域的OSS存储桶（例如oss：// ros-template / demo）中的模板（最大大小：524288字节）。

 您必须指定TemplateBody或TemplateURL参数，但不能同时指定两者。

 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求的幂等性。 该值由客户端生成，并且必须是全局唯一的。 仅允许使用字母数字字符（区分大小写），连字符和下划线。 它最多可包含64个字符。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Stack|Map|见返回实例中的Stack字段|堆栈信息。

 |
|RequestId|String|B288A0BE-D927-4888-B0F7-B35EF84B6E6F|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=PreviewStack
&RegionId=cn-beijing
&Parameters.1.ParameterValue=ecs.cm4.6xlarge
&Parameters.1.ParameterKey=InstanceType
&StackName=MyStack
&TimeoutInMinutes=10
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<PreviewStackResponse>
      <Stacks>
            <Description>No description</Description>
            <DisableRollback>true</DisableRollback>
            <Parameters>
                  <Parameter>
                        <ParameterKey>UpdateVersion</ParameterKey>
                        <ParameterValue>1</ParameterValue>
                  </Parameter>
            </Parameters>
            <RegionId>cn-beijing</RegionId>
            <Resources>
                  <Resource>
                        <Description></Description>
                        <LogicalResourceId>WaitConditionHandle</LogicalResourceId>
                        <Properties>
                              <Count>-1</Count>
                              <Mode>Full</Mode>
                              <UpdateVersion>1</UpdateVersion>
                        </Properties>
                        <RequiredBy></RequiredBy>
                        <ResourceType>ALIYUN::ROS::WaitConditionHandle</ResourceType>
                  </Resource>
                  <Resource>
                        <Description></Description>
                        <LogicalResourceId>nested</LogicalResourceId>
                        <Properties>
                              <Parameters></Parameters>
                              <TemplateURL>oss://nested-stack/simple/nested_demo</TemplateURL>
                              <TimeoutMins>16</TimeoutMins>
                        </Properties>
                        <RequiredBy></RequiredBy>
                        <ResourceType>ALIYUN::ROS::Stack</ResourceType>
                        <Stack>
                              <Description>No description</Description>
                              <DisableRollback>true</DisableRollback>
                              <Parameters>
                                    <Parameter>
                                          <ParameterKey>ALIYUN::AccountId</ParameterKey>
                                          <ParameterValue>16xxxxxxxx1</ParameterValue>
                                          <ParameterKey>ALIYUN::NoValue</ParameterKey>
                                          <ParameterValue>None</ParameterValue>
                                          <ParameterKey>ALIYUN::Region</ParameterKey>
                                          <ParameterValue>cn-beijing</ParameterValue>
                                          <ParameterKey>ALIYUN::StackId</ParameterKey>
                                          <ParameterValue>None</ParameterValue>
                                          <ParameterKey>ALIYUN::StackName</ParameterKey>
                                          <ParameterValue>test-preview-stack-complex-nested</ParameterValue>
                                    </Parameter>
                              </Parameters>
                              <RegionId>cn-beijing</RegionId>
                              <Resources>
                                    <Resource>
                                          <Description></Description>
                                          <LogicalResourceId>WaitConditionHandle</LogicalResourceId>
                                          <Properties>
                                                <Count>-1</Count>
                                                <Mode>Full</Mode>
                                                <UpdateVersion>1</UpdateVersion>
                                          </Properties>
                                          <RequiredBy></RequiredBy>
                                          <ResourceType>ALIYUN::ROS::WaitConditionHandle</ResourceType>
                                    </Resource>
                              </Resources>
                              <StackName>test-preview-stack-complex-nested</StackName>
                              <StackPolicyBody>
                                    <Statement>
                                          <Statement>
                                                <Action>Update:*</Action>
                                                <Effect>Allow</Effect>
                                                <Principal>*</Principal>
                                                <Resource>*</Resource>
                                          </Statement>
                                    </Statement>
                              </StackPolicyBody>
                              <TemplateDescription>No description</TemplateDescription>
                              <TimeoutInMinutes>12</TimeoutInMinutes>
                        </Stack>
                  </Resource>
            </Resources>
            <StackName>test-preview-stack-complex</StackName>
            <StackPolicyBody>
                  <Statement>
                        <Statement>
                              <Action>Update:*</Action>
                              <Effect>Allow</Effect>
                              <Principal>*</Principal>
                              <Resource>*</Resource>
                        </Statement>
                  </Statement>
            </StackPolicyBody>
            <TemplateDescription>No description</TemplateDescription>
            <TimeoutInMinutes>10</TimeoutInMinutes>
      </Stacks>
      <RequestId>B288A0BE-D927-4888-B0F7-B35EF84B6E6F</RequestId>    
</PreviewStackResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Stack":{
		"Parameters":[
			{
				"ParameterValue":"1",
				"ParameterKey":"UpdateVersion"
			}
		],
		"TimeoutInMinutes":10,
		"TemplateDescription":"No description",
		"Description":"No description",
		"StackPolicyBody":{
			"Statement":[
				{
					"Resource":"*",
					"Principal":"*",
					"Action":"Update:*",
					"Effect":"Allow"
				},
				{
					"Resource":"LogicalResourceId/apple1",
					"Principal":"*",
					"Action":"Update:*",
					"Effect":"Deny"
				}
			]
		},
		"RegionId":"cn-beijing",
		"DisableRollback":true,
		"StackName":"test-preview-stack-complex",
		"Resources":[
			{
				"RequiredBy":[],
				"LogicalResourceId":"WaitConditionHandle",
				"Description":"",
				"ResourceType":"ALIYUN::ROS::WaitConditionHandle",
				"Properties":{
					"UpdateVersion":1,
					"Count":-1,
					"Mode":"Full"
				}
			},
			{
				"Stack":{
					"Parameters":[
						{
							"ParameterValue":"16xxxxxxxx1",
							"ParameterKey":"ALIYUN::AccountId"
						},
						{
							"ParameterValue":"None",
							"ParameterKey":"ALIYUN::NoValue"
						},
						{
							"ParameterValue":"cn-beijing",
							"ParameterKey":"ALIYUN::Region"
						},
						{
							"ParameterValue":"None",
							"ParameterKey":"ALIYUN::StackId"
						},
						{
							"ParameterValue":"test-preview-stack-complex-nested",
							"ParameterKey":"ALIYUN::StackName"
						}
					],
					"TimeoutInMinutes":12,
					"TemplateDescription":"No description",
					"Description":"No description",
					"StackPolicyBody":{
						"Statement":[
							{
								"Resource":"*",
								"Principal":"*",
								"Action":"Update:*",
								"Effect":"Allow"
							},
							{
								"Resource":"LogicalResourceId/apple1",
								"Principal":"*",
								"Action":"Update:*",
								"Effect":"Deny"
							}
						]
					},
					"RegionId":"cn-beijing",
					"DisableRollback":true,
					"StackName":"test-preview-stack-complex-nested",
					"Resources":[
						{
							"RequiredBy":[],
							"LogicalResourceId":"WaitConditionHandle",
							"Description":"",
							"ResourceType":"ALIYUN::ROS::WaitConditionHandle",
							"Properties":{
								"UpdateVersion":1,
								"Count":-1,
								"Mode":"Full"
							}
						}
					]
				},
				"RequiredBy":[],
				"LogicalResourceId":"nested",
				"Description":"",
				"ResourceType":"ALIYUN::ROS::Stack",
				"Properties":{
					"TemplateURL":"oss://nested-stack/simple/nested_demo",
					"TimeoutMins":16
				}
			}
		]
	},
	"RequestId":"B288A0BE-D927-4888-B0F7-B35EF84B6E6F"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/ROS)查看更多错误码。


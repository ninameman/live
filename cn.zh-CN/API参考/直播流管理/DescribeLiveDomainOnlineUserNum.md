# DescribeLiveDomainOnlineUserNum {#doc_api_live_DescribeLiveDomainOnlineUserNum .reference}

调用DescribeLiveDomainOnlineUserNum查询域名下所有流某分钟的在线人数信息。

**说明：** 建议使用本接口替换原有的**DescribeLiveStreamOnlineUserNum**接口。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveDomainOnlineUserNum&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveDomainOnlineUserNum|系统规定参数，取值：**DescribeLiveDomainOnlineUserNum**。

 |
|DomainName|String|是|example.com|您的播流域名。

 |
|QueryTime|String|否|2018-12-27T13:09:21Z|查询的时间UTC 格式，精确到秒。

 |
|RegionId|String|否|cn-hangzhou|地域ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|OnlineUserInfo| | |流的信息。

 |
|Infos| | |流统计信息

 |
|TranscodeTemplate|String|origin|转码模板名，origin是原始流

 |
|UserNumber|Long|1|转码流或原始流的人数

 |
|StreamName|String|rtmp://example.com/test/livestream\_3\_1|流名称

 |
|RequestId|String|3A3A8C3D-F8B2-4FBF-9319-771A11B855FA|请求ID。

 |
|StreamCount|Integer|1|流数

 |
|UserCount|Integer|1|查询时间下域名的所有在线人数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=DescribeLiveDomainOnlineUserNum
&DomainName=example.com&QueryTime=2018-12-27T13:09:21Z
&<公共请求参数>

```

正常返回示例

`JSON` 格式

``` {#json_return_success_demo}
{
	"UserCount":1,
	"OnlineUserInfo":{
		"LiveStreamOnlineUserNumInfo":[
			{
				"StreamName":"rtmp://example.com/test/livestream_3_1",
				"Infos":{
					"Info":[
						{
							"TranscodeTemplate":"origin",
							"UserNumber":1
						}
					]
				}
			}
		]
	},
	"RequestId":"3A3A8C3D-F8B2-4FBF-9319-771A11B855FA",
	"StreamCount":1
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


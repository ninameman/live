# DescribeLiveRecordVodConfigs {#doc_api_live_DescribeLiveRecordVodConfigs .reference}

调用DescribeLiveRecordVodConfigs查询直转点配置列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveRecordVodConfigs&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveRecordVodConfigs|系统规定参数。取值：**DescribeLiveRecordVodConfigs**。

 |
|DomainName|String|是|play.aliyunlive.com|您的加速域名。

 |
|AppName|String|否|app|直播流所属应用名称。

 |
|PageNum|Long|否|1|分页的页码。默认值：**1**。

 |
|PageSize|Long|否|10|每页大小。默认值为**10**。

 -   取值范围：5~100

 |
|RegionId|String|否|cn-shanghai|区域。

 |
|StreamName|String|否|stream|直播流名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|LiveRecordVodConfigs| | |配置信息列表。

 |
|AppName|String|app|流所属应用名称。

 |
|AutoCompose|String|ON|是否开启自动合并。

 -   **ON**：开启
-   **OFF**：关闭

 |
|ComposeVodTranscodeGroupId|String|dadfcaaddexxxx|自动合并点播转码模板组ID。

 **说明：** 如果开启了自动合成，则该字段必填。

 |
|CreateTime|String|2015-12-01T17:37:00Z|创建时间。

 UTC格式：2015-12-01T17:37:00Z。

 |
|CycleDuration|Integer|360|周期录制时长，单位：秒。默认值为**3600**，取值范围：**300~21600**。

 |
|DomainName|String|play.aliyunlive.com|流所属加速域名。

 |
|StreamName|String|stream|直播流名称。

 |
|VodTranscodeGroupId|String|e2d796d3bb5fd8049d32bff62f940711|点播转码组模板ID。

 |
|PageNum|Integer|1|分页页码。

 |
|PageSize|Integer|1|分页大小。

 |
|RequestId|String|创建房间时输入的主播ID，最大长度32位，合法字符：\[a-z, A-Z, 0-9, -\]|请求ID。

 |
|Total|String|100|总页数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeLiveRecordVodConfigs
&DomainName=play.aliyunlive.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveRecordVodConfigsResponse>
  <LiveRecordVodConfigs>
		    <LiveRecordVodConfig>
			      <AppName>aliyuntest</AppName>
			      <CycleDuration>300</CycleDuration>
			      <DomainName>xxxxx</DomainName>
			      <VodTranscodeGroupId>xxxx</VodTranscodeGroupId>
			      <AutoCompose>OFF</AutoCompose>
			      <ComposeVodTranscodeGroupId>xxx</ComposeVodTranscodeGroupId>
			      <CreateTime>2018-10-11T12:12:11Z</CreateTime>
		    </LiveRecordVodConfig>
	  </LiveRecordVodConfigs>
	  <PageNum>1</PageNum>
	  <PageSize>1</PageSize>
	  <RequestId>5056369B-D337-499E-B8B7-B761BD37B08A</RequestId>
	  <Total>100</Total>
</DescribeLiveRecordVodConfigsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageSize":1,
	"RequestId":"5056369B-D337-499E-B8B7-B761BD37B08A",
	"LiveRecordVodConfigs":{
		"LiveRecordVodConfig":[
			{
				"ComposeVodTranscodeGroupId":"xxx",
				"AutoCompose":"OFF",
				"CreateTime":"2018-10-11T12:12:11Z",
				"CycleDuration":300,
				"DomainName":"xxxxx",
				"AppName":"aliyuntest",
				"VodTranscodeGroupId":"xxxx"
			}
		]
	},
	"PageNum":1,
	"Total":100
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


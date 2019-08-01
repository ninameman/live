# DescribeLivePullStreamConfig {#doc_api_live_DescribeLivePullStreamConfig .reference}

调用DescribeLivePullStreamConfig查询域名下拉流配置信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLivePullStreamConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLivePullStreamConfig|系统规定参数，取值：**DescribeLivePullStreamConfig**。

 |
|DomainName|String|是|play.yourdomain.com|您的拉流域名。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|LiveAppRecordList| | |拉流配置。

 |
|DomainName|String|play.yourdomain.com|流所属拉流域名。

 |
|AppName|String|AppName|直播流所属应用名称。

 |
|StreamName|String|StreamName|流名称。

 |
|SourceUrl|String|play.yourdomain.com|拉流源站。

 |
|StartTime|String|2016-05-15T01:30:00Z|开始时间。

 |
|EndTime|String|2016-05-20T01:33:00Z|结束时间。

 |
|RequestId|String|A3136B58-5876-4168-83CA-B562781981A0|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=DescribeLivePullStreamConfig
&DomainName=play.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLivePullStreamConfigResponse>
	  <LiveAppRecordList>
		    <LiveAppRecord>
			      <AppName>xxxx</AppName>
			      <DomainName>live.aliyunlive.com</DomainName>
			      <EndTime>2016-05-20T01:33:00Z</EndTime>
			      <SourceUrl>http://test</SourceUrl>
			      <StartTime>2016-05-15T01:30:00Z</StartTime>
			      <StreamName>xxxxxx</StreamName>
		    </LiveAppRecord>
	  </LiveAppRecordList>
	  <RequestId>A3136B58-5876-4168-83CA-B562781981A0</RequestId>
</DescribeLivePullStreamConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"LiveAppRecordList":{
		"LiveAppRecord":[
			{
				"StreamName":"xxxxxx",
				"SourceUrl":"http://test",
				"DomainName":"live.aliyunlive.com",
				"EndTime":"2016-05-20T01:33:00Z",
				"AppName":"xxxx",
				"StartTime":"2016-05-15T01:30:00Z"
			}
		]
	},
	"RequestId":"A3136B58-5876-4168-83CA-B562781981A0"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


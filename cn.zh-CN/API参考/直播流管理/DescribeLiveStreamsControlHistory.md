# DescribeLiveStreamsControlHistory {#doc_api_live_DescribeLiveStreamsControlHistory .reference}

调用DescribeLiveStreamsControlHistory获取某个域名或应用下的直播流操作记录。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveStreamsControlHistory&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveStreamsControlHistory|系统规定参数，取值：**DescribeLiveStreamsControlHistory**。

 |
|DomainName|String|是|play.yourdomain.com|您的直播加速域名。

 |
|EndTime|String|是|2017-12-22T08:00:00Z|查询结束时间。UTC格式：2015-12-01T17:37:00Z。

 EndTime和StartTime之间的间隔不能超过30天。

 |
|StartTime|String|是|2017-12-21T08:00:00Z|查询开始时间。UTC格式：2015-12-01T17:37:00Z。

 |
|AppName|String|否|testApp|直播流所属应用名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|ControlInfo| | |直播流的操作记录。

 |
|StreamName|String|StreamName|流的名字。

 |
|ClientIP|String|10.207.197.201|用户端的IP地址。

 |
|Action|String|DescribeLiveStreamsControlHistory|执行的操作名称。

 |
|TimeStamp|String|2015-12-01T16:36:18Z|操作执行的时间。

 |
|RequestId|String|9C31856F-386D-4DB3-BE79-A0AA493D702A|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeLiveStreamsControlHistory
&DomainName=play.yourdomain.com
&EndTime=2017-12-22T08:00:00Z
&StartTime=2017-12-21T08:00:00Z
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveStreamsControlHistoryResponse>
	  <ControlInfo>
		    <LiveStreamControlInfo>
			      <Action>forbid</Action>
			      <ClientIP>10.207.197.201</ClientIP>
			      <StreamName>test101.aliyunlive.com/diaoliang/dd</StreamName>
			      <TimeStamp>2015-12-01T16:36:18Z</TimeStamp>
		    </LiveStreamControlInfo>
	  </ControlInfo>
	  <RequestId>9C31856F-386D-4DB3-BE79-A0AA493D702A</RequestId>
</DescribeLiveStreamsControlHistoryResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"ControlInfo":{
		"LiveStreamControlInfo":[
			{
				"TimeStamp":"2015-12-01T16:36:18Z",
				"Action":"forbid",
				"StreamName":"test101.aliyunlive.com/diaoliang/dd",
				"ClientIP":"10.207.197.201"
			}
		]
	},
	"RequestId":"9C31856F-386D-4DB3-BE79-A0AA493D702A"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidStartTime.Malformed|Specified parameter StartTime is not valid.|StartTime参数错误，请您确认该StartTime参数是否正确。|
|400|InvalidEndTime.Malformed|Specified parameter EndTime is not valid.|结束时间错误，请您确认结束时间是否正确。|
|400|InvalidEndTime.Mismatch|Specified end time does not math the specified start time.|结束时间与开始时间不匹配，请您确认时间的匹配度。|

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


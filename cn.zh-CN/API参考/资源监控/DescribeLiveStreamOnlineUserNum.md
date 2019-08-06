# DescribeLiveStreamOnlineUserNum {#doc_api_live_DescribeLiveStreamOnlineUserNum .reference}

调用DescribeLiveStreamOnlineUserNum查询直播流实时在线人数。

整体数据延时**2-5**分钟。此接口仅支持**RTMP**和**FLV**流人数统计，如需**HLS**在线人数统计，请您提交工单申请配置。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveStreamOnlineUserNum&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveStreamOnlineUserNum|系统规定参数。取值：**DescribeLiveStreamOnlineUserNum**。

 |
|DomainName|String|是|www.yourdomain.com|您的加速域名。

 |
|AppName|String|否|testApp|直播流所属应用名称。

 |
|EndTime|String|否|2017-12-21T08:00:00Z|结束时间。

 -   UTC格式。
-   StartTime和EndTime时间间隔在7天内。

 |
|StartTime|String|否|2017-12-21T08:00:00Z|开始时间。

 -   UTC格式。
    -   StartTime和EndTime时间间隔在7天内。

 |
|StreamName|String|否|testStream|直播流名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|TotalUserNumber|Long|2|所有流的用户数总和。

 |
|OnlineUserInfo| | |每条直播流的用户数信息。

 |
|StreamUrl|String|rtmp://play.aliyunlive.com/AppName/StreamName|直播流的URL。

 |
|UserNumber|Long|2|直播流的在线人数。

 |
|Time|String|2015-12-01T17:37:00Z|统计时刻。

 UTC时间。格式：`2015-12-01T17:37:00Z`。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://live.aliyuncs.com/?Action=DescribeLiveStreamOnlineUserNum
&DomainName=www.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveStreamOnlineUserNumResponse>
	  <OnlineUserInfo>
		    <LiveStreamOnlineUserNumInfo>
			      <StreamUrl>rtmp://example.com/live/example</StreamUrl>
			      <UserNumber>2</UserNumber>
		    </LiveStreamOnlineUserNumInfo>
		    <LiveStreamOnlineUserNumInfo>
			      <StreamUrl>rtmp://example.com/live/example1</StreamUrl>
			      <UserNumber>5</UserNumber>
		    </LiveStreamOnlineUserNumInfo>
	  </OnlineUserInfo>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <TotalUserNumber>7</TotalUserNumber>
</DescribeLiveStreamOnlineUserNumResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"TotalUserNumber":7,
	"OnlineUserInfo":{
		"LiveStreamOnlineUserNumInfo":[
			{
				"StreamUrl":"rtmp://example.com/live/example",
				"UserNumber":2
			},
			{
				"StreamUrl":"rtmp://example.com/live/example1",
				"UserNumber":5
			}
		]
	},
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


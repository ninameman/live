# DescribeLiveStreamHistoryUserNum {#doc_api_live_DescribeLiveStreamHistoryUserNum .reference}

调用DescribeLiveStreamHistoryUserNum查询直播流历史在线人数。

整体数据延时**2-5**分钟。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveStreamHistoryUserNum&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveStreamHistoryUserNum|系统规定参数。取值：**DescribeLiveStreamHistoryUserNum**。

 |
|AppName|String|是|testApp|直播流所属应用名称。

 |
|DomainName|String|是|www.yourdomain.com|您的域名。

 |
|EndTime|String|是|2017-12-22T08:00:00Z|结束时间。

 -   UTC格式。
-   StartTime和EndTime时间间隔在一天内，且EndTime不超过当前时间。

 |
|StartTime|String|是|2017-12-21T08:00:00Z|开始时间。

 -   UTC格式。
-   StartTime和EndTime时间间隔在一天内。

 |
|StreamName|String|是|testStream|直播流名。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F5FF8|请求ID。

 |
|LiveStreamUserNumInfos| | |直播流历史在线人数信息。

 |
|UserNum|String|1|人数。

 |
|StreamTime|String|2017-10-20T06:20:00Z|流时间，UTC格式。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=DescribeLiveStreamHistoryUserNum
&AppName=testApp
&DomainName=www.yourdomain.com
&EndTime=2017-12-22T08:00:00Z
&StartTime=2017-12-21T08:00:00Z
&StreamName=testStream
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveStreamHistoryUserNumResponse>
	  <LiveStreamUserNumInfos>
		    <LiveStreamUserNumInfo>
			      <StreamTime>2017-10-20T06:20:00Z</StreamTime>
			      <UserNum>0</UserNum>
		    </LiveStreamUserNumInfo>
		    <LiveStreamUserNumInfo>
			      <StreamTime>2017-10-20T06:19:00Z</StreamTime>
			      <UserNum>0</UserNum>
		    </LiveStreamUserNumInfo>
		    <LiveStreamUserNumInfo>
			      <StreamTime>2017-10-20T06:18:00Z</StreamTime>
			      <UserNum>15</UserNum>
		    </LiveStreamUserNumInfo>
		    <LiveStreamUserNumInfo>
			      <StreamTime>2017-10-20T06:17:00Z</StreamTime>
			      <UserNum>0</UserNum>
		    </LiveStreamUserNumInfo>
		    <LiveStreamUserNumInfo>
			      <StreamTime>2017-10-20T06:16:00Z</StreamTime>
			      <UserNum>0</UserNum>
		    </LiveStreamUserNumInfo>
		    <LiveStreamUserNumInfo>
			      <StreamTime>2017-10-20T06:15:00Z</StreamTime>
			      <UserNum>6</UserNum>
		    </LiveStreamUserNumInfo>
		    <LiveStreamUserNumInfo>
			      <StreamTime>2017-10-20T06:14:00Z</StreamTime>
			      <UserNum>0</UserNum>
		    </LiveStreamUserNumInfo>
	  </LiveStreamUserNumInfos>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F5FF8</RequestId>
</DescribeLiveStreamHistoryUserNumResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"LiveStreamUserNumInfos":{
		"LiveStreamUserNumInfo":[
			{
				"UserNum":0,
				"StreamTime":"2017-10-20T06:20:00Z"
			},
			{
				"UserNum":0,
				"StreamTime":"2017-10-20T06:19:00Z"
			},
			{
				"UserNum":15,
				"StreamTime":"2017-10-20T06:18:00Z"
			},
			{
				"UserNum":0,
				"StreamTime":"2017-10-20T06:17:00Z"
			},
			{
				"UserNum":0,
				"StreamTime":"2017-10-20T06:16:00Z"
			},
			{
				"UserNum":6,
				"StreamTime":"2017-10-20T06:15:00Z"
			},
			{
				"UserNum":0,
				"StreamTime":"2017-10-20T06:14:00Z"
			}
		]
	},
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F5FF8"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidStartTime.Malformed|Specified StartTime is malformed.|StartTime参数错误，请您确认该StartTime参数是否正确。|
|400|InvalidEndTime.Malformed|Specified EndTime is malformed.|结束时间错误，请您确认结束时间是否正确。|

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


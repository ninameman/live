# DescribeLiveStreamRecordContent {#doc_api_live_DescribeLiveStreamRecordContent .reference}

调用DescribeLiveStreamRecordContent查询录制内容。

查询某条流的录制内容包含的时间段，即这条流在哪些时间段存在录制内容，可用于录制时间轴展示。注意查询时间是UTC，并且只能查询6个月内的记录。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveStreamRecordContent&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveStreamRecordContent|系统规定参数。取值：**DescribeLiveStreamRecordContent**。

 |
|AppName|String|是|testApp|直播流所属应用名称。

 |
|DomainName|String|是|www.yourdomain.com|您的加速域名。

 |
|EndTime|String|是|2017-12-22T08:00:00Z|结束时间。与StartTime的间隔时间不能超过4天。

 格式：UTC时间。

 示例：2015-12-01T17:36:00Z。

 |
|StartTime|String|是|2017-12-21T08:00:00Z|开始时间。

 格式：UTC时间。

 示例：2015-12-01T17:36:00Z。

 |
|StreamName|String|是|testStream|直播流名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RecordContentInfoList| | |录制内容列表。

 |
|OssEndpoint|String|oss-cn-shanghai.aliyuncs.com|OSS endpoint。

 |
|OssBucket|String|test123|OSS存储bucket名称。

 |
|OssObjectPrefix|String|record/\{Date\}/\{UnixTimestamp\}\_\{Sequence\}|OSS存储的录制文件名的规则。

 |
|StartTime|String|2015-12-01T17:36:00Z|开始时间，格式：2015-12-01T17:36:00Z。

 |
|EndTime|String|2015-12-01T17:36:00Z|结束时间，格式：2015-12-01T17:36:00Z。

 |
|Duration|Float|10|录制时长。

 |
|RequestId|String|62136AE6-7793-45ED-B14A-60D19A9486D3|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[live.aliyuncs.com]/?Action=DescribeLiveStreamRecordContent
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
<DescribeLiveStreamRecordContentResponse>
	  <RecordContentInfoList>
		    <RecordContentInfo>
			      <Duration>14638</Duration>
			      <EndTime>2016-05-25T09:41:09Z</EndTime>
			      <OssBucket>livevideo-test</OssBucket>
			      <OssEndpoint>oss-cn-hangzhou.aliyuncs.com</OssEndpoint>
			      <OssObjectPrefix>record/{Date}/{UnixTimestamp}_{Sequence}</OssObjectPrefix>
			      <StartTime>2016-05-25T05:37:11Z</StartTime>
		    </RecordContentInfo>
	  </RecordContentInfoList>
	  <RequestId>62136AE6-7793-45ED-B14A-60D19A9486D3</RequestId>
</DescribeLiveStreamRecordContentResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"62136AE6-7793-45ED-B14A-60D19A9486D3",
	"RecordContentInfoList":{
		"RecordContentInfo":[
			{
				"Duration":14638.0,
				"OssEndpoint":"oss-cn-hangzhou.aliyuncs.com",
				"EndTime":"2016-05-25T09:41:09Z",
				"StartTime":"2016-05-25T05:37:11Z",
				"OssObjectPrefix":"record/{Date}/{UnixTimestamp}_{Sequence}",
				"OssBucket":"livevideo-test"
			}
		]
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidStartTime.Malformed|Specified StartTime is malformed.|StartTime参数错误，请您确认该StartTime参数是否正确。|
|400|InvalidEndTime.Malformed|Specified EndTime is malformed.|结束时间错误，请您确认结束时间是否正确。|
|400|InvalidEndTime.Mismatch|Specified end time does not math the specified start time.|结束时间与开始时间不匹配，请您确认时间的匹配度。|

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


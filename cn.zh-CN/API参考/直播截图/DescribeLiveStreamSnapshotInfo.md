# DescribeLiveStreamSnapshotInfo {#doc_api_live_DescribeLiveStreamSnapshotInfo .reference}

调用DescribeLiveStreamSnapshotInfo查询一段时间内截图内容。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveStreamSnapshotInfo&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveStreamSnapshotInfo|系统规定参数。取值：**DescribeLiveStreamSnapshotInfo**。

 |
|AppName|String|是|testApp|直播流所属应用名称。

 |
|DomainName|String|是|www.yourdomain.com|您的加速域名。

 |
|EndTime|String|是|2017-12-22T08:00:00Z|结束时间。EndTime和StartTime之间的间隔不能超过**1**天。

 格式：2015-12-01T17:36:00Z。

 |
|StartTime|String|是|2017-12-21T08:00:00Z|开始时间。

 格式：2015-12-01T17:36:00Z。

 |
|StreamName|String|是|testStream|直播流名称。

 |
|Limit|Integer|否|10| 

 一次调用获取的数量。

 -   取值范围：1~100
-   默认值：10

 |
|Order|String|否|asc|排序。取值：

 -   asc（默认值）：升序
-   desc：降序

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|62136AE6-7793-45ED-B14A-60D19A9486D3|请求ID。

 |
|LiveStreamSnapshotInfoList| | |截图内容列表，没有则返回空数组。

 |
|CreateTime|String|2015-12-01T17:36:00Z|截图产生时间。

 格式：2015-12-01T17:36:00Z。

 |
|OssBucket|String|test123|OssBucket的名称。

 |
|OssEndpoint|String|oss-cn-shanghai.aliyuncs.com|OssEndpoint域名。

 |
|OssObject|String|test123|OssObject名称。

 |
|NextStartTime|String|2015-12-01T17:36:00Z|下一个起始时间。

 当此时间范围内的内容超出了limit的数量限制，则返回此参数，表示下一个文件的创建时间，可以将此时间当做StartTime，重新调用此接口获取下一段内容，不传则表示未超出 limit数量。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://live.aliyuncs.com/?Action=DescribeLiveStreamSnapshotInfo
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
<DescribeLiveStreamSnapshotInfoResponse>
	  <LiveStreamSnapshotInfoList>
		    <LiveStreamSnapshotInfo>
			      <CreateTime>2016-05-25T09:41:09Z</CreateTime>
			      <OssBucket>livevideo-test</OssBucket>
			      <OssEndpoint>oss-test.aliyun-inc.com</OssEndpoint>
			      <OssObject>{AppName}/{StreamName}.jpg</OssObject>
		    </LiveStreamSnapshotInfo>
	  </LiveStreamSnapshotInfoList>
	  <NextStartTime>2015-12-01T17:36:00Z</NextStartTime>
	  <RequestId>62136AE6-7793-45ED-B14A-60D19A9486D3</RequestId>
</DescribeLiveStreamSnapshotInfoResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"LiveStreamSnapshotInfoList":{
		"LiveStreamSnapshotInfo":[
			{
				"OssObject":"{AppName}/{StreamName}.jpg",
				"CreateTime":"2016-05-25T09:41:09Z",
				"OssEndpoint":"oss-test.aliyun-inc.com",
				"OssBucket":"livevideo-test"
			}
		]
	},
	"RequestId":"62136AE6-7793-45ED-B14A-60D19A9486D3",
	"NextStartTime":"2015-12-01T17:36:00Z"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidStartTime.Malformed|Specified parameter StartTime is not valid.|StartTime参数错误，请您确认该StartTime参数是否正确。|
|400|InvalidEndTime.Malformed|Specified parameter EndTime is not valid.|结束时间错误，请您确认结束时间是否正确。|
|400|InvalidEndTime.Mismatch|Specified end time does not math the specified start time.|结束时间与开始时间不匹配，请您确认时间的匹配度。|
|400|InvalidStream.NotFound|Speicified stream does not exist.|直播流不存在，请您确认直播流是否正确。|

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


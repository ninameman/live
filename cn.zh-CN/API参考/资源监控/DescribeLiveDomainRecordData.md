# DescribeLiveDomainRecordData {#doc_api_live_DescribeLiveDomainRecordData .reference}

调用DescribeLiveDomainRecordData查询直播域名录制时长数据。

-   支持用户查询单个直播域名在指定时间区段内的每日录制时长数据。
-   每日录制时长数据包括：当日录制总时长和区分录制格式的时长数据列表。
-   支持查询2018/01/01起的数据，数据查询的起止时间跨度最大为90天。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveDomainRecordData&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveDomainRecordData|系统规定参数，取值：**DescribeLiveDomainRecordData**。

 |
|StartTime|String|是|2018-01-01T00:00:00Z|获取数据起始时间点。日期格式按照ISO8601表示法，并使用UTC时间。格式为：`YYYY-MM-DDThh:mm:ssZ`。

 **说明：** 支持查询2018/01/01起的数据，即StartTime≥`2018-01-01T00:00:00Z`。

 |
|EndTime|String|是|2018-01-02T00:00:00Z|获取数据结束时间，需大于起始时间。日期格式按照ISO8601表示法，并使用UTC时间。格式为：`YYYY-MM-DDThh:mm:ssZ`。

 |
|DomainName|String|否|www.example.com|需要查询的直播域名。

 |
|RecordType|String|否|MP4|录制类型，目前支持**TS**、**MP4**、**FLV**三种，不传查询所有类型。

 |
|RegionId|String|否|cn-shanghai|区域。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RecordDataInfos| | |直播录制时长的每日数据统计。

 |
|Date|String|20180202|日期，具体到天。

 |
|Total|Integer|4710|单日录制总时长，单位：秒。

 |
|Detail| | |区分录制格式的录制时长信息。

 |
|FLV|Integer|100|FLV格式录制时长，单位：秒。

 |
|MP4|Integer|230|MP4格式录制时长，单位：秒。

 |
|TS|Integer|456|TS格式录制时长，单位：秒。

 |
|RequestId|String|B955107D-E658-4E77-B913-E0AC3D31693F|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeLiveDomainRecordData
&StartTime=2018-01-01T00:00:00Z
&EndTime=2018-01-02T00:00:00Z
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveDomainRecordDataResponse>
  <RecordDataInfos>
		    <RecordDataInfo>
			      <Date>20180101</Date>
			      <Detail>
				        <TS>86310</TS>
			      </Detail>
			      <Total>86310</Total>
		    </RecordDataInfo>
		    <RecordDataInfo>
			      <Date>20180102</Date>
			      <Detail>
				        <TS>86310</TS>
			      </Detail>
			      <Total>86310</Total>
		    </RecordDataInfo>
	  </RecordDataInfos>
	  <RequestId>0B250400-6260-4CBC-85BF-FB0ED3753690</RequestId>
</DescribeLiveDomainRecordDataResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"0B250400-6260-4CBC-85BF-FB0ED3753690",
	"RecordDataInfos":{
		"RecordDataInfo":[
			{
				"Detail":{
					"TS":86310
				},
				"Date":"20180101",
				"Total":86310
			},
			{
				"Detail":{
					"TS":86310
				},
				"Date":"20180102",
				"Total":86310
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

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


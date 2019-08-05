# DescribeLiveDomainBpsData {#doc_api_live_DescribeLiveDomainBpsData .reference}

调用DescribeLiveDomainBpsData查询直播域名的网络带宽监控数据。

-   不指定StartTime和EndTime时，默认读取过去24小时的数据，同时支持按指定的起止时间查询，两者需要同时指定。
-   支持批量域名查询，多个域名用逗号（半角）分隔。
-   最多可获取最近90天的数据。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveDomainBpsData&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveDomainBpsData|系统规定参数。取值：**DescribeLiveDomainBpsData**。

 |
|DomainName|String|否|test.com|需要查询的直播域名。

 若参数为空，默认返回所有直播域名合并后数据。

 |
|StartTime|String|否|2017-12-10T20:00:00Z|获取数据起始时间点。

 -   日期格式按照ISO8601表示法，并使用UTC时间。格式为：YYYY-MM-DDThh:mm:ssZ。
-   最小数据粒度为**5**分钟。
-   最大数据粒度为**1**天。
-   最长可查询**90**天内的数据。

 |
|EndTime|String|否|2017-12-10T21:00:00Z|结束时间需大于起始时间。

 -   获日期格式按照ISO8601表示法，并使用UTC时间。格式为：YYYY-MM-DDThh:mm:ssZ。
-   最小数据粒度为**5**分钟。
-   最大数据粒度为**1**天。
-   最长可查询**90**天内的数据。

 |
|Interval|String|否|300|查询数据的时间粒度，支持**300（默认值）**, **3600**和**86400**秒。

 **说明：** 不传或传值不支持时，使用默认值300秒。

 |
|LocationNameEn|String|否|tianjin|区域英文名，通过**DescribeCdnRegionAndIsp**接口获得，不传为所有区域。

 |
|IspNameEn|String|否|alibaba|运营商英文名，通过**DescribeCdnRegionAndIsp**接口获得，不传为所有运营商。

 |
|RegionId|String|否|cn-shanghai|区域。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DomainName|String|test.com|直播域名信息。

 |
|DataInterval|String|300|查询数据的时间粒度。

 |
|BpsDataPerInterval| | |每个时间间隔的网络带宽数据。

 |
|TimeStamp|String|2017-12-10T20:00:05Z|时间片起始时刻。

 |
|BpsValue|String|11288111|bps数据值，单位：bit/second。

 |
|HttpBpsValue|String|11286111|http bps数据值，单位：bit/second。

 |
|HttpsBpsValue|String|2000|https bps数据值，单位：bit/second。

 |
|RequestId|String|B955107D-E658-4E77-B913-E0AC3D31693E|请求ID。

 |
|StartTime|String|2017-12-10T20:00:00Z|开始时间。

 |
|EndTime|String|2017-12-10T21:00:00Z|结束时间。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=DescribeLiveDomainBpsData
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveDomainBpsDataResponse>
	  <BpsDataPerInterval>
		    <DataModule>
			      <BpsValue>11288111</BpsValue>
			      <HttpBpsValue>11286111</HttpBpsValue>
			      <HttpsBpsValue>2000</HttpsBpsValue>
			      <TimeStamp>2017-12-10T20:00:00Z</TimeStamp>
		    </DataModule>
		    <DataModule>
			      <BpsValue>1288111</BpsValue>
			      <HttpBpsValue>1286111</HttpBpsValue>
			      <HttpsBpsValue>2000</HttpsBpsValue>
			      <TimeStamp>2017-12-10T20:05:00Z</TimeStamp>
		    </DataModule>
	  </BpsDataPerInterval>
	  <DataInterval>300</DataInterval>
	  <DomainName>test.com</DomainName>
	  <EndTime>2017-12-10T21:00:00Z</EndTime>
	  <RequestId>3C6CCEC4-6B88-4D4A-93E4-D47B3D92CF8F</RequestId>
	  <StartTime>2017-12-10T20:00:00Z</StartTime>
</DescribeLiveDomainBpsDataResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"DataInterval":"300",
	"BpsDataPerInterval":{
		"DataModule":[
			{
				"TimeStamp":"2017-12-10T20:00:00Z",
				"HttpBpsValue":"11286111",
				"BpsValue":"11288111",
				"HttpsBpsValue":"2000"
			},
			{
				"TimeStamp":"2017-12-10T20:05:00Z",
				"HttpBpsValue":"1286111",
				"BpsValue":"1288111",
				"HttpsBpsValue":"2000"
			}
		]
	},
	"RequestId":"3C6CCEC4-6B88-4D4A-93E4-D47B3D92CF8F",
	"DomainName":"test.com",
	"EndTime":"2017-12-10T21:00:00Z",
	"StartTime":"2017-12-10T20:00:00Z"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidStartTime.Malformed|Specified StartTime is malformed.|StartTime参数错误，请您确认该StartTime参数是否正确。|
|400|InvalidEndTime.Malformed|Specified EndTime is malformed.|结束时间错误，请您确认结束时间是否正确。|
|400|InvalidEndTime.Mismatch|Specified end time does not math the specified start time.|结束时间与开始时间不匹配，请您确认时间的匹配度。|

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


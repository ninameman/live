# DescribeLiveDomainRealTimeTrafficData {#doc_api_live_DescribeLiveDomainRealTimeTrafficData .reference}

调用DescribeLiveDomainRealTimeTrafficData获取加速域名的1分钟流量监控数据。

-   不指定StartTime和EndTime时，默认读取过去 1 小时的数据，同时支持按指定的起止时间查询，两者需要同时指定。
-   支持批量域名查询，多个域名可用逗号（半角）分隔。
-   最多可获取最近90天的数据。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveDomainRealTimeTrafficData&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveDomainRealTimeTrafficData|系统规定参数。取值：**DescribeLiveDomainRealTimeTrafficData**。

 |
|DomainName|String|否|test.com|可输入需要查询的加速域名。

 **说明：** 支持批量域名查询，多个域名用逗号（半角）分隔。若参数为空，默认返回所有加速域名合并后数据。

 |
|EndTime|String|否|2015-12-10T20:01:00Z|结束时间需大于起始时间。日期格式按照ISO8601表示法，并使用UTC时间。格式为：`YYYY-MM-DDThh:mm:ssZ`。

 |
|IspNameEn|String|否|alibaba|运营商英文名，通过**DescribeCdnRegionAndIsp**接口获得，不传为所有运营商。

 |
|LocationNameEn|String|否|tianjin|区域英文名，通过**DescribeCdnRegionAndIsp**接口获得，不传为所有区域。

 |
|RegionId|String|否|cn-shanghai|区域。

 |
|StartTime|String|否|2015-12-10T20:00:00Z|获取数据起始时间点。日期格式按照ISO8601表示法，并使用UTC时间。格式为：`YYYY-MM-DDThh:mm:ssZ` 。

 **说明：** 不写默认读取过去1小时数据。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DataInterval|String|60|每条记录的时间间隔，以秒为单位。

 |
|DomainName|String|test.com|加速域名信息。

 |
|EndTime|String|2015-12-10T20:01:00Z|结束时间。

 |
|RealTimeTrafficDataPerInterval| | |每个时间间隔的流量数据。

 |
|TimeStamp|String|2015-12-10T20:01:00Z|时间片起始时刻。

 |
|Value|String|0|详细使用数据。

 |
|RequestId|String|A666D44F-19D6-490E-97CF-1A64AB962C57|请求ID。

 |
|StartTime|String|2015-12-10T20:00:00Z|开始时间。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeLiveDomainRealTimeTrafficData
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveDomainRealTimeTrafficDataResponse>
	  <DomainName>test.com</DomainName>
	  <DataInterval>60</DataInterval>
	  <RealTimeTrafficDataPerInterval>
		    <DataModule>
			      <TimeStamp>2015-12-10T20:00:00Z</TimeStamp>
			      <Value>0</Value>
		    </DataModule>
		    <DataModule>
			      <TimeStamp>2015-12-10T20:01:00Z</TimeStamp>
			      <Value>0</Value>
		    </DataModule>
	  </RealTimeTrafficDataPerInterval>
	  <RequestId>A666D44F-19D6-490E-97CF-1A64AB962C57</RequestId>
	  <StartTime>2015-12-10T20:00:00Z</StartTime>
	  <EndTime>2015-12-10T20:01:00Z</EndTime>
</DescribeLiveDomainRealTimeTrafficDataResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"DataInterval":"60",
	"RequestId":"A666D44F-19D6-490E-97CF-1A64AB962C57",
	"RealTimeTrafficDataPerInterval":{
		"DataModule":[
			{
				"TimeStamp":"2015-12-10T20:00:00Z",
				"Value":"0"
			},
			{
				"TimeStamp":"2015-12-10T20:01:00Z",
				"Value":"0"
			}
		]
	},
	"DomainName":"test.com",
	"EndTime":"2015-12-10T20:01:00Z",
	"StartTime":"2015-12-10T20:00:00Z"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidStartTime.Malformed|Specified StartTime is malformed.|StartTime参数错误，请您确认该StartTime参数是否正确。|
|400|InvalidEndTime.Malformed|Specified EndTime is malformed.|结束时间错误，请您确认结束时间是否正确。|
|400|InvalidEndTime.Mismatch|Specified end time does not math the specified start time.|结束时间与开始时间不匹配，请您确认时间的匹配度。|

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


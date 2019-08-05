# DescribeLiveDomainRealTimeBpsData {#doc_api_live_DescribeLiveDomainRealTimeBpsData .reference}

调用DescribeLiveDomainRealTimeBpsData获取域名1分钟粒度带宽数据。

-   可以查询7天内的数据，单次查询StartTime和EndTime跨度不能超过24小时。
-   如果StartTime和EndTime均未指定，默认返回当前时间起一小时内的数据。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveDomainRealTimeBpsData&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveDomainRealTimeBpsData|系统规定参数，取值：**DescribeLiveDomainRealTimeBpsData**。

 |
|DomainName|String|是|test.com,abc.com|域名。

 |
|EndTime|String|否|2015-11-30T05:40:00Z|结束时间。

 -   日期格式按照ISO8601表示法，并使用UTC时间。 例如：**2016-10-20T04:00:00Z**。
-   不填默认查询从StartTime起一小时内的数据。

 |
|IspNameEn|String|否|alibaba|运营商英文名，通过**DescribeCdnRegionAndIsp**接口获得，不传为所有运营商。

 |
|LocationNameEn|String|否|tianjin|区域英文名，通过**DescribeCdnRegionAndIsp**接口获得，不传为所有区域。

 |
|RegionId|String|否|cn-shanghai|区域。

 |
|StartTime|String|否|2015-11-30T05:39:00Z|起始时间。

 日期格式按照ISO8601表示法，并使用UTC时间。 例如：**2016-10-20T04:00:00Z**。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DataInterval|String|60|查询数据的时间粒度。

 |
|DomainName|String|test.com,abc.com|直播域名信息。

 |
|EndTime|String|2015-11-30T05:40:00Z|结束时间。

 |
|RealTimeBpsDataPerInterval| | |域名1分钟粒度带宽数据。

 |
|TimeStamp|String|2015-11-30T05:39:00Z|数据时间戳。

 |
|Value|String|59392614.8|带宽数据，单位是**bit/second**。

 |
|RequestId|String|BC858082-736F-4A25-867B-E5B67C85ACF7|请求ID。

 |
|StartTime|String|2015-11-30T05:33:00Z|开始时间。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=DescribeLiveDomainRealTimeBpsData
&DomainName=test.com,abc.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveDomainRealTimeBpsDataResponse>
	  <RealTimeBpsDataPerInterval>
		    <DataModule>
			      <TimeStamp>2018-01-02T11:05:00Z</TimeStamp>
			      <Value>16710625.733333332</Value>
		    </DataModule>
		    <DataModule>
			      <TimeStamp>2018-01-02T11:04:00Z</TimeStamp>
			      <Value>59392614.8</Value>
		    </DataModule>
	  </RealTimeBpsDataPerInterval>
	  <RequestId>B49E6DDA-F413-422B-B58E-2FA23F286726</RequestId>
	  <DomainName>test.com</DomainName>
	  <EndTime>2017-12-10T21:00:00Z</EndTime>
	  <DataInterval>300</DataInterval>
	  <StartTime>2017-12-10T20:00:00Z</StartTime>
</DescribeLiveDomainRealTimeBpsDataResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"DataInterval":"300",
	"RealTimeBpsDataPerInterval":{
		"DataModule":[
			{
				"TimeStamp":"2018-01-02T11:05:00Z",
				"Value":16710625.733333332
			},
			{
				"TimeStamp":"2018-01-02T11:04:00Z",
				"Value":59392614.8
			}
		]
	},
	"RequestId":"B49E6DDA-F413-422B-B58E-2FA23F286726",
	"DomainName":"test.com",
	"EndTime":"2017-12-10T21:00:00Z",
	"StartTime":"2017-12-10T20:00:00Z"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


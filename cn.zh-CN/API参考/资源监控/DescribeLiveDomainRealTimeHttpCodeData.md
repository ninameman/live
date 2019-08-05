# DescribeLiveDomainRealTimeHttpCodeData {#doc_api_live_DescribeLiveDomainRealTimeHttpCodeData .reference}

调用DescribeLiveDomainRealTimeHttpCodeData获取加速域名1分钟粒度的HTTP返回码占比数据。

-   单次查询**StartTime**和**EndTime**跨度不能超过24小时。
-   如果**StartTime**和**EndTime**均未指定, 默认返回当前时间起一小时内的数据。
-   支持批量域名查询，多个域名用逗号（半角）分隔。
-   最多可获取最近**7**天的数据。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveDomainRealTimeHttpCodeData&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveDomainRealTimeHttpCodeData|系统规定参数，取值：**DescribeLiveDomainRealTimeHttpCodeData**。

 |
|DomainName|String|是|test.com,abc.com|需要查询的加速域名。

 **说明：** 支持批量查询，多个域名用逗号（半角）分隔。

 |
|EndTime|String|否|2015-11-30T05:40:00Z|结束时间需大于起始时间。日期格式按照ISO8601表示法，并使用UTC时间。 格式为：`YYYY-MM-DDThh:mm:ssZ`。

 |
|IspNameEn|String|否|alibaba|运营商英文名，通过**DescribeCdnRegionAndIsp**接口获得，不传为所有运营商。

 |
|LocationNameEn|String|否|tianjin|区域英文名，通过**DescribeCdnRegionAndIsp**接口获得，不传为所有区域。

 |
|RegionId|String|否|cn-shanghai|区域。

 |
|StartTime|String|否|2015-11-30T05:39:00Z|获取数据起始时间点。日期格式按照ISO8601表示法，并使用UTC时间。 格式为：`YYYY-MM-DDThh:mm:ssZ`。

 **说明：** 若参数为空，默认读取过去**1**小时数据。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DataInterval|String|60|每条记录的时间间隔，以秒为单位，默认值为**60**。

 |
|DomainName|String|test.com,abc.com|加速域名信息。

 |
|EndTime|String|2015-11-30T05:40:00Z|结束时间。

 |
|RealTimeHttpCodeData| | |每个时间间隔的HTTP返回码占比数据。

 |
|TimeStamp|String|2015-11-30T05:39:00Z|时间片起始时刻。

 |
|Value| | |各返回码占比使用数据列表。

 |
|Code|String|200|http返回码。

 |
|Count|String|20|返回码数。

 |
|Proportion|String|66.046511627907|占比使用数据。

 |
|RequestId|String|BC858082-736F-4A25-867B-E5B67C85ACF7|请求ID。

 |
|StartTime|String|2015-11-30T05:33:00Z|开始时间。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=DescribeLiveDomainRealTimeHttpCodeData
&DomainName=test.com,abc.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveDomainRealTimeHttpCodeDataResponse>
	  <RealTimeHttpCodeData>
		    <UsageData>
			      <TimeStamp>2015-11-30T05:40:00Z</TimeStamp>
			      <Value>
				        <RealTimeCodeProportionData>
					          <Proportion>66.046511627907</Proportion>
					          <Code>200</Code>
				        </RealTimeCodeProportionData>
				        <RealTimeCodeProportionData>
					          <Proportion>4.72868217054264</Proportion>
					          <Code>206</Code>
				        </RealTimeCodeProportionData>
				        <RealTimeCodeProportionData>
					          <Proportion>0.155038759689922</Proportion>
					          <Code>302</Code>
				        </RealTimeCodeProportionData>
				        <RealTimeCodeProportionData>
					          <Proportion>0.62015503875969</Proportion>
					          <Code>304</Code>
				        </RealTimeCodeProportionData>
				        <RealTimeCodeProportionData>
					          <Proportion>28.4496124031008</Proportion>
					          <Code>500</Code>
				        </RealTimeCodeProportionData>
			      </Value>
		    </UsageData>
		    <UsageData>
			      <TimeStamp>2015-11-30T05:39:00Z</TimeStamp>
			      <Value>
				        <RealTimeCodeProportionData>
					          <Proportion>66.046511627907</Proportion>
					          <Code>200</Code>
				        </RealTimeCodeProportionData>
				        <RealTimeCodeProportionData>
					          <Proportion>4.72868217054264</Proportion>
					          <Code>206</Code>
				        </RealTimeCodeProportionData>
				        <RealTimeCodeProportionData>
					          <Proportion>0.155038759689922</Proportion>
					          <Code>302</Code>
				        </RealTimeCodeProportionData>
				        <RealTimeCodeProportionData>
					          <Proportion>0.62015503875969</Proportion>
					          <Code>304</Code>
				        </RealTimeCodeProportionData>
				        <RealTimeCodeProportionData>
					          <Proportion>28.4496124031008</Proportion>
					          <Code>500</Code>
				        </RealTimeCodeProportionData>
			      </Value>
		    </UsageData>
	  </RealTimeHttpCodeData>
	  <DataInterval>60</DataInterval>
	  <RequestId>BC858082-736F-4A25-867B-E5B67C85ACF7</RequestId>
	  <DomainName>test.com,abc.com</DomainName>
	  <EndTime>2015-11-30T05:40:00Z</EndTime>
	  <StartTime>2015-11-30T05:33:00Z</StartTime>
</DescribeLiveDomainRealTimeHttpCodeDataResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"DataInterval":"60",
	"RequestId":"BC858082-736F-4A25-867B-E5B67C85ACF7",
	"DomainName":"test.com,abc.com",
	"EndTime":"2015-11-30T05:40:00Z",
	"StartTime":"2015-11-30T05:33:00Z",
	"RealTimeHttpCodeData":{
		"UsageData":[
			{
				"TimeStamp":"2015-11-30T05:40:00Z",
				"Value":{
					"RealTimeCodeProportionData":[
						{
							"Proportion":"66.046511627907",
							"Code":"200"
						},
						{
							"Proportion":"4.72868217054264",
							"Code":"206"
						},
						{
							"Proportion":"0.155038759689922",
							"Code":"302"
						},
						{
							"Proportion":"0.62015503875969",
							"Code":"304"
						},
						{
							"Proportion":"28.4496124031008",
							"Code":"500"
						}
					]
				}
			},
			{
				"TimeStamp":"2015-11-30T05:39:00Z",
				"Value":{
					"RealTimeCodeProportionData":[
						{
							"Proportion":"66.046511627907",
							"Code":"200"
						},
						{
							"Proportion":"4.72868217054264",
							"Code":"206"
						},
						{
							"Proportion":"0.155038759689922",
							"Code":"302"
						},
						{
							"Proportion":"0.62015503875969",
							"Code":"304"
						},
						{
							"Proportion":"28.4496124031008",
							"Code":"500"
						}
					]
				}
			}
		]
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


# DescribeLiveDomainTranscodeData {#doc_api_live_DescribeLiveDomainTranscodeData .reference}

调用DescribeLiveDomainTranscodeData查询直播域名转码时长数据。

-   支持用户查询单个直播域名在指定时间区段内的每日转码时长数据。
-   每日转码时长数据包括：**当日转码总时长**和**区分转码规格**的时长数据列表。
-   支持查询**2018/01/01**起的数据，数据查询的起止时间跨度最大为**90**天。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveDomainTranscodeData&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveDomainTranscodeData|系统规定参数。取值：**DescribeLiveDomainTranscodeData**。

 |
|StartTime|String|是|2018-01-01T00:00:00Z|获取数据起始时间点。

 日期格式按照ISO8601表示法，并使用UTC时间格式：`YYYY-MM-DDThh:mm:ssZ`。

 **说明：** 支持查询2018/01/01起的数据，即**StartTime** ≥ `2018-01-01T00:00:00Z`。

 |
|EndTime|String|是|2018-01-02T01:00:00Z|获取数据结束时间。需大于起始时间。

 日期格式按照ISO8601表示法，并使用UTC时间格式：`YYYY-MM-DDThh:mm:ssZ`。

 |
|DomainName|String|否|www.example.com|需要查询的直播域名。

 |
|RegionId|String|否|cn-shanghai|区域。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|TranscodeDataInfos| | |直播转码时长的每日数据统计。

 |
|Date|String|20180202|日期，具体到天。

 |
|Total|Integer|4710|单日转码总时长，单位：秒。

 |
|Detail|String|\{ "LD\_CASTER": 86315, "SD\_CASTER": 86315 \}, "Date": "20180212", "Total": 172630\}|区分转码规格的转码时长信息。

 |
|RequestId|String|B955107D-E658-4E77-B913-E0AC3D31693F|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeLiveDomainTranscodeData
&StartTime=2018-01-01T00:00:00Z
&EndTime=2018-01-02T01:00:00Z
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveDomainTranscodeDataResponse>
	  <RequestId>BCB009C1-10B1-47F0-BD2F-936D5DD4F5FA</RequestId>
	  <TranscodeDataInfos>
		    <TranscodeDataInfo>
			      <Date>20180212</Date>
			      <Detail>
				        <LD_CASTER>86315</LD_CASTER>
				        <SD_CASTER>86315</SD_CASTER>
			      </Detail>
			      <Total>172630</Total>
		    </TranscodeDataInfo>
		    <TranscodeDataInfo>
			      <Date>20180213</Date>
			      <Detail>
				        <LD_CASTER>86315</LD_CASTER>
				        <SD_CASTER>86320</SD_CASTER>
			      </Detail>
			      <Total>172635</Total>
		    </TranscodeDataInfo>
		    <TranscodeDataInfo>
			      <Date>20180214</Date>
			      <Detail>
				        <LD_CASTER>86315</LD_CASTER>
				        <SD_CASTER>86315</SD_CASTER>
			      </Detail>
			      <Total>172630</Total>
		    </TranscodeDataInfo>
		    <TranscodeDataInfo>
			      <Date>20180215</Date>
			      <Detail>
				        <LD_CASTER>86315</LD_CASTER>
				        <SD_CASTER>86320</SD_CASTER>
			      </Detail>
			      <Total>172635</Total>
		    </TranscodeDataInfo>
	  </TranscodeDataInfos>
</DescribeLiveDomainTranscodeDataResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"BCB009C1-10B1-47F0-BD2F-936D5DD4F5FA",
	"TranscodeDataInfos":{
		"TranscodeDataInfo":[
			{
				"Detail":{
					"LD_CASTER":86315,
					"SD_CASTER":86315
				},
				"Date":"20180212",
				"Total":172630
			},
			{
				"Detail":{
					"LD_CASTER":86315,
					"SD_CASTER":86320
				},
				"Date":"20180213",
				"Total":172635
			},
			{
				"Detail":{
					"LD_CASTER":86315,
					"SD_CASTER":86315
				},
				"Date":"20180214",
				"Total":172630
			},
			{
				"Detail":{
					"LD_CASTER":86315,
					"SD_CASTER":86320
				},
				"Date":"20180215",
				"Total":172635
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


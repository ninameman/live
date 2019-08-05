# DescribeLiveRecordConfig {#doc_api_live_DescribeLiveRecordConfig .reference}

调用DescribeLiveRecordConfig查询域名下所有App录制配置。

根据DomainName、AppName、StreamName匹配查询，以列表形式返回（可能有多条配置）。支持分页和排序。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveRecordConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveRecordConfig|系统规定参数。取值：**DescribeLiveRecordConfig**。

 |
|DomainName|String|是|www.yourdomain.com|您的加速域名。

 |
|AppName|String|否|testApp|直播流所属应用名称。

 |
|Order|String|否|asc|排序。取值：

 -   asc（默认值）：升序
-   desc：降序

 |
|PageNum|Integer|否|1|当前页码。默认值：**1**。

 |
|PageSize|Integer|否|5|每页大小。默认值：**10**，取值范围：**5~30**。

 |
|StreamName|String|否|myStreamName|直播流名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|5056369B-D337-499E-B8B7-B761BD37B08A|请求ID。

 |
|LiveAppRecordList| | |录制配置。

 |
|DomainName|String|test.com|流所属加速域名。

 |
|AppName|String|testApp|流所属应用名称。

 |
|OssEndpoint|String|oss-cn-shanghai.aliyuncs.com|OSS endpoint。

 |
|OssBucket|String|test123|OSS存储bucket名称。

 |
|CreateTime|String|2016-05-20T09:33:38Z|创建时间。

 |
|RecordFormatList| | |格式列表。

 |
|Format|String|xxx|格式名称。

 |
|OssObjectPrefix|String|xxx|OSS存储文件名。

 |
|SliceOssObjectPrefix|String|xxx|存储分片的OSS文件名。

 |
|CycleDuration|Integer|3600|周期录制时间，单位：秒。

 |
|EndTime|String|2018-11-08T03:49:18Z|计划录制结束时间，UTC时间。

 |
|OnDemond|Integer|0|按需录制。可取值：**0 | 1 | 2**。0表示关闭，1表示通过HTTP回调方式，2表示通过推流参数方式。

 使用1方式时候需要设置OnDemandCallback, 否则默认不录制。

 |
|StartTime|String|2018-11-08T02:49:18Z|计划录制开始时间，UTC时间。

 |
|StreamName|String|myStreamName|流名称。

 |
|PageNum|Integer|5|分页的页码。

 |
|PageSize|Integer|10|每页大小。

 |
|Order|String|desc|排序。

 |
|TotalPage|Integer|20|总页数。

 |
|TotalNum|Integer|12|符合条件的总个数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[live.aliyuncs.com]/?Action=DescribeLiveRecordConfig
&DomainName=www.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveRecordConfigResponse>
	  <LiveAppRecordList>
		    <LiveAppRecord>
			      <AppName>aliyuntest</AppName>
			      <CreateTime>2016-05-20T09:33:38Z</CreateTime>
			      <DomainName>xxxxx</DomainName>
			      <FormatList>
				        <Format>
					          <Name>m3u8</Name>
					          <OssObjectPrefix>xxx</OssObjectPrefix>
					          <SliceOssObjectPrefix>xxx</SliceOssObjectPrefix>
				        </Format>
			      </FormatList>
			      <OssBucket>chimang.bucket</OssBucket>
			      <OssEndpoint>oss-cn-hangzhou.aliyuncs.com</OssEndpoint>
		    </LiveAppRecord>
	  </LiveAppRecordList>
	  <RequestId>5056369B-D337-499E-B8B7-B761BD37B08A</RequestId>
</DescribeLiveRecordConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"LiveAppRecordList":{
		"LiveAppRecord":[
			{
				"CreateTime":"2016-05-20T09:33:38Z",
				"DomainName":"xxxxx",
				"OssEndpoint":"oss-cn-hangzhou.aliyuncs.com",
				"FormatList":{
					"Format":[
						{
							"Name":"m3u8",
							"SliceOssObjectPrefix":"xxx",
							"OssObjectPrefix":"xxx"
						}
					]
				},
				"AppName":"aliyuntest",
				"OssBucket":"chimang.bucket"
			}
		]
	},
	"RequestId":"5056369B-D337-499E-B8B7-B761BD37B08A"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


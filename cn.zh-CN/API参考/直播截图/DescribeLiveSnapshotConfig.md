# DescribeLiveSnapshotConfig {#doc_api_live_DescribeLiveSnapshotConfig .reference}

调用DescribeLiveSnapshotConfig查询域名下的截图配置。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveSnapshotConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveSnapshotConfig|系统规定参数。取值：**DescribeLiveSnapshotConfig**。

 |
|DomainName|String|是|www.yourdomain.com|您的加速域名。

 |
|AppName|String|否|testApp|直播流所属应用名称。

 \*表示查询针对域名的配置，不传表示查询该域名下所有的配置。

 |
|Order|String|否|asc|排序。取值：

 -   asc（默认值）：升序
-   desc：降序

 |
|PageNum|Integer|否|1| 

 分页的页码。

 默认值：**1**。

 |
|PageSize|Integer|否|10|每页大小。取值范围：**5~30**。

 默认值：**10**。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|A3136B58-5876-4168-83CA-B562781981A0|请求ID。

 |
|LiveStreamSnapshotConfigList| | |截图配置。

 |
|DomainName|String|xxx|加速域名。

 |
|AppName|String|xxx|直播流所属的应用名称。

 |
|TimeInterval|Integer|10|截图周期。

 |
|CreateTime|String|2016-05-20T01:33:38Z|创建时间。

 |
|OssBucket|String|test123|OssBucket的名称。

 |
|OssEndpoint|String|oss-cn-shanghai.aliyuncs.com|OssEndpoint域名。

 |
|OverwriteOssObject|String|test123|OSS存储文件名。

 |
|SequenceOssObject|String|test123|OSS存储文件名。

 |
|PageNum|Integer|2|分页的页码。

 |
|PageSize|Integer|11|每页大小。

 |
|Order|String|asc|排序。

 |
|TotalPage|Integer|10|总页数。

 |
|TotalNum|Integer|6|符合条件的总个数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=DescribeLiveSnapshotConfig
&DomainName=www.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveSnapshotConfigResponse>
	  <LiveStreamSnapshotConfigList>
		    <LiveStreamSnapshotConfig>
			      <AppName>xxx</AppName>
			      <CreateTime>2016-05-20T01:33:38Z</CreateTime>
			      <DomainName>xxx</DomainName>
			      <OssBucket>bucket</OssBucket>
			      <OssEndpoint>endpoint</OssEndpoint>
			      <OverwriteOssObject>object</OverwriteOssObject>
			      <SequenceOssObject>object</SequenceOssObject>
			      <TimeInterval>10</TimeInterval>
		    </LiveStreamSnapshotConfig>
	  </LiveStreamSnapshotConfigList>
	  <Order>asc</Order>
	  <PageNum>1</PageNum>
	  <PageSize>10</PageSize>
	  <RequestId>A3136B58-5876-4168-83CA-B562781981A0</RequestId>
	  <TotalNum>100</TotalNum>
	  <TotalPage>10</TotalPage>
</DescribeLiveSnapshotConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"TotalPage":10,
	"TotalNum":100,
	"PageSize":10,
	"RequestId":"A3136B58-5876-4168-83CA-B562781981A0",
	"Order":"asc",
	"LiveStreamSnapshotConfigList":{
		"LiveStreamSnapshotConfig":[
			{
				"OverwriteOssObject":"object",
				"SequenceOssObject":"object",
				"CreateTime":"2016-05-20T01:33:38Z",
				"DomainName":"xxx",
				"OssEndpoint":"endpoint",
				"AppName":"xxx",
				"OssBucket":"bucket",
				"TimeInterval":10
			}
		]
	},
	"PageNum":1
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


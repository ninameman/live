# DescribeLiveSnapshotDetectPornConfig {#doc_api_live_DescribeLiveSnapshotDetectPornConfig .reference}

调用DescribeLiveSnapshotDetectPornConfig查询审核配置。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveSnapshotDetectPornConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveSnapshotDetectPornConfig|系统规定参数。取值：**DescribeLiveSnapshotDetectPornConfig**。

 |
|DomainName|String|是|www.yourdomain.com|用户域名。

 |
|AppName|String|否|testApp|app名，如不给出表示域名下所有的。

 |
|Order|String|否|asc|排序。取值：

 -   **Asc（默认值）**：升序
-   **Desc**：降序

 |
|PageNum|Integer|否|1|分页的页码。

 默认值：**1**。

 |
|PageSize|Integer|否|10| 

 每页大小。默认值：**10**。

 取值范围：**5~30**。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |
|LiveSnapshotDetectPornConfigList| | |审核配置，只在正确返回时有。

 |
|DomainName|String|live.aliyunlive.com|用户域名。

 |
|AppName|String|xxx02|app名。

 |
|Interval|Integer|80|采样间隔。

 |
|OssBucket|String|test123|OSS的Bucket名称。

 |
|OssEndpoint|String|oss-cn-shanghai.aliyuncs.com|OssEndpoint的名称。

 |
|OssObject|String|\{AppName\}/\{StreamName\}/\{Date\}/\{Hour\}/\{Minute\}\_\{Second\}.jpg|OssObject的名称。

 |
|Scenes| |porn|检测场景，包括：**porn（默认值） | terrorism | ad | live**。

 |
|PageNum|Integer|1|分页的页码。

 |
|PageSize|Integer|2|每页大小。

 |
|Order|String|desc|排序。

 |
|TotalPage|Integer|11|总页数。

 |
|TotalNum|Integer|6|符合条件的总个数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://live.aliyuncs.com/?Action=DescribeLiveSnapshotDetectPornConfig
&DomainName=www.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveSnapshotDetectPornConfigResponse>
	  <LiveSnapshotDetectPornConfigList>
		    <LiveSnapshotDetectPornConfig>
			      <AppName>xxx01</AppName>
			      <DomainName>live.aliyunlive.com</DomainName>
			      <Interval>80</Interval>
			      <OssBucket>bucket</OssBucket>
			      <OssEndpoint>oss-cn-hangzhou.aliyuncs.com</OssEndpoint>
			      <OssObject>{AppName}/{StreamName}/{Date}/{Hour}/{Minute}_{Second}.jpg</OssObject>
		    </LiveSnapshotDetectPornConfig>
		    <LiveSnapshotDetectPornConfig>
			      <AppName>xxx02</AppName>
			      <DomainName>live.aliyunlive.com</DomainName>
			      <Interval>80</Interval>
			      <OssBucket>bucket</OssBucket>
			      <OssEndpoint>oss-cn-hangzhou.aliyuncs.com</OssEndpoint>
			      <OssObject>{AppName}/{StreamName}/{Date}/{Hour}/{Minute}_{Second}.jpg</OssObject>
		    </LiveSnapshotDetectPornConfig>
	  </LiveSnapshotDetectPornConfigList>
	  <Order>desc</Order>
	  <PageNum>1</PageNum>
	  <PageSize>2</PageSize>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <TotalNum>11</TotalNum>
	  <TotalSize>6</TotalSize>
</DescribeLiveSnapshotDetectPornConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"TotalNum":11,
	"PageSize":2,
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
	"Order":"desc",
	"LiveSnapshotDetectPornConfigList":{
		"LiveSnapshotDetectPornConfig":[
			{
				"OssObject":"{AppName}/{StreamName}/{Date}/{Hour}/{Minute}_{Second}.jpg",
				"Interval":80,
				"DomainName":"live.aliyunlive.com",
				"OssEndpoint":"oss-cn-hangzhou.aliyuncs.com",
				"AppName":"xxx01",
				"OssBucket":"bucket"
			},
			{
				"OssObject":"{AppName}/{StreamName}/{Date}/{Hour}/{Minute}_{Second}.jpg",
				"Interval":80,
				"DomainName":"live.aliyunlive.com",
				"OssEndpoint":"oss-cn-hangzhou.aliyuncs.com",
				"AppName":"xxx02",
				"OssBucket":"bucket"
			}
		]
	},
	"TotalSize":6,
	"PageNum":1
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


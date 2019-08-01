# DescribeLiveStreamsBlockList {#doc_api_live_DescribeLiveStreamsBlockList .reference}

调用DescribeLiveStreamsBlockList获取域名下直播流播放的黑名单。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveStreamsBlockList&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveStreamsBlockList|系统规定参数。取值：**DescribeLiveStreamsBlockList**。

 |
|DomainName|String|是|www.yourdomain.com|您的加速域名。

 |
|PageNum|Integer|否|2|当前页码。默认值为**1**。

 |
|PageSize|Integer|否|10|每页大小。取值范围：**1~3000**之间的任意整数，默认值为**2000**，最大值为**3000**。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DomainName|String|play.aliyunlive.com|流所属加速域名。

 |
|StreamUrls| |play.aliyunlive.com/AppName/StreamName|流完整URL地址。

 |
|PageNum|Integer|2|分页的当前页码。

 |
|PageSize|Integer|10|每页显示的条数。

 |
|RequestId|String|9D855EC8-CF71-4615-B164-F7DFCB23B41D|请求ID。

 |
|TotalNum|Integer|11|符合条件的总个数。

 |
|TotalPage|Integer|2|总页数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeLiveStreamsBlockList
&DomainName=www.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveStreamsBlockListResponse>
	  <DomainName>test101.cdnpe.com</DomainName>
	  <PageNum>2</PageNum>
	  <PageSize>10</PageSize>
	  <RequestId>9D855EC8-CF71-4615-B164-F7DFCB23B41D</RequestId>
	  <StreamUrls>
		    <StreamUrl>test101.cdnpe.com/app/stream1</StreamUrl>
	  </StreamUrls>
	  <TotalNum>11</TotalNum>
	  <TotalPage>2</TotalPage>
</DescribeLiveStreamsBlockListResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"TotalPage":2,
	"TotalNum":11,
	"PageSize":10,
	"RequestId":"9D855EC8-CF71-4615-B164-F7DFCB23B41D",
	"StreamUrls":{
		"StreamUrl":[
			"test101.cdnpe.com/app/stream1"
		]
	},
	"DomainName":"test101.cdnpe.com",
	"PageNum":2
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


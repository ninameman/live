# DescribeLiveStreamsOnlineList {#doc_api_live_DescribeLiveStreamsOnlineList .reference}

调用DescribeLiveStreamsOnlineList查看指定域名下（或者指定域名下某个应用）的所有正在推的流的信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveStreamsOnlineList&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveStreamsOnlineList|系统规定参数。取值：**DescribeLiveStreamsOnlineList**。

 |
|DomainName|String|是|play.yourdomain.com|您的加速域名。

 |
|AppName|String|否|testApp|应用名称。

 **说明：** AppName不支持通配符（\*）查询，且不支持模糊查询。

 |
|PageNum|Integer|否|1|当前页码，默认值为**1**。

 |
|PageSize|Integer|否|1500|每页大小，取值：**1~3000**之前的任意整数。最大值为**3000**，默认值为**2000**。

 |
|QueryType|String|否|fuzzy|指定是否模糊匹配流名称。取值：

 -   **fuzzy**：模糊匹配
-   **strict**：精准匹配

 |
|RegionId|String|否|cn-hangzhou|地域ID。

 |
|StreamName|String|否|myStream|流名称。

 **说明：** StreamName不支持通配符（\*）查询，但支持模糊查询 。

 |
|StreamType|String|否|all|流类型。取值范围：

 -   **all（默认值）**：查询所有流
-   **raw**：查询原始流
-   **trans**：查询转码流

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|OnlineInfo| | |正在推送流的信息。

 |
|DomainName|String|play.yourdomain.com|流所属加速域名。

 |
|AppName|String|AppName|流所属应用名称。

 |
|StreamName|String|StreamName|流名称。

 |
|PublishTime|String|2015-12-02T06:58:04Z|开始推流时刻，UTC格式。

 |
|PublishUrl|String|rtmp://play.aliyunlive.com/AppName/StreamName|推流完整URL地址。

 |
|PublishDomain|String|push.aliyunlive.com|直播推流域名，使用中心推流的可直接填写播放域名。

 |
|PageNum|Integer|1|分页的页码。

 |
|PageSize|Integer|10|每页显示的条数。

 |
|RequestId|String|40A4F36D-A7CC-473A-88E7-154F92242566|请求ID。

 |
|TotalNum|Integer|10|符合条件的总个数。

 |
|TotalPage|Integer|100|总页数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com?Action=DescribeLiveStreamsOnlineList
&DomainName=play.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveStreamsOnlineListResponse>
	  <OnlineInfo>
		    <LiveStreamOnlineInfo>
			      <AppName>xchen</AppName>
			      <DomainName>test101.cdnpe.com</DomainName>
			      <PublishTime>2015-12-02T06:58:04Z</PublishTime>
			      <PublishUrl>rtmp://test101.cdnpe.com/xchen</PublishUrl>
			      <StreamName>testxchen</StreamName>
		    </LiveStreamOnlineInfo>
	  </OnlineInfo>
	  <PageNum>2</PageNum>
	  <PageSize>10</PageSize>
	  <RequestId>0D70427D-91E4-4349-AAD3-5511A5BB823B</RequestId>
	  <TotalNum>11</TotalNum>
	  <TotalPage>2</TotalPage>
</DescribeLiveStreamsOnlineListResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"TotalPage":2,
	"TotalNum":11,
	"PageSize":10,
	"RequestId":"0D70427D-91E4-4349-AAD3-5511A5BB823B",
	"PageNum":2,
	"OnlineInfo":{
		"LiveStreamOnlineInfo":[
			{
				"PublishTime":"2015-12-02T06:58:04Z",
				"StreamName":"testxchen",
				"PublishUrl":"rtmp://test101.cdnpe.com/xchen",
				"DomainName":"test101.cdnpe.com",
				"AppName":"xchen"
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


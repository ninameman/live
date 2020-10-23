# DescribeLiveStreamsPublishList

调用DescribeLiveStreamsPublishList获取某一时间段内某个域名（或域名下某应用或某个流）的历史推流记录。

**说明：** 调用频率限制3次/秒

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveStreamsPublishList&type=RPC&version=2016-11-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveStreamsPublishList|系统规定参数。取值：**DescribeLiveStreamsPublishList**。 |
|DomainName|String|是|play.yourdomain.com|您的域名。 |
|EndTime|String|是|2017-12-22T08:00:00Z|结束时间。EndTime和StartTime之间的间隔不能超过30天。

 UTC格式，例如：2016-06-30T19:00:00Z。 |
|StartTime|String|是|2017-12-21T08:00:00Z|起始时间。

 UTC 格式，例如：2016-06-29T19:00:00Z。 |
|RegionId|String|否|cn-hangzhou|所属区域。 |
|AppName|String|否|testApp|直播流所属应用名称。

 <note\>AppName不支持通配符（\*）查询，且不支持模糊查询。</note\> |
|StreamName|String|否|testStream|直播流名称。

 <note\>StreamName不支持通配符（\*）查询，但支持模糊查询 。</note\> |
|PageSize|Integer|否|1500|分页大小，取值：**1~3000**之前的任意整数。最大值为**3000**，默认值为**2000**。 |
|PageNumber|Integer|否|1|当前页码，默认值为**1**。 |
|StreamType|String|否|all|流类型。取值范围：

 -   **all（默认值）**：查询所有流
-   **raw**：查询原始流
-   **trans**：查询转码流 |
|QueryType|String|否|fuzzy|指定是否模糊匹配流名称。取值：

 -   **fuzzy**：模糊匹配
-   **strict**：精准匹配 |
|OrderBy|String|否|publish\_time\_desc|排序方式。取值范围：

 -   stream\_name\_desc
-   stream\_name\_asc
-   publish\_time\_desc
-   publish\_time\_asc |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|PublishInfo|Array of LiveStreamPublishInfo| |推流记录信息。 |
|LiveStreamPublishInfo| | | |
|DomainName|String|play.yourdomain.com|流所属加速域名。 |
|AppName|String|AppName|流所属应用名称。 |
|StreamName|String|StreamName|直播流名称。 |
|StreamUrl|String|http://play.aliyunlive.com/AppName/StreamName.flv|直播流的URL。 |
|PublishTime|String|2015-12-02T03:05:53Z|开始推流时刻。

 UTC时间。 |
|StopTime|String|2015-12-02T03:11:19Z|停止推流时刻。

 UTC时间。 |
|ClientAddr|String|10.175.60.33|主播IP。 |
|EdgeNodeAddr|String|10.175.30.21|CDN上行节点 IP。 |
|PublishUrl|String|rtmp://push.aliyunlive.com/AppName/StreamName|推流完整URL地址。 |
|PublishDomain|String|play.yourdomain.com|推流域名。 |
|PublishType|String|edge|推流类型。取值：

 -   **edge**：边缘推流
-   **center**：中心推流 |
|TranscodeId|String|ld|若有转码，返回转码模板ID。 |
|Transcoded|String|yes|是否是转码流。 |
|PageNum|Integer|2|分页的页码。 |
|PageSize|Integer|10|每页大小。 |
|RequestId|String|40A4F36D-A7CC-473A-88E7-154F92242566|请求ID。 |
|TotalNum|Integer|11|符合条件的总个数。 |
|TotalPage|Integer|2|总页数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeLiveStreamsPublishList
&DomainName=play.yourdomain.com
&EndTime=2017-12-22T08:00:00Z
&StartTime=2017-12-21T08:00:00Z
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeLiveStreamsPublishListResponse>
	  <PageNum>2</PageNum>
	  <PageSize>10</PageSize>
	  <PublishInfo>
		    <LiveStreamPublishInfo>
			      <AppName>xchen</AppName>
			      <ClientAddr>10.175.60.33</ClientAddr>
			      <DomainName>test101.cdnpe.com</DomainName>
			      <EdgeNodeAddr>10.175.30.21</EdgeNodeAddr>
			      <PublishDomain>test101.cdnpe.com</PublishDomain>
			      <PublishTime>2015-12-02T03:05:53Z</PublishTime>
			      <PublishUrl>rtmp://test101.cdnpe.com/xchen</PublishUrl>
			      <StopTime>2015-12-02T03:11:19Z</StopTime>
			      <StreamName>testxchen</StreamName>
			      <StreamUrl>rtmp://xxx/xxxx</StreamUrl>
		    </LiveStreamPublishInfo>
	  </PublishInfo>
	  <RequestId>1C0E0C22-77B7-42AC-8212-AF99B2E0077F</RequestId>
	  <TotalNum>11</TotalNum>
	  <TotalPage>2</TotalPage>
</DescribeLiveStreamsPublishListResponse>
```

`JSON` 格式

```
{
  "DescribeLiveStreamsPublishListResponse": {
    "PageNum": "2",
    "PageSize": "10",
    "PublishInfo": {
      "LiveStreamPublishInfo": {
        "AppName": "xchen",
        "ClientAddr": "10.175.60.33",
        "DomainName": "test101.cdnpe.com",
        "EdgeNodeAddr": "10.175.30.21",
        "PublishDomain": "test101.cdnpe.com",
        "PublishTime": "2015-12-02T03:05:53Z",
        "PublishUrl": "rtmp://test101.cdnpe.com/xchen",
        "StopTime": "2015-12-02T03:11:19Z",
        "StreamName": "testxchen",
        "StreamUrl": "rtmp://xxx/xxxx"
      }
    },
    "RequestId": "1C0E0C22-77B7-42AC-8212-AF99B2E0077F",
    "TotalNum": "11",
    "TotalPage": "2"
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidStartTime.Malformed|Specified parameter StartTime is not valid.|StartTime参数错误，请您确认该StartTime参数是否正确。|
|400|InvalidEndTime.Malformed|Specified parameter EndTime is not valid.|结束时间错误，请您确认结束时间是否正确。|

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


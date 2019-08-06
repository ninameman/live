# DescribeCasterVideoResources {#doc_api_live_DescribeCasterVideoResources .reference}

调用DescribeCasterVideoResources查询视频源。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeCasterVideoResources&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeCasterVideoResources|系统规定参数，取值：**DescribeCasterVideoResources**。

 |
|CasterId|String|是|80787064-1c94-4dc1-85ce-9409960a9bf0|导播台ID。

 |
|RegionId|String|否|cn-shanghai|地域。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CF60DB6A-7FD6-426E-9288-122CC1A52FA7|请求ID。

 |
|VideoResources| | |资源列表。

 |
|ResourceId|String|b5f8c837-ceeb-424f-b30b-68e94e864995|资源ID。

 |
|ResourceName|String|resource-Name1|资源名称。

 |
|LocationId|String|RV01|视频源位置，坑位号。

 |
|LiveStreamUrl|String|rtmp://XXXXXX/appName/b5447c21fcfe444c9e9b6f7ba208f141|直播流地址。

 |
|MaterialId|String|d2c429cd907742ee8f6e76465ad3c784|素材ID。

 |
|RepeatNum|Integer|0|仅对文件视频有效，表示播放完后重复继续播放的次数。

 -   **0（默认值）**：表示不重复播放
-   **-1**：表示一直循环重复

 |
|BeginOffset|Integer|1000|仅对文件视频有效， 单位：毫秒\(ms\) 。

 **大于0**，表示从相对于首帧的偏差时间作为开始读取的位置。

 |
|EndOffset|Integer|10000|仅对文件视频有效，单位：毫秒\(ms\)。

 -   **大于0**时，表示从相对于首帧的偏差时间为结束读取的位置。
-   **小于0**时，表示相对于最后一帧的偏差时间作为结束读取的位置。

 |
|PtsCallbackInterval|Integer|0|点播文件的回调间隔，等于0时为不回调。

 |
|VodUrl|String|http://XXXXXX/XXXXXX/XXXXXX.flv|点播文件地址。

 当且仅当资源为文件视频，且视频文件未导入素材库时使用，仅限**mp4/flv/ts**格式。

 |
|Total|Integer|2|总记录数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://live.aliyuncs.com?Action=DescribeCasterVideoResources
&CasterId=80787064-1c94-4dc1-85ce-9409960a9bf0
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeCasterVideoResourcesResponse>
	  <RequestId>CF60DB6A-7FD6-426E-9288-122CC1A52FA7</RequestId>
	  <VideoResource>
		    <ResourceId>b5f8c837-ceeb-424f-b30b-68e94e864995</ResourceId>
		    <ResourceName>resource-Name1</ResourceName>
		    <LocationId>RV01</LocationId>
		    <LiveStreamUrl>rtmp://XXXXXX/appName/b5447c21fcfe444c9e9b6f7ba208f141</LiveStreamUrl>
	  </VideoResource>
	  <VideoResource>
		    <ResourceId>b5f8c837-ceeb-424f-b30b-68e94e864995</ResourceId>
		    <MaterialId>d2c429cd907742ee8f6e76465ad3c784</MaterialId>
		    <ResourceName>resource-Name3</ResourceName>
		    <LocationId>RV02</LocationId>
		    <BeginOffset>1000</BeginOffset>
            <EndOffset>10000</EndOffset>
            <PtsCallbackInterval>0</PtsCallbackInterval>
	  </VideoResource>
</DescribeCasterVideoResourcesResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"VideoResources":[
		{
			"LocationId":"RV01",
			"ResourceId":"b5f8c837-ceeb-424f-b30b-68e94e864995",
			"ResourceName":"resource-Name1",
			"LiveStreamUrl":"rtmp://XXXXXX/appName/b5447c21fcfe444c9e9b6f7ba208f141"
		},
		{
			"EndOffset":10000,
			"LocationId":"RV02",
			"RepeatNum":2,
			"ResourceId":"b5f8c837-ceeb-424f-b30b-68e94e864995",
			"PtsCallbackInterval":0,
			"MaterialId":"d2c429cd907742ee8f6e76465ad3c784",
			"ResourceName":"resource-Name3",
			"BeginOffset":1000
		}
	],
	"RequestId":"CF60DB6A-7FD6-426E-9288-122CC1A52FA7"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


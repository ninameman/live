# ModifyCasterVideoResource {#doc_api_live_ModifyCasterVideoResource .reference}

调用ModifyCasterVideoResource修改视频资源。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=ModifyCasterVideoResource&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyCasterVideoResource|系统规定参数，取值：**ModifyCasterVideoResource**。

 |
|CasterId|String|是|80787064-1c94-4dc1-85ce-9409960a9bf0|导播台ID。

 |
|ResourceId|String|是|05ab713c-676e-49c0-96ce-cc408da1b314|资源ID。

 |
|BeginOffset|Integer|否|0|仅对文件视频有效，BeginOffset值大于0，表示从相对于首帧的偏差时间作为开始读取的位置。 单位：毫秒\(ms\) 。

 |
|EndOffset|Integer|否|10000|仅对文件视频有效，单位：毫秒\(ms\) 。

 -   EndOffset值大于0时，表示从相对于首帧的偏差时间为结束读取的位置。
-   EndOffset值小于0时，表示相对于最后一帧的偏差时间作为结束读取的位置。

 |
|LiveStreamUrl|String|否|rtmp://XXXXXX/XXX/XXXXXX|直播流地址。

 |
|MaterialId|String|否|f080575eb5f4427684fc0715159ab3cd|素材ID。

 |
|PtsCallbackInterval|Integer|否|2000|PTS回调间隔，单位ms，仅对点播素材有效。

 |
|RegionId|String|否|cn-shanghai|地域。

 |
|RepeatNum|Integer|否|2|仅对文件视频有效，表示播放完后重复继续播放的次数。

 -   **0（默认值）**：表示不重复播放。
-   **-1**：表示一直循环重复。

 |
|ResourceName|String|否|test001|视频源名称。

 |
|VodUrl|String|否|http://XXXXXX/XXX/XXXXXX.flv|点播文件地址。

 当且仅当资源为文件视频，且视频文件未导入素材库时使用，仅限**mp4、flv、ts、mov**格式。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CF60DB6A-7FD6-426E-9288-122CC1A52FA7|请求ID。

 |
|CasterId|String|80787064-1c94-4dc1-85ce-9409960a9bf0|导播台ID。

 |
|ResourceId|String|98461064-1c94-4dc1-85ce-940987645632|资源ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=ModifyCasterVideoResource
&CasterId=80787064-1c94-4dc1-85ce-9409960a9bf0
&ResourceId=05ab713c-676e-49c0-96ce-cc408da1b314
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyCasterVideoResourceResponse>
	  <RequestId>CF60DB6A-7FD6-426E-9288-122CC1A52FA7</RequestId>
      <CasterId>80787064-1c94-4dc1-85ce-9409960a9bf0</CasterId>
      <ResourceId>98461064-1c94-4dc1-85ce-940987645632</ResourceId>
</ModifyCasterVideoResourceResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"CasterId":"80787064-1c94-4dc1-85ce-9409960a9bf0",
	"ResourceId":"98461064-1c94-4dc1-85ce-940987645632",
	"RequestId":"CF60DB6A-7FD6-426E-9288-122CC1A52FA7"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


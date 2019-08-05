# AddCasterVideoResource {#doc_api_live_AddCasterVideoResource .reference}

调用AddCasterVideoResource添加视频源，视频源数量受限于导播台输入路数。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=AddCasterVideoResource&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddCasterVideoResource|系统规定参数，取值：**AddCasterVideoResource**。

 |
|CasterId|String|是|80787064-1c94-4dc1-85ce-9409960a9bf0|导播台ID。

 |
|ResourceName|String|是|test001|视频源名称。

 |
|BeginOffset|Integer|否|1000|仅对文件视频有效， 单位：毫秒\(ms\) 。

 **说明：** 大于0，表示从相对于首帧的偏差时间作为开始读取的位置。

 |
|EndOffset|Integer|否|10000|仅对文件视频有效，单位：毫秒\(ms\)。

 **说明：** 

-   大于0时，表示从相对于首帧的偏差时间为结束读取的位置。
-   小于0时，表示相对于最后一帧的偏差时间作为结束读取的位置。

 |
|LiveStreamUrl|String|否|http://live.aliyun.com/AppName/StreamName.flv|直播流地址，视频源类型为直播流时必选。

 |
|LocationId|String|否|RV01|用于标识视频源位置，定义布局内画面的引用编号，每个位置至多关联一个资源，格式需符合“RV01…RV12”。

 |
|MaterialId|String|否|f080575eb5f4427684fc0715159ab3cd|媒资库素材ID，视频源类型为素材时必选。

 |
|PtsCallbackInterval|Integer|否|2000|PTS回调间隔。

 |
|RegionId|String|否|cn-shanghai|区域。

 |
|RepeatNum|Integer|否|2|仅对文件视频有效，表示播放完后重复继续播放的次数。

 **说明：** 其中，**0（默认值）**表示不重复播放。**-1**表示一直循环重复。

 |
|VodUrl|String|否|http://live.aliyun.com/AppName/StreamName.flv|点播文件地址，当且仅当资源为文件视频，且视频文件未导入素材库时使用，仅限**mp4、flv、ts**格式。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CF60DB6A-7FD6-426E-9288-122CC1A52FA7|请求ID。

 |
|ResourceId|String|e5542d98-b08c-46bf-83e9-5b09d08c692f|资源ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=AddCasterVideoResource
&CasterId=80787064-1c94-4dc1-85ce-9409960a9bf0
&ResourceName=test001
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddCasterVideoResourceResponse>
	  <RequestId>CF60DB6A-7FD6-426E-9288-122CC1A52FA7</RequestId>
	  <ResourceId>e5542d98-b08c-46bf-83e9-5b09d08c692f</ResourceId>
</AddCasterVideoResourceResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"ResourceId":"e5542d98-b08c-46bf-83e9-5b09d08c692f",
	"RequestId":"CF60DB6A-7FD6-426E-9288-122CC1A52FA7"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


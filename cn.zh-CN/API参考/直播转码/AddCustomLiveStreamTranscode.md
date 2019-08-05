# AddCustomLiveStreamTranscode {#doc_api_live_AddCustomLiveStreamTranscode .reference}

调用AddCustomLiveStreamTranscode添加自定义转码配置信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=AddCustomLiveStreamTranscode&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddCustomLiveStreamTranscode|系统规定参数。取值：**AddCustomLiveStreamTranscode**。

 |
|App|String|是|AppName|直播流所属应用名称。

 可包含数字、大小写字母、下划线\("\_"\)或短横线\("-"\)。

 |
|Domain|String|是|live.aliyunlive.com|您的加速域名。

 |
|Template|String|是|LDtest|转码模板自定义名称。

 取值要求：数字、大小写字母或短横线\("-"\)。

 **说明：** 不能与标准的转码模板命名重复。

 |
|TemplateType|String|是|h264|自定义转码模版类型。目前支持：

 -   **h264**\(自定义H264标准模版\)
-   **h264-nbhd**\(自定义H264窄带高清™模版\)
-   **h265**\(自定义H265标准模版\)
-   **h265-nbhd**\(自定义H265窄带高清模版\)
-   **audio纯音频模板**

 |
|AudioBitrate|Integer|否|512|转码音频比特率。单位: kbps，取值范围：1 ≤AudioBitrate ≤ 1000。

 |
|AudioChannelNum|Integer|否|2|音频声道数。可选值：**1** | **2** 。

 |
|AudioCodec|String|否|aac|音频编码器。可选值：**aac** | **mp3**。

 |
|AudioProfile|String|否|aac\_low|音频编码Profile。可选值

 -   aac\_low
-   aac\_he
-   aac\_he\_v2
-   aac\_ld，采样率不能超过44100

 |
|AudioRate|Integer|否|96000|音频采样率。取值：**22050~96000**。

 **说明：** 如果是 aac\_ld, 则采样率不能超过44100

 |
|FPS|Integer|否|30|转码视频帧率。单位：fps，取值范围：1~60。

 |
|Gop|String|否|1|视频GOP。单位: 帧，取值要求：1 ≤ Gop ≤ 3000。

 |
|Height|Integer|否|720|转码视频宽度。

 -   取值范围：Width≥ 100
-   max\(Height,Width\) ≤ 2560
-   min\(Height,Width\) ≤ 1440

 **说明：** 265窄带高清模板不得超过1280\*720

 |
|Profile|Integer|否|2|视频GOP。取值：

 -   **1**：baseline
-   **2**：main
-   **3**：high

 |
|RegionId|String|否|cn-shanghai|所属区域。

 |
|VideoBitrate|Integer|否|720|转码视频比特率。单位：kbps，取值范围：1~6000。

 **说明：** 转码视频会尽量接近您所设定的比特率, 但转码视频的实际比特率不能保证和您所设定的完全一致, 尤其是当您设定的比特率过大或过小时。

 |
|Width|Integer|否|576|转码视频宽度。

 -   取值要求：Width ≥ 100
-   max\(Height,Width\) ≤ 2560
-   min\(Height,Width\) ≤ 1440

 **说明：** 265窄带高清模板不得超过1280\*720

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=AddCustomLiveStreamTranscode
&App=AppName
&Domain=live.aliyunlive.com
&FPS=30
&Height=720
&Template=LDtest
&TemplateType=h264
&VideoBitrate=720
&Width=576
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddCustomLiveStreamTranscodeResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
</AddCustomLiveStreamTranscodeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


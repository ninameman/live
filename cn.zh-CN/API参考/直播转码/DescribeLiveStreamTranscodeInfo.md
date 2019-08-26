# DescribeLiveStreamTranscodeInfo {#doc_api_live_DescribeLiveStreamTranscodeInfo .reference}

调用DescribeLiveStreamTranscodeInfo查询转码配置信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveStreamTranscodeInfo&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveStreamTranscodeInfo|系统规定参数。取值：**DescribeLiveStreamTranscodeInfo**。

 |
|DomainTranscodeName|String|是|play.aliyunlive.com|您的加速域名。

 |
|RegionId|String|否|cn-shanghai|地域。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DomainTranscodeList| | |转码配置信息。

 |
|TranscodeName|String|play.aliyunlive.com|播放域名。

 |
|TranscodeApp|String|app|应用名称。

 |
|TranscodeTemplate|String|lld|转码模版，目前有：

 -   标准质量模板：lld、lsd、lhd、lud
-   高品质（窄带高清™转码）模板：ld、sd、hd、ud

 |
|CustomTranscodeParameters| | |用户自定义转码配置。

 |
|AudioBitrate|Integer|64|音频码率

 |
|AudioChannelNum|Integer|2|音频声道数

 |
|AudioCodec|String|aac|音频编码

 |
|AudioProfile|String|low|音频profile

 |
|AudioRate|Integer|44100|音频采样率

 |
|FPS|Integer|15|转码视频帧率，单位：fps

 |
|Gop|String|10|GOP大小（Group of Picture）

 |
|Height|Integer|1200|转码视频高度

 |
|TemplateType|String|h264|自定义转码模版类型

 |
|VideoBitrate|Integer|3000|转码视频比特率，单位：kbps

 |
|VideoProfile|String|high|视频profile

 |
|Width|Integer|1000|转码视频宽度

 |
|RequestId|String|62136AE6-7793-45ED-B14A-60D19A9486D3|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=DescribeLiveStreamTranscodeInfo
&DomainTranscodeName=play.aliyunlive.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveStreamTranscodeInfoResponse>
	  <DomainTranscodeList>
		    <DomainTranscodeInfo>
			      <TranscodeApp>xxxx</TranscodeApp>
			      <TranscodeName>xxxx</TranscodeName>
			      <TranscodeTemplate>xxxx</TranscodeTemplate>
		    </DomainTranscodeInfo>
		    <DomainTranscodeInfo>
			      <CustomTranscodeParameters>
				        <FPS>25</FPS>
				        <Height>720</Height>
				        <Type>h264</Type>
				        <VideoBitrate>2000</VideoBitrate>
				        <Width>1280</Width>
			      </CustomTranscodeParameters>
			      <TranscodeApp>yyyy</TranscodeApp>
			      <TranscodeName>yyyy</TranscodeName>
			      <TranscodeTemplate>yyyy</TranscodeTemplate>
		    </DomainTranscodeInfo>
	  </DomainTranscodeList>
	  <RequestId>62136AE6-7793-45ED-B14A-60D19A9486D3</RequestId>
</DescribeLiveStreamTranscodeInfoResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"DomainTranscodeList":{
		"DomainTranscodeInfo":[
			{
				"TranscodeTemplate":"xxxx",
				"TranscodeName":"xxxx",
				"TranscodeApp":"xxxx"
			},
			{
				"TranscodeTemplate":"yyyy",
				"TranscodeName":"yyyy",
				"TranscodeApp":"yyyy",
				"CustomTranscodeParameters":{
					"VideoBitrate":2000,
					"FPS":25,
					"Type":"h264",
					"Height":720,
					"Width":1280
				}
			}
		]
	},
	"RequestId":"62136AE6-7793-45ED-B14A-60D19A9486D3"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


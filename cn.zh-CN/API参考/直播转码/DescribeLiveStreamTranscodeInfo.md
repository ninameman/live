# DescribeLiveStreamTranscodeInfo {#doc_api_990470 .reference}

查询转码配置信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=live&api=DescribeLiveStreamTranscodeInfo)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveStreamTranscodeInfo|系统规定参数。取值：**DescribeLiveStreamTranscodeInfo**

 |
|DomainTranscodeName|String|是|play.aliyunlive.com|您的加速域名。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DomainTranscodeList| | |转码配置信息。

 |
|└TranscodeName|String|play.aliyunlive.com|播放域名。

 |
|└TranscodeApp|String|app|应用名称。

 |
|└TranscodeTemplate|String|lld|转码模版，目前有：

 -   标准质量模板：lld、lsd、lhd、lud，
-   高品质（窄带高清™转码）模板：ld、sd、hd、ud

 |
|└CustomTranscodeParameters| | |用户自定义转码配置。

 |
|└FPS|Integer|15|转码视频帧率, 单位：fps。

 |
|└Height|Integer|1200|转码视频高度。

 |
|└TemplateType|String|h264|自定义转码模版类型。

 |
|└VideoBitrate|Integer|3000|转码视频比特率, 单位: kbps。

 |
|└Width|Integer|1000|转码视频宽度。

 |
|RequestId|String|62136AE6-7793-45ED-B14A-60D19A9486D3|该条任务请求 ID。

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

[查看本产品错误码](https://error-center.aliyun.com/status/product/live)


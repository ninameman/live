# DescribeCasterStreamUrl {#doc_api_live_DescribeCasterStreamUrl .reference}

调用DescribeCasterStreamUrl查询导播台流信息列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeCasterStreamUrl&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeCasterStreamUrl|系统规定参数，取值：**DescribeCasterStreamUrl**。

 |
|CasterId|String|是|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播台ID。

 |
|RegionId|String|否|cn-shanghai|地域。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |
|CasterId|String|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播台ID。

 |
|CasterStreams| | |导播台流信息列表。

 |
|SceneId|String|23ca74e0-aca3-4e7a-8561-9d96f525dd4a|场景ID。

 |
|StreamUrl|String|http://XXX/caster/YYY.flv|输出流地址。

 |
|OutputType|Integer|1|是否正式输出。

 -   **0**：输出预览
-   **1**：输出正式

 |
|StreamInfos| | |播放地址列表。

 |
|TranscodeConfig|String|lld|转码配置。

 -   lsd：标清
-   lld：流畅
-   lud：超清
-   lhd：高清

 |
|VideoFormat|String|flv|格式。取值：**flv，rtmp，m3u8**。

 |
|OutputStreamUrl|String|http://XXX/caster/YYY\_lld.flv|播放地址。

 |
|Total|Integer|1|数量。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeCasterStreamUrl
&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeCasterStreamUrlResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <CasterId>a2b8e671-2fe5-4642-a2ec-bf93880e1a49</CasterId>
	  <CasterStreams>
		    <StreamUrl>rtmp://XXXXXX/caster/1975ee99db904ebb83908d43bc878188?auth_key=1506396160-0-0-063397072a9980fd418d43eb00e02e09</StreamUrl>
		    <SceneId>23ca74e0-aca3-4e7a-8561-9d96f525dd4a</SceneId>
		    <OutputType>1</OutputType>
		    <StreamInfos>
			      <VideoFormat>flv</VideoFormat>
			      <OutputStreamUrl>http://XXXXXX/caster/fb628e2469f94f2aa2c0c219af8b2527_lld.flv?auth_key=1506396160-0-0-7de771a77102680861853af862d5eaf0</OutputStreamUrl>
			      <TranscodeConfig>lld</TranscodeConfig>
		    </StreamInfos>
		    <StreamInfos>
			      <VideoFormat>rtmp</VideoFormat>
			      <OutputStreamUrl>rtmp://XXXXXX/caster/fb628e2469f94f2aa2c0c219af8b2527_lld?auth_key=1506396160-0-0-77ed32cd82ed32ccd51a832b5765814c</OutputStreamUrl>
			      <TranscodeConfig>lld</TranscodeConfig>
		    </StreamInfos>
		    <StreamInfos>
			      <VideoFormat>m3u8</VideoFormat>
			      <OutputStreamUrl>http://XXXXXX/caster/fb628e2469f94f2aa2c0c219af8b2527.m3u8?auth_key=1506396160-0-0-d51f0512dcf76aa749f79f53ae6421d2</OutputStreamUrl>
			      <TranscodeConfig>lld</TranscodeConfig>
		    </StreamInfos>
	  </CasterStreams>
	  <CasterStreams>
		    <StreamUrl>rtmp://XXXXXX/caster/3a2e3cf978f3496f96d44e28b54295fa?auth_key=1506396160-0-0-6182084bd33e93a72029764f5cfbdc21</StreamUrl>
		    <SceneId>9445dbed-7aef-4cae-925f-8a3a026fc120</SceneId>
		    <OutputType>0</OutputType>
	  </CasterStreams>
</DescribeCasterStreamUrlResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"CasterId":"a2b8e671-2fe5-4642-a2ec-bf93880e1a49",
	"CasterStreams":[
		{
			"StreamInfos":[
				{
					"TranscodeConfig":"lld",
					"OutputStreamUrl":"http://XXXXXX/caster/fb628e2469f94f2aa2c0c219af8b2527_lld.flv?auth_key=1506396160-0-0-7de771a77102680861853af862d5eaf0",
					"VideoFormat":"flv"
				},
				{
					"TranscodeConfig":"lld",
					"OutputStreamUrl":"rtmp://XXXXXX/caster/fb628e2469f94f2aa2c0c219af8b2527_lld?auth_key=1506396160-0-0-77ed32cd82ed32ccd51a832b5765814c",
					"VideoFormat":"rtmp"
				},
				{
					"TranscodeConfig":"lld",
					"OutputStreamUrl":"http://XXXXXX/caster/fb628e2469f94f2aa2c0c219af8b2527.m3u8?auth_key=1506396160-0-0-d51f0512dcf76aa749f79f53ae6421d2",
					"VideoFormat":"m3u8"
				}
			],
			"StreamUrl":"rtmp://XXXXXX/caster/1975ee99db904ebb83908d43bc878188?auth_key=1506396160-0-0-063397072a9980fd418d43eb00e02e09",
			"OutputType":1,
			"SceneId":"23ca74e0-aca3-4e7a-8561-9d96f525dd4a"
		},
		{
			"StreamUrl":"rtmp://XXXXXX/caster/3a2e3cf978f3496f96d44e28b54295fa?auth_key=1506396160-0-0-6182084bd33e93a72029764f5cfbdc21",
			"OutputType":0,
			"SceneId":"9445dbed-7aef-4cae-925f-8a3a026fc120"
		}
	],
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


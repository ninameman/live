# DescribeCasterScenes {#doc_api_live_DescribeCasterScenes .reference}

调用DescribeCasterScenes查询场景信息列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeCasterScenes&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeCasterScenes|系统规定参数，取值：**DescribeCasterScenes**。

 |
|CasterId|String|是|80787064-1c94-4dc1-85ce-9409960a9bf0|导播台ID。

 |
|SceneId|String|否|b5f8c837-ceeb-424f-b30b-68e94e864995|场景ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CF60DB6A-7FD6-426E-9288-122CC1A52FA7|请求ID。

 |
|SceneList| | |场景信息列表。

 |
|SceneId|String|b5f8c837-ceeb-424f-b30b-68e94e864995|场景ID。

 |
|SceneName|String|scene1|场景名称。

 |
|OutputType|String|0|是否正式输出。

 -   **0**：输出预监
-   **1**：输出正式

 |
|LayoutId|String|37cb2f8b-f152-4338-b928-6704f71dbf41|布局ID。

 |
|StreamUrl|String|rtmp://XXX/caster/YYY|输出流地址。

 |
|ComponentIds| |1506396160-0-0-7de771a77102680861853af862d5eaf0|组件Id列表。

 |
|Status|Integer|0|场景状态。

 -   **0**：关闭
-   **1**：开启

 |
|StreamInfos| | |播放地址列表。

 |
|OutputStreamUrl|String|http://XXX/caster/YYY.flv|播放地址。

 |
|TranscodeConfig|String|lld|转码配置。取值：

 -   **sd**：标清
-   **lld**：流畅
-   **lud**：超清
-   **lhd**：高清

 |
|VideoFormat|String|flv|格式。取值：**flv** | **mp4** | **m3u8**。

 |
|Total|Integer|2|总记录数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeCasterScenes
&CasterId=80787064-1c94-4dc1-85ce-9409960a9bf0
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeCasterScenesResponse>
	  <RequestId>CF60DB6A-7FD6-426E-9288-122CC1A52FA7</RequestId>
	  <SceneList>
		    <SceneId>b5f8c837-ceeb-424f-b30b-68e94e864995</SceneId>
		    <SceneName>scene1</SceneName>
		    <LayoutId>37cb2f8b-f152-4338-b928-6704f71dbf41</LayoutId>
		    <StreamUrl>rtmp://XXXXXX/XXXXXX/b5447c21fcfe444c9e9b6f7ba208f141</StreamUrl>
		    <OutputType>0</OutputType>
		    <Status>1</Status>
	  </SceneList>
	  <SceneList>
		    <SceneId>86f661ee-c893-4aae-a852-ccacf2001dad</SceneId>
		    <SceneName>scene2</SceneName>
		    <StreamUrl>rtmp://XXXXXX/XXXXXX/37087ce7a76e424bbb61e8b5eefe76ed</StreamUrl>
		    <OutputType>1</OutputType>
		    <Status>1</Status>
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
	  </SceneList>
</DescribeCasterScenesResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"CF60DB6A-7FD6-426E-9288-122CC1A52FA7",
	"SceneList":[
		{
			"Status":1,
			"StreamUrl":"rtmp://XXXXXX/XXXXXX/b5447c21fcfe444c9e9b6f7ba208f141",
			"OutputType":0,
			"SceneName":"scene1",
			"SceneId":"b5f8c837-ceeb-424f-b30b-68e94e864995",
			"LayoutId":"37cb2f8b-f152-4338-b928-6704f71dbf41"
		},
		{
			"Status":1,
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
			"StreamUrl":"rtmp://XXXXXX/XXXXXX/37087ce7a76e424bbb61e8b5eefe76ed",
			"OutputType":1,
			"SceneName":"scene2",
			"SceneId":"86f661ee-c893-4aae-a852-ccacf2001dad"
		}
	]
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


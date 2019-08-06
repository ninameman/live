# StartCaster {#doc_api_live_StartCaster .reference}

调用StartCaster启动导播台。若PVW、PGM场景不存在则创建，启动PVW、PGM场景，启动底层音视频处理任务。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=StartCaster&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|StartCaster|系统规定参数，取值：**StartCaster**。

 |
|CasterId|String|是|80787064-1c94-4dc1-85ce-9409960a9bf0|导播台ID。

 |
|RegionId|String|否|cn-shanghai|地域。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6EBD1AC4-C34D-4AE1-963E-B688A228BE31|请求ID。

 |
|PvwSceneInfos| | |PVW场景信息列表。

 |
|SceneId|String|b5f8c837-ceeb-424f-b30b-68e94e864995|场景ID。

 |
|StreamUrl|String|http://XXX/caster/YYY.flv|导播台PVW场景对应播放流地址，非旁路输出流地址。

 |
|PgmSceneInfos| | |PGM场景信息列表。

 |
|SceneId|String|b5f8c837-ceeb-424f-b30b-68e94e864996|场景ID。

 |
|StreamUrl|String|http://XXX/caster/ZZZ.flv|导播台PGM场景对应播放流地址，非旁路输出流地址。

 |
|StreamInfos| | |旁路输出播放地址列表。

 |
|TranscodeConfig|String|lld|转码配置。 取值：

 -   **lsd**：标清
-   **lld**：流畅
-   **lud**：超清
-   **lhd**：高清

 |
|VideoFormat|String|flv|格式：**flv** | **rtmp** | **m3u8**。

 |
|OutputStreamUrl|String|http://XXX/caster/MMM.flv|播放地址。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://live.aliyuncs.com?Action=StartCaster
&CasterId=80787064-1c94-4dc1-85ce-9409960a9bf0
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<StartCasterResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <PvwSceneInfos>
		    <SceneId>b5f8c837-ceeb-424f-b30b-68e94e864995</SceneId>
		    <StreamUrl>rtmp://XXXXXX/caster/1975ee99db904ebb83908d43bc878188?auth_key=1506396160-0-0-063397072a9980fd418d43eb00e02e09</StreamUrl>
	  </PvwSceneInfos>
	  <PgmSceneInfos>
		    <SceneId>b5f8c837-ceeb-424f-b30b-68e94e864996</SceneId>
		    <StreamUrl>rtmp://XXXXXX/caster/1975ee99db904ebb83908d43bc878188?auth_key=1506396160-0-0-063397072a9980fd418d43eb00e02e10</StreamUrl>
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
	  </PgmSceneInfos>
</StartCasterResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PvwSceneInfos":[
		{
			"StreamUrl":"rtmp://XXXXXX/caster/1975ee99db904ebb83908d43bc878188?auth_key=1506396160-0-0-063397072a9980fd418d43eb00e02e09",
			"SceneId":"b5f8c837-ceeb-424f-b30b-68e94e864995"
		}
	],
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
	"PgmSceneInfos":[
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
			"StreamUrl":"rtmp://XXXXXX/caster/1975ee99db904ebb83908d43bc878188?auth_key=1506396160-0-0-063397072a9980fd418d43eb00e02e10",
			"SceneId":"b5f8c837-ceeb-424f-b30b-68e94e864996"
		}
	]
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


# UpdateCasterSceneAudio {#doc_api_live_UpdateCasterSceneAudio .reference}

调用UpdateCasterSceneAudio更新场景音频配置。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=UpdateCasterSceneAudio&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateCasterSceneAudio|系统规定参数，取值：**UpdateCasterSceneAudio**。

 |
|CasterId|String|是|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播台ID。

 |
|SceneId|String|是|a2b8e671-2fe5-4642-a2ec-bf93880e19876|场景ID。

 |
|AudioLayer.N.FixedDelayDuration|Integer|否|0|该字段对视频进行固定延迟设置，可用于字幕同步。

 单位：**ms**，取值范围：**0~5000**，默认值：**0**。

 |
|AudioLayer.N.ValidChannel|String|否|all|确定哪些声道可以作为音量输入。

 取值范围：**leftChannel** | **rightChannel** | **all（默认值）**

 |
|AudioLayer.N.VolumeRate|Float|否|1|调节音频流的音量大小倍数。取值范围：**0~10.0**，默认值：**1.0** 。

 -   **1.0**：表示保持原有音量
-   **小于1**：表示降低音量的倍数
-   **大于1**：表示放大的倍数

 |
|FollowEnable|Integer|否|1|是否启用音频跟随。 默认启用音频跟随，为空则保持最近一次配置不变。

 -   **0**：混音模式，
-   **1**：音频跟随视频模式

 |
|MixList.N|RepeatList|否|RV01|资源位置locationId关联列表。

 与audioLayers顺序保持一致，若启用Channel时，引用Channel的LocationId，否则引用视频源的LocationId。

 |
|RegionId|String|否|cn-shanghai|地域。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://live.aliyuncs.com?Action=UpdateCasterSceneAudio
&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49
&SceneId=a2b8e671-2fe5-4642-a2ec-bf93880e19876
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UpdateCasterSceneAudioResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
</UpdateCasterSceneAudioResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


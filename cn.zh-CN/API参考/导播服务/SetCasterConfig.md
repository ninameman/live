# SetCasterConfig {#doc_api_live_SetCasterConfig .reference}

调用SetCasterConfig配置导播台，全量覆盖配置信息，若指定参数置为空则清除导播台该项配置。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=SetCasterConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetCasterConfig|系统规定参数，取值：**SetCasterConfig**。

 |
|CasterId|String|是|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播台ID。

 |
|CallbackUrl|String|否|http://XXXXXX/XXXXXXX|用户回调地址。若需要接收回调通知，请输入可用的接收地址，接受http协议。 若该参数置为空，默认取消导播台回调通知。

 |
|CasterName|String|否|caster001|导播台名称。

 |
|ChannelEnable|Integer|否|1|是否启用Channel。

 -   **0（默认）**：不启用。
-   **1**：启用。

 **说明：** 默认不启用，且启用后不可取消；不启用时Resource直接被布局引用，首次开启Channel需要在导播台停止的状态下进行，之前已存在的布局将被废弃，Resource需要首先设置到Channel中，新增的布局直接引用Channel，通过Channel可调整视频源播放进度和播放状态，该模式下视频源、PVW、PGM三区域若引用同一Resource，则对应画面将保持同步。

 |
|Delay|Float|否|0|延时播放。

 -   0（默认值）：禁用延时
-   大于0：为启用延时
-   时间单位：秒
-   若该参数置为空，默认清除延播配置。

 |
|DomainName|String|否|test.live.com|域名。

 请您在导播台启动前完成域名配置。 若该参数为空，默认清除导播台域名配置。

 |
|ProgramEffect|Integer|否|1|轮播生效标志。

 -   **0**：不生效
-   **1**：生效

 |
|ProgramName|String|否|program\_name|轮播台名称，若使用轮播功能时可配置。

 |
|RecordConfig|String|否|\{ "endpoint": "XXXXXX", "ossBucket": "XXXXXX", "videoFormat": \["flv","m3u8" \] "interval": 5 \}|录制配置。

 参数设置为空时表示不启用录制功能。 JSON格式字符串，结构体内部字段请按首字母大写，驼峰格式输入。 若该参数置为空，默认清除录制配置。

 |
|RegionId|String|否|cn-shanghai|地域。

 |
|SideOutputUrl|String|否|http://XXXXXX/XXXXXXX|用户自定义导播台旁路输出地址。 若该参数为空，则默认使用阿里云自动生成的输出地址。

 |
|TranscodeConfig|String|否|lld|转码配置。

 JSON格式字符串，结构体内部字段请按首字母大写，驼峰格式输入。 若该参数设置为空，默认清除转码配置。

 |
|UrgentMaterialId|String|否|a2b8e671|备播视频，媒资库素材Id若该参数置为空，默认清除备播配置。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|CasterId|String|b4810848-bcf9-4aef-bd4a-e6bba2d966c8|导播台ID。

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=SetCasterConfig
&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetCasterConfigResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <casterId>b4810848-bcf9-4aef-bd4a-e6bba2d966c8</casterId>
</SetCasterConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"casterId":"b4810848-bcf9-4aef-bd4a-e6bba2d966c8",
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


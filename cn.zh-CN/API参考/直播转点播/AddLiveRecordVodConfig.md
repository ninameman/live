# AddLiveRecordVodConfig {#doc_api_live_AddLiveRecordVodConfig .reference}

调用AddLiveRecordVodConfig增加直播录制转点播配置，将录制内容保存到点播媒资库。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=AddLiveRecordVodConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddLiveRecordVodConfig|系统规定参数，取值：**AddLiveRecordVodConfig**。

 |
|AppName|String|是|testApp|直播流所属应用名称。

 支持通配符（\*），代表该域名下所有的AppName，不能与普通录制设置的AppName重复。

 |
|DomainName|String|是|www.yourdomain.com|您的加速域名。

 |
|VodTranscodeGroupId|String|是|e2d796d3bb5fd8049d32bff62f940711|点播转码模板组ID。

 |
|AutoCompose|String|否|OFF|是否开启自动合并。

 -   **ON**：开启
-   **OFF**：关闭

 |
|ComposeVodTranscodeGroupId|String|否|XXXXXX|自动合并点播转码模板组ID。

 **说明：** 如果开启了自动合成，则该字段必填。

 |
|CycleDuration|Integer|否|300|周期录制时长，单位为秒。默认值为**3600**，可取值为**300~21600**。

 |
|RegionId|String|否|cn-shanghai|区域。

 |
|StorageLocation|String|否|xxx-tjptr2vatm.oss-cn-shanghai.aliyuncs.com|登录点播控制台，找存储管理，复制存储地址

 |
|StreamName|String|否|stream|流名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=AddLiveRecordVodConfig
&AppName=testApp
&DomainName=www.yourdomain.com
&VodTranscodeGroupId=e2d796d3bb5fd8049d32bff62f940711
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddLiveRecordVodConfigResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
</AddLiveRecordVodConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|ConfigAlreadyExists|Config has already exist.|配置已添加。|

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


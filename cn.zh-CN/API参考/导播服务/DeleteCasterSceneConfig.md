# DeleteCasterSceneConfig {#doc_api_live_DeleteCasterSceneConfig .reference}

调用DeleteCasterSceneConfig清除指定场景的配置信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DeleteCasterSceneConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteCasterSceneConfig|系统规定参数，取值：**DeleteCasterSceneConfig**。

 |
|CasterId|String|是|b4810848-bcf9-4aef-bd4a-e6bba2d966c8|导播台ID。

 |
|SceneId|String|是|b5f8c837-ceeb-424f-b30b-68e94e864995|场景ID。

 |
|Type|String|是|Component|可取值：

 -   **Component**：清除组件配置
-   **Layou**：清除布局配置
-   **All**：清除组件和布局配置

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://live.aliyuncs.com?Action=DeleteCasterSceneConfig
&CasterId=b4810848-bcf9-4aef-bd4a-e6bba2d966c8
&SceneId=b5f8c837-ceeb-424f-b30b-68e94e864995
&Type=Component
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteCasterSceneConfigResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
</DeleteCasterSceneConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


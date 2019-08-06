# SetCasterSceneConfig {#doc_api_live_SetCasterSceneConfig .reference}

调用SetCasterSceneConfig全量设置场景配置，清空场景配置，并将布局信息设置并生效至指定场景。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=SetCasterSceneConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetCasterSceneConfig|系统规定参数，取值：**SetCasterSceneConfig**。

 |
|CasterId|String|是|80787064-1c94-4dc1-85ce-9409960a9bf0|导播台ID。

 |
|SceneId|String|是|242b4e2c-c30f-4442-85ba-2e3e4e3dec1b|场景ID。

 |
|ComponentId.N|RepeatList|否|ids|组件ID列表，数组内按照由下至上的顺序排列组件。

 |
|LayoutId|String|否|0c6da077-f037-49e8-8440-3be133938359|布局ID。

 |
|RegionId|String|否|cn-shanghai|地域。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CF60DB6A-7FD6-426E-9288-122CC1A52FA7|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=SetCasterSceneConfig
&CasterId=80787064-1c94-4dc1-85ce-9409960a9bf0
&SceneId=242b4e2c-c30f-4442-85ba-2e3e4e3dec1b
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetCasterSceneConfigResponse>
	  <RequestId>CF60DB6A-7FD6-426E-9288-122CC1A52FA7</RequestId>
</SetCasterSceneConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"CF60DB6A-7FD6-426E-9288-122CC1A52FA7"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


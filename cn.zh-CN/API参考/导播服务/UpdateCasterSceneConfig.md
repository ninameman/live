# UpdateCasterSceneConfig {#doc_api_live_UpdateCasterSceneConfig .reference}

调用UpdateCasterSceneConfig增量设置场景配置，不清空原配置，布局信息在原场景上增量修改，效率较全量设置高。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=UpdateCasterSceneConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UpdateCasterSceneConfig|系统规定参数，取值：**UpdateCasterSceneConfig**。

 |
|CasterId|String|是|80787064-1c94-4dc1-85ce-9409960a9bf0|导播台ID。

 |
|LayoutId|String|是|eeab74fb-379d-4599-a93d-86d16a05f92d|布局ID。

 |
|SceneId|String|是|242b4e2c-c30f-4442-85ba-2e3e4e3dec1b|场景ID。

 |
|ComponentId.N|RepeatList|否|98778372-c30f-4442-85ba-2e3e4e3dec1b|组件ID列表，数组内按照由下至上的顺序排列组件。

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

http(s)://[Endpoint]/?Action=UpdateCasterSceneConfig
&CasterId=80787064-1c94-4dc1-85ce-9409960a9bf0
&LayoutId=eeab74fb-379d-4599-a93d-86d16a05f92d
&SceneId=242b4e2c-c30f-4442-85ba-2e3e4e3dec1b
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UpdateCasterSceneConfigResponse>
	  <RequestId>CF60DB6A-7FD6-426E-9288-122CC1A52FA7</RequestId>
</UpdateCasterSceneConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"CF60DB6A-7FD6-426E-9288-122CC1A52FA7"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


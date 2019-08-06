# StartCasterScene {#doc_api_live_StartCasterScene .reference}

调用StartCasterScene启动指定场景，限制仅用于PVW的打开。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=StartCasterScene&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|StartCasterScene|系统规定参数，取值：**StartCasterScene**。

 |
|CasterId|String|是|80787064-1c94-4dc1-85ce-9409960a9bf0|导播台ID。

 |
|SceneId|String|是|242b4e2c-c30f-4442-85ba-2e3e4e3dec1b|场景ID，PVW场景时有效。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CF60DB6A-7FD6-426E-9288-122CC1A52FA7|请求ID。

 |
|StreamUrl|String|http://XXXXXX/caster/XXXXXX.flv|当前场景的输出流地址。用于导播台播放，非旁路输出

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=StartCasterScene
&CasterId=80787064-1c94-4dc1-85ce-9409960a9bf0
&SceneId=242b4e2c-c30f-4442-85ba-2e3e4e3dec1b
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<StartCasterSceneResponse>
	  <RequestId>CF60DB6A-7FD6-426E-9288-122CC1A52FA7</RequestId>
      <RequestId>http://XXXXXX/caster/XXXXXX.flv</RequestId>
</StartCasterSceneResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"StreamUrl":"http://XXXXXX/caster/XXXXXX.flv",
	"RequestId":"CF60DB6A-7FD6-426E-9288-122CC1A52FA7"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


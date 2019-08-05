# DeleteCasterVideoResource {#doc_api_live_DeleteCasterVideoResource .reference}

调用DeleteCasterVideoResource删除视频资源。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DeleteCasterVideoResource&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteCasterVideoResource|系统规定参数，取值：**DeleteCasterVideoResource**。

 |
|CasterId|String|是|80787064-1c94-4dc1-85ce-9409960a9bf0|导播台ID。

 |
|ResourceId|String|是|05ab713c-676e-49c0-96ce-cc408da1b314|资源ID。

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

http(s)://[Endpoint]/?Action=DeleteCasterVideoResource
&CasterId=80787064-1c94-4dc1-85ce-9409960a9bf0
&ResourceId=05ab713c-676e-49c0-96ce-cc408da1b314
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteCasterVideoResourceResponse>
	  <RequestId>CF60DB6A-7FD6-426E-9288-122CC1A52FA7</RequestId>
</DeleteCasterVideoResourceResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"CF60DB6A-7FD6-426E-9288-122CC1A52FA7"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


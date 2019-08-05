# CopyCasterSceneConfig {#doc_api_live_CopyCasterSceneConfig .reference}

调用CopyCasterSceneConfig将原场景配置应用至目标场景并生效，仅限PVW场景配置拷贝至PGM场景。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=CopyCasterSceneConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CopyCasterSceneConfig|系统规定参数，取值：**CopyCasterSceneConfig**。

 |
|CasterId|String|是|80787064-1c94-4dc1-85ce-9409960a9bf0|导播台ID。

 |
|FromSceneId|String|是|f1a361f4-bee3-436d-ae6e-d38e69437666|原场景ID，仅限于PVM场景。

 |
|ToSceneId|String|是|05ab713c-676e-49c0-96ce-cc408da1b314|目标场景ID，仅限于PGM场景。

 |
|RegionId|String|否|cn-shanghai|区域。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CF60DB6A-7FD6-426E-9288-122CC1A52FA7|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=CopyCasterSceneConfig
&CasterId=80787064-1c94-4dc1-85ce-9409960a9bf0
&FromSceneId=f1a361f4-bee3-436d-ae6e-d38e69437666
&ToSceneId=05ab713c-676e-49c0-96ce-cc408da1b314
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CopyCasterSceneConfigResponse>
	  <RequestId>CF60DB6A-7FD6-426E-9288-122CC1A52FA7</RequestId>
</CopyCasterSceneConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"CF60DB6A-7FD6-426E-9288-122CC1A52FA7"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


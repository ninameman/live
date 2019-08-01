# StopLiveDomain {#doc_api_live_StopLiveDomain .reference}

调用StopLiveDomain停用某个直播域名，将DomainStatus变更为offline。

**说明：** 停用该直播域名后，该条直播域名信息仍保留，针对直播域名的请求，系统将自动回源处理。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=StopLiveDomain&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|StopLiveDomain|系统规定参数，取值：**StopLiveDomain**。

 |
|DomainName|String|是|live.yourdomain.com|直播域名。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|324AEFFF-308C-4DA7-8CD3-01B277B98F28|请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=StopLiveDomain
&DomainName=live.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<StopLiveDomainResponse>
	  <RequestId>324AEFFF-308C-4DA7-8CD3-01B277B98F28</RequestId>
</StopLiveDomainResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"324AEFFF-308C-4DA7-8CD3-01B277B98F28"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


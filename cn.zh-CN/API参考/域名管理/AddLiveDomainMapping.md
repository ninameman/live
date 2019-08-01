# AddLiveDomainMapping {#doc_api_live_AddLiveDomainMapping .reference}

调用AddLiveDomainMapping添加直播域名播流域名和推流域名的映射关系配置。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=AddLiveDomainMapping&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddLiveDomainMapping|系统规定参数，取值：**AddLiveDomainMapping**。

 |
|PullDomain|String|是|play.yourdomain.com|您的播流域名，域名类型为**liveVideo**。

 |
|PushDomain|String|是|push.yourdomain.com|您的推流域名，域名类型为**liveEdge**。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=AddLiveDomainMapping
&PullDomain=play.yourdomain.com
&PushDomain=push.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddLiveDomainMappingResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
</AddLiveDomainMappingResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


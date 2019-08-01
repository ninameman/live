# DeleteLiveDomain {#doc_api_live_DeleteLiveDomain .reference}

调用DeleteLiveDomain删除已添加的直播域名。

**说明：** 请慎重操作（建议您在进行域名删除前到域名解析服务商处恢复域名A记录），以免导致删除操作后此域名不可访问。

**DeleteLiveDomain**调用成功后，将删除本条直播域名的全部相关记录，对于仅需要暂停使用该直播域名的用户，推荐**StopLiveDomain**接口。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DeleteLiveDomain&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteLiveDomain|系统规定参数，取值：**DeleteLiveDomain**。

 |
|DomainName|String|是|live.yourdomain.com|要删除的域名。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|94E3559F-7B6A-4A5E-AFFD-44E2A208A249|请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DeleteLiveDomain
&DomainName=live.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteLiveDomainResponse>
	  <RequestId>94E3559F-7B6A-4A5E-AFFD-44E2A208A249</RequestId>
</DeleteLiveDomainResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"94E3559F-7B6A-4A5E-AFFD-44E2A208A249"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


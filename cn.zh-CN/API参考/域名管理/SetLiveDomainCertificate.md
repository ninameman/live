# SetLiveDomainCertificate {#doc_api_live_SetLiveDomainCertificate .reference}

调用SetLiveDomainCertificate设置某域名下证书功能是否启用及修改证书信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=SetLiveDomainCertificate&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetLiveDomainCertificate|系统规定参数，取值：**SetLiveDomainCertificate**。

 |
|DomainName|String|是|play.yourdomain.com|指定证书所属加速域名。属于`https`加速类型。

 |
|SSLProtocol|String|是|off|HTTPS证书是否启用。取值：

 -   **on**：启用
-   **off（默认值）**：不启用

 |
|CertName|String|否|证书1|证书名称。

 |
|SSLPri|String|否|XXX|私钥内容。

 不启用证书则无需输入，配置证书请输入私钥内容。

 |
|SSLPub|String|否|XXX|安全证书内容。

 不启用证书则无需输入，配置证书请输入证书内容。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=SetLiveDomainCertificate
&DomainName=play.yourdomain.com
&SSLProtocol=off
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetLiveDomainCertificateResponse>
	  <RequestId>0AEDAF20-4DDF-4165-8750-47FF9C1929C9</RequestId>
</SetLiveDomainCertificateResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"0AEDAF20-4DDF-4165-8750-47FF9C1929C9"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|IllegalOperation|Illegal domain operate is not permitted.|接口权限不足，请您联系管理员，配置访问权限。|

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


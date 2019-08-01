# DescribeLiveCertificateList {#doc_api_990439 .reference}

获取证书列表信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=live&api=DescribeLiveCertificateList)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveCertificateList|操作接口名，系统规定参数

 DescribeLiveCertificateList

 |
|DomainName|String|否|live.yourdomain.com|域名

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|CertificateListModel| | |数据类型

 |
|└CertList| | |数据类型

 |
|└CertId|Long|123|证书id

 |
|└CertName|String|证书名称|证书名称

 |
|└Common|String|test|Common

 |
|└Fingerprint|String|xxx|Fingerprint

 |
|└Issuer|String|xxx|证书发行商

 |
|└LastTime|Long|1512388659|时间

 |
|└Count|Integer|1|证书个数

 |
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=DescribeLiveCertificateList
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveCertificateListResponse>
  <CertificateListModel>
    <Count>2</Count>
    <CertList>
      <Cert>
        <CertName>证书1</CertName>
        <Issuer>xxx</Issuer>
        <LastTime>1512388610</LastTime>
        <CertId>xxx</CertId>
        <Common>test</Common>
        <Fingerprint>xxx</Fingerprint>
      </Cert>
      <Cert>
        <CertName>证书2</CertName>
        <Issuer>xxx</Issuer>
        <LastTime>1512388659</LastTime>
        <CertId>xxx</CertId>
        <Common>test</Common>
        <Fingerprint>xxx</Fingerprint>
      </Cert>
    </CertList>
  </CertificateListModel>
  <RequestId>FC0E34AC-0239-44A7-AB0E-800DE522C8DA</RequestId>
</DescribeLiveCertificateListResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"CertificateListModel":{
		"Count":2,
		"CertList":{
			"Cert":[
				{
					"CertId":"xxx",
					"Issuer":"xxx",
					"LastTime":1512388610,
					"CertName":"证书1",
					"Common":"test",
					"Fingerprint":"xxx"
				},
				{
					"CertId":"xxx",
					"Issuer":"xxx",
					"LastTime":1512388659,
					"CertName":"证书2",
					"Common":"test",
					"Fingerprint":"xxx"
				}
			]
		}
	},
	"RequestId":"FC0E34AC-0239-44A7-AB0E-800DE522C8DA"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/live)


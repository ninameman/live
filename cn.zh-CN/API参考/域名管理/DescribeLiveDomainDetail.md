# DescribeLiveDomainDetail {#doc_api_live_DescribeLiveDomainDetail .reference}

调用DescribeLiveDomainDetail获取指定直播域名配置的基本信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveDomainDetail&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveDomainDetail|要执行的操作。取值：**DescribeLiveDomainDetail**。

 |
|DomainName|String|是|live.yourdomain.com|直播域名名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DomainDetail| | |直播域名名称。

 |
|CertName|String|testCertName|若开启`https`，表示为证书名称。

 |
|Cname|String|live.yourdomain.com.m.test.net|为直播域名生成一个CNAME域名，需要在域名解析服务商处将直播域名CNAME解析到该域名。

 |
|Description|String|test|域名备注，说明信息。

 |
|DomainName|String|live.yourdomain.com|直播域名。

 |
|DomainStatus|String|online|直播域名运行状态。取值：

 -   **online**：启用
-   **offline**：停用
-   **configuring**：配置中

 |
|GmtCreated|String|2018-07-27T06:51:25Z|创建时间。

 |
|GmtModified|String|2018-08-07T06:51:25Z|最近修改时间。

 |
|LiveDomainType|String|liveVideo|直播域名类型。

 |
|Region|String|cn-shanghai|域名所在区域。

 |
|SSLProtocol|String|on|是否开启ssl证书。取值：

 -   **on**：开启
-   **off**：关闭

 |
|SSLPub|String|xxxxxxxxxxxxpublickey|若开启`https`，表示为证书公钥。

 |
|Scope|String|domestic|加速区域。

 返回值范围：**domestic**,**overseas**,**global**。

 |
|RequestId|String|09ABE829-6CD3-4FE0-AFEE-556113E29727|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeLiveDomainDetail
&DomainName=live.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveDomainDetailResponse>
	  <DomainDetail>
		    <Cname>bb.test.com.scdn7mhp.com</Cname>
		    <DomainName>bb.test.com</DomainName>
		    <DomainStatus>online</DomainStatus>
		    <GmtCreated>2017-11-27T06:51:25Z</GmtCreated>
		    <GmtModified>2017-11-27T06:51:26Z</GmtModified>
		    <LiveDomainType>liveVideo</LiveDomainType>
		    <Region>cn-beijing</Region>
		    <Scope>domestic</Scope>
	  </DomainDetail>
	  <RequestId>09ABE829-6CD3-4FE0-AFEE-556113E29727</RequestId>
</DescribeLiveDomainDetailResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"09ABE829-6CD3-4FE0-AFEE-556113E29727",
	"DomainDetail":{
		"Cname":"bb.test.com.scdn7mhp.com",
		"Region":"cn-beijing",
		"LiveDomainType":"liveVideo",
		"DomainStatus":"online",
		"DomainName":"bb.test.com",
		"GmtModified":"2017-11-27T06:51:26Z",
		"GmtCreated":"2017-11-27T06:51:25Z",
		"Scope":"domestic"
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


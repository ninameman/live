# DescribeLiveUserDomains {#doc_api_live_DescribeLiveUserDomains .reference}

调用DescribeLiveUserDomains查询用户名下所有的直播域名。

支持域名模糊匹配过滤、域名所处region过滤。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeLiveUserDomains&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLiveUserDomains|系统规定参数，取值：**DescribeLiveUserDomains**。

 |
|DomainName|String|否|\*.testdomain.com|域名模糊匹配过滤。

 不传值，默认查询用户所有直播域名。

 |
|DomainSearchType|String|否|fuzzy\_match|域名查询类型。取值：

 -   **fuzzy\_match（默认值）**：模糊匹配
-   **pre\_match**：前匹配
-   **suf\_match**：后匹配
-   **full\_match**：完全匹配

 |
|DomainStatus|String|否|online|域名状态过滤。域名状态包括：

 -   **online**：运行中（表示域名服务状态正常）
-   **offline**：已停止
-   **configuring**：配置中

 |
|LiveDomainType|String|否|liveVideo|直播域名业务类型，不传查询所有。

 取值：**liveVideo**|**liveEdge**。

 |
|PageNumber|Integer|否|1|当前页码。取值范围：**1~100000**。

 |
|PageSize|Integer|否|100|分页大小。默认值为**20**，最大值为**50**。

 |
|RegionName|String|否|cn-beijing|域名所属区域。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Domains| | |由PageData组成的数组格式，返回直播域名的状态信息。

 |
|Cname|String|xingzu-bj.alivecdn.com.w.alikunlun.net|直播域名对应的CNAME域名。

 |
|Description|String|test|备注说明。

 |
|DomainName|String|live.yourdomain.com|直播域名名称。

 |
|GmtCreated|String|2017-08-29T12:15:36Z|直播域名创建时间。

 |
|GmtModified|String|2017-12-29T12:15:36Z|直播域名修改时间。

 |
|LiveDomainStatus|String|online|直播域名状态。取值：

 -   **online**：启用
-   **offline**：停用
-   **configuring**：配置中
-   **configure\_failed**：配置失败
-   **checking**：正在审核
-   **check\_failed**：审核失败

 |
|LiveDomainType|String|liveVideo|直播域名业务类型。

 |
|RegionName|String|cn-beijing|域名所属区域。

 |
|PageNumber|Long|1|返回数据的当前页码。

 |
|PageSize|Long|100|分页大小。

 |
|RequestId|String|E4EBD2BF-5EB0-4476-8829-9D94E1B15267|请求ID。

 |
|TotalCount|Long|2|总条数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=DescribeLiveUserDomains
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLiveUserDomainsResponse>
      <Domains>
		    <PageData>
			      <Cname>xingzu-bj.alivecdn.com.w.alikunlun.net</Cname>
			      <Description></Description>
			      <DomainName>xingzu-bj.alivecdn.com</DomainName>
			      <GmtCreated>2017-08-29T12:15:36Z</GmtCreated>
			      <GmtModified>2017-12-29T09:24:08Z</GmtModified>
			      <LiveDomainStatus>offline</LiveDomainStatus>
			      <LiveDomainType>liveVideo</LiveDomainType>
			      <RegionName>cn-beijing</RegionName>
		    </PageData>
		    <PageData>
			      <Cname>kehan-bj.alivecdn.com.w.alikunlun.net</Cname>
			      <Description>浙ICP备12022327号</Description>
			      <DomainName>kehan-bj.alivecdn.com</DomainName>
			      <GmtCreated>2017-08-29T08:40:53Z</GmtCreated>
			      <GmtModified>2017-12-29T09:24:12Z</GmtModified>
			      <LiveDomainStatus>offline</LiveDomainStatus>
			      <LiveDomainType>liveVideo</LiveDomainType>
			      <RegionName>cn-beijing</RegionName>
		    </PageData>
	  </Domains>
	  <PageNumber>1</PageNumber>
	  <PageSize>100</PageSize>
	  <RequestId>E4EBD2BF-5EB0-4476-8829-9D94E1B15267</RequestId>
	  <TotalCount>2</TotalCount>
    </DescribeLiveUserDomainsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":2,
	"PageSize":100,
	"RequestId":"E4EBD2BF-5EB0-4476-8829-9D94E1B15267",
	"Domains":{
		"PageData":[
			{
				"Cname":"xingzu-bj.alivecdn.com.w.alikunlun.net",
				"Description":"",
				"RegionName":"cn-beijing",
				"LiveDomainType":"liveVideo",
				"DomainName":"xingzu-bj.alivecdn.com",
				"GmtModified":"2017-12-29T09:24:08Z",
				"GmtCreated":"2017-08-29T12:15:36Z",
				"LiveDomainStatus":"offline"
			},
			{
				"Cname":"kehan-bj.alivecdn.com.w.alikunlun.net",
				"Description":"浙ICP备12022327号",
				"RegionName":"cn-beijing",
				"LiveDomainType":"liveVideo",
				"DomainName":"kehan-bj.alivecdn.com",
				"GmtModified":"2017-12-29T09:24:12Z",
				"GmtCreated":"2017-08-29T08:40:53Z",
				"LiveDomainStatus":"offline"
			}
		]
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


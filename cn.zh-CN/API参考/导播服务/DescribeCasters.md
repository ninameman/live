# DescribeCasters {#doc_api_live_DescribeCasters .reference}

调用DescribeCasters查询导播台列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DescribeCasters&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeCasters|系统规定参数，取值：**DescribeCasters**。

 |
|CasterId|String|否|af2ace82-dc55-40b1-9fa3-688787214b1d|导播台ID。

 |
|CasterName|String|否|caster001|导播台名称。

 |
|StartTime|String|否|2016-06-29T19:00:00Z|起始时间，UTC 格式。 例如：`2016-06-29T19:00:00Z`。

 |
|EndTime|String|否|2016-06-29T21:00:00Z|结束时间。

 |
|PageNum|Integer|否|1|页码。

 |
|PageSize|Integer|否|5|每页条数。

 |
|Status|Integer|否|0|状态。

 -   **0**：空闲
-   **1**：导播中

 |
|RegionId|String|否|cn-shanghai|地域。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|CasterList| | |导播台信息列表。

 |
|CasterId|String|dce0f9c0-f65c-47cf-bc33-69387286e9c6|导播台ID。

 |
|CasterName|String|coco-caster2|导播台名称。

 |
|CasterTemplate|String|lp\_ld|导播台分辨率配置，付费类型为预付费时必选。

 -   **lp\_ld**：流畅
-   **lp\_sd**：标清
-   **lp\_hd**：高清
-   **lp\_ud**：超清
-   **lp\_ld\_v**：竖屏流畅
-   **lp\_sd\_v**：竖屏标清
-   **lp\_hd\_v**：竖屏高清
-   **lp\_ud\_v**：竖屏超清

 |
|ChannelEnable|Integer|1|是否启用Channel。

 -   **0**：不启用
-   **1**：启用

 |
|ChargeType|String|PrePaid|付费方式。 目前只支持**PostPaid**。

 -   **PrePaid**：预付费
-   **PostPaid**：后付费

 |
|CreateTime|String|2017-08-30 12:02:57.0|创建时间。

 |
|ExpireTime|String|2018-08-30 12:02:57.0|导播台过期时间。

 |
|NormType|Integer|1|导播台规格类型 。

 -   0：播单型
-   1：通用型

 |
|PurchaseTime|String|2017-08-30 12:02:57.0|导播台购买时间。

 |
|StartTime|String|2017-08-30 18:02:57.0|导播台启动时间，当导播台处于导播中时输出。

 |
|Status|Integer|1|状态。

 -   **0**：空闲
-   **1**：导播中

 |
|RequestId|String|6159ba01-6687-4fb2-a831-f0cd8d188648|请求ID。

 |
|Total|Integer|1|导播台数量。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=DescribeCasters
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeCastersResponse>
	  <RequestId>6159ba01-6687-4fb2-a831-f0cd8d188648</RequestId>
	  <CasterList>
		    <Status>0</Status>
		    <CasterName>coco-caster1</CasterName>
		    <NormType>1</NormType>
		    <ChargeType>PostPaid</ChargeType>
		    <CreateTime>2017-08-30 10:47:25.0</CreateTime>
		    <CasterId>af2ace82-dc55-40b1-9fa3-688787214b1d</CasterId>
	  </CasterList>
	  <CasterList>
		    <Status>0</Status>
		    <CasterName>coco-caster2</CasterName>
		    <NormType>1</NormType>
		    <ChargeType>PrePaid</ChargeType>
		    <Period>3</Period>
		    <CasterTemplate>lp_hd</CasterTemplate>
		    <CreateTime>2017-08-30 12:02:57.0</CreateTime>
		    <CasterId>dce0f9c0-f65c-47cf-bc33-69387286e9c6</CasterId>
	  </CasterList>
</DescribeCastersResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"6159ba01-6687-4fb2-a831-f0cd8d188648",
	"CasterList":[
		{
			"ChargeType":"PostPaid",
			"CasterId":"af2ace82-dc55-40b1-9fa3-688787214b1d",
			"Status":0,
			"CasterName":"coco-caster1",
			"NormType":1,
			"CreateTime":"2017-08-30 10:47:25.0"
		},
		{
			"Period":3,
			"ChargeType":"PrePaid",
			"CasterId":"dce0f9c0-f65c-47cf-bc33-69387286e9c6",
			"CasterTemplate":"lp_hd",
			"Status":0,
			"CasterName":"coco-caster2",
			"NormType":1,
			"CreateTime":"2017-08-30 12:02:57.0"
		}
	]
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


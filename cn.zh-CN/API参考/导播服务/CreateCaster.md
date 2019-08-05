# CreateCaster {#doc_api_live_CreateCaster .reference}

调用CreateCaster创建导播台。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=CreateCaster&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateCaster|系统规定参数，取值：**CreateCaster**。

 |
|ChargeType|String|是|PrePaid|付费方式。可取值：

 -   **PrePaid**：预付费
-   **PostPaid**：后付费

**说明：** 目前只支持PostPaid。


 |
|ClientToken|String|是|53200b81-b761-4c10-842a-a0726d972293|用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。

 |
|NormType|Integer|是|1|导播台规格类型。可取值：

 -   **0**：播单型
-   **1**：通用型

 |
|CasterName|String|否|coco-caster5|默认为**CasterId**。

 |
|CasterTemplate|String|否|lp\_sd|导播台预设分辨率。采用预付费方式时，取值：

 -   **lp\_ld**：流畅
-   **lp\_sd**：标清
-   **lp\_hd**：高清
-   **lp\_ud**：超清

 |
|ExpireTime|String|否|2017-08-22T12:10:10Z|导播台过期时间。

 |
|PurchaseTime|String|否|2017-08-20T12:10:10Z|导播台购买时间。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |
|CasterId|String|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播台ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=CreateCaster
&ChargeType=PrePaid
&ClientToken=53200b81-b761-4c10-842a-a0726d972293
&NormType=1
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateCasterResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
	  <CasterId>a2b8e671-2fe5-4642-a2ec-bf93880e1a49</CasterId>
</CreateCasterResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"CasterId":"a2b8e671-2fe5-4642-a2ec-bf93880e1a49",
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


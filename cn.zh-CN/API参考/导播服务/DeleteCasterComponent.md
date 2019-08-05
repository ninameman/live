# DeleteCasterComponent {#doc_api_live_DeleteCasterComponent .reference}

调用DeleteCasterComponent删除组件。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DeleteCasterComponent&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteCasterComponent|系统规定参数，取值：**DeleteCasterComponent**。

 |
|CasterId|String|是|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播间ID。

 |
|ComponentId|String|是|21926b36-7dd2-4fde-ae25-51b5bc8e52d8|组件ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |
|CasterId|String|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播台ID。

 |
|ComponentId|String|21926b36-7dd2-4fde-ae25-51b5bc8e52d8|组件ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://live.aliyuncs.com?Action=DeleteCasterComponent
&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49
&ComponentId=21926b36-7dd2-4fde-ae25-51b5bc8e52d8
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteCasterComponentResponse>
	  <requestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</requestId>
      <ComponentId>21926b36-7dd2-4fde-ae25-51b5bc8e52d8</ComponentId>
      <CasterId>a2b8e671-2fe5-4642-a2ec-bf93880e1a49</CasterId>
</DeleteCasterComponentResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"CasterId":"a2b8e671-2fe5-4642-a2ec-bf93880e1a49",
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8",
	"ComponentId":"21926b36-7dd2-4fde-ae25-51b5bc8e52d8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


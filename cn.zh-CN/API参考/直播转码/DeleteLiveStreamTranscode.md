# DeleteLiveStreamTranscode {#doc_api_live_DeleteLiveStreamTranscode .reference}

调用DeleteLiveStreamTranscode删除转码配置信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DeleteLiveStreamTranscode&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteLiveStreamTranscode|系统规定参数。取值：**DeleteLiveStreamTranscode**。

 |
|App|String|是|app|直播流所属应用名称。

 |
|Domain|String|是|play.aliyunlive.com|您的加速域名。

 |
|Template|String|是|lld|转码模版。目前有：

 -   标准质量模板：**lld**、**lsd**、**lhd**、**lud**。
-   高品质（窄带高清™转码）模板：**ld**、**sd**、**hd**、**ud**。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=DeleteLiveStreamTranscode
&App=app
&Domain=play.aliyunlive.com
&Template=lld
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteLiveStreamTranscodeResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
</DeleteLiveStreamTranscodeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


# DeleteLiveRecordVodConfig {#doc_api_live_DeleteLiveRecordVodConfig .reference}

调用DeleteLiveRecordVodConfig删除直播录制转点播配置。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DeleteLiveRecordVodConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteLiveRecordVodConfig|系统规定参数。取值：**DeleteLiveRecordVodConfig**。

 |
|AppName|String|是|testApp|直播流所属应用名称。

 |
|DomainName|String|是|www.yourdomain.com|您的加速域名。

 |
|RegionId|String|否|cn-hangzhou|区域。

 |
|StreamName|String|否|testApp|播流地址。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|40A4F36D-A7CC-473A-88E7-154F92242566|请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DeleteLiveRecordVodConfig
&AppName=testApp
&DomainName=www.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteLiveRecordVodConfigResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
</DeleteLiveRecordVodConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


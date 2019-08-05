# DeleteLiveAppRecordConfig {#doc_api_live_DeleteLiveAppRecordConfig .reference}

调用DeleteLiveAppRecordConfig解除录制配置。

通过**AddLiveAppRecordConfig**添加的配置，可以使用该接口删除。会删除DomainName、AppName、StreamName对应的配置。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=DeleteLiveAppRecordConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteLiveAppRecordConfig|系统规定参数。取值：**DeleteLiveAppRecordConfig**。

 |
|AppName|String|是|testApp|直播流所属应用名称。

 |
|DomainName|String|是|www.yourdomain.com|您的加速域名。

 |
|StreamName|String|否|teststream|流名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|6EBD1AC4-C34D-4AE1-963E-B688A228BE31|请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[live.aliyuncs.com]/?Action=DeleteLiveAppRecordConfig
&AppName=testApp
&DomainName=www.yourdomain.com
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteLiveAppRecordConfigResponse>
	  <RequestId>6EBD1AC4-C34D-4AE1-963E-B688A228BE31</RequestId>
</DeleteLiveAppRecordConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"6EBD1AC4-C34D-4AE1-963E-B688A228BE31"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


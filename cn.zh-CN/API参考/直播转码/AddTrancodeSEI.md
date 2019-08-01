# AddTrancodeSEI {#doc_api_live_AddTrancodeSEI .reference}

调用AddTrancodeSEI添加转码SEI信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=AddTrancodeSEI&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddTrancodeSEI|系统规定参数。取值：**AddTrancodeSEI**。

 |
|AppName|String|是|AppName|直播流所属应用名称。

 |
|Delay|Integer|是|100|接收到命令后的delay时间。单位： 毫秒。

 |
|DomainName|String|是|live.aliyunlive.com|您的加速域名。

 |
|Pattern|String|是|keyframe|追加到每一个关键帧/每一帧。取值：**keyframe** | **frame**。

 |
|Repeat|Integer|是|1|重复次数，-1代表无限。

 |
|StreamName|String|是|StreamName|流名称。

 |
|Text|String|是|firsttxt|SEI文本。长度限制：4000字节。

 |
|RegionId|String|否|cn-shanghai|区域。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=AddTrancodeSEI
&AppName=AppName
&Delay=100
&DomainName=live.aliyunlive.com
&Pattern=keyframe
&Repeat=1
&StreamName=StreamName
&Text=firsttxt
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddTrancodeSEIResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
</AddTrancodeSEIResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


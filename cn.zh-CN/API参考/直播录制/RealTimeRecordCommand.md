# RealTimeRecordCommand {#doc_api_live_RealTimeRecordCommand .reference}

调用RealTimeRecordCommand按需完成手动录制。例如，动态地启动、停止录制 。

您可以事先配置录制配置，但是设置默认行为是不录制（AddLiveAppRecordConfig设置OnDemand=7），直接通过手动录制的接口启动某条直播流的录制。

如果某条直播流正在录制（可能是自动录制，也可能是手动录制启动的），您也可以通过手动录制的接口停止该直播流的录制。

手动启动录制的直播流如果发生了断流，就会停止录制，并且重新推流后不会自动启动录制（如果没有配置自动录制）。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=RealTimeRecordCommand&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RealTimeRecordCommand|系统规定参数。取值：**RealTimeRecordCommand**。

 |
|AppName|String|是|testApp|App名。

 |
|Command|String|是|start|操作行为。支持start、stop两种类型。

 |
|DomainName|String|是|test.com|您的加速域名。

 |
|StreamName|String|是|testStream|直播流名。

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

http(s)://[live.aliyuncs.com]/?AppName=testApp
&Command=start
&DomainName=test.com
&StreamName=testStream
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<RealTimeRecordCommandResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
</RealTimeRecordCommandResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


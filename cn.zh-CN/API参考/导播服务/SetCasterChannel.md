# SetCasterChannel {#doc_api_live_SetCasterChannel .reference}

调用SetCasterChannel在视频源同步模式时，将视频资源设置到通道中。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=SetCasterChannel&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetCasterChannel|系统规定参数，取值：**SetCasterChannel**。

 |
|CasterId|String|是|a2b8e671-2fe5-4642-a2ec-bf93880e1a49|导播台ID。

 |
|ChannelId|String|是|RV01|通道ID。

 布局画面的引用编号，每个通道位置至多设置一个资源，数量受限于导播台创建时的通道路数。格式符合“RV01...RV12”。

 |
|PlayStatus|Integer|否|1|仅对文件视频有效，直播源无效。

 播放状态：

 -   **1（默认）**：播放
-   **0**：暂停

 |
|RegionId|String|否|cn-shanghai|地域。

 |
|ResourceId|String|否|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|视频源ID。

 |
|SeekOffset|Integer|否|1000|仅对文件视频有效，直播源无效，必须大于0，表示从相对于首帧的偏差时间作为开始读取的位置。 单位：毫秒\(ms\) 。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=SetCasterChannel
&CasterId=a2b8e671-2fe5-4642-a2ec-bf93880e1a49
&ChannelId=RV01
&ResourceId=16A96B9A-F203-4EC5-8E43-CB92E68F4CD8
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetCasterChannelResponse>
	  <RequestId>16A96B9A-F203-4EC5-8E43-CB92E68F4CD8</RequestId>
</SetCasterChannelResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"16A96B9A-F203-4EC5-8E43-CB92E68F4CD8"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


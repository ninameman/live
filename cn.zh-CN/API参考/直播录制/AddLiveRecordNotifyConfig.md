# AddLiveRecordNotifyConfig {#doc_api_live_AddLiveRecordNotifyConfig .reference}

调用AddLiveRecordNotifyConfig添加域名级别录制回调配置。

添加域名级别录制回调配置时，您可以添加以下内容：

-   录制回调（包括录制文件生成事件回调、录制任务状态回调）URL地址，详见 [录制事件回调](~~55016~~)。
-   按需录制回调URL地址 [按需录制回调](~~85910~~)。
-   是否需要录制任务状态回调。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=AddLiveRecordNotifyConfig&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddLiveRecordNotifyConfig|系统规定参数。取值：**AddLiveRecordNotifyConfig**。

 |
|DomainName|String|是|www.yourdomain.com|您的加速域名。

 |
|NotifyUrl|String|是|http://www.yourdomain.cn/examplecallback.action|录制回调（包括录制事件和状态回调） url 地址。

 -   必须以`http://`或者`https://`开头。
-   需要做url encode。

 |
|OnDemandUrl|String|否|http://www.yourdomain.cn/ondemandcallback.action|按需录制回调 url 地址。

 -   必须以`http://`或者`https://`开头。
-   需要做url encode。

 |
|NeedStatusNotify|Boolean|否|false|是否需要录制任务状态回调，可取值：**true | false**。

 默认值：false。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://live.aliyuncs.com/?Action=AddLiveRecordNotifyConfig
&DomainName=www.yourdomain.com
&NotifyUrl=http://www.yourdomain.cn/examplecallback.action
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddLiveRecordNotifyConfigResponse>
	  <RequestId>394966CA-5940-44D7-A1C5-24211C7B07A9</RequestId>
</AddLiveRecordNotifyConfigResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"394966CA-5940-44D7-A1C5-24211C7B07A9"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidNotifyUrl.Malformed|Specified NotifyUrl is invalid.|指定的notifyurl错误，请您确认该notifyurl参数是否正确。|
|400|InvalidNotifyUrl.Unsafe|Specified NotifyUrl is not safe.|指定的notifyurl错误，请您确认该notifyurl参数是否正确。|
|400|ConfigAlreadyExists|Config has already exist.|配置已添加。|

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


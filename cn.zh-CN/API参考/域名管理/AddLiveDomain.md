# AddLiveDomain {#doc_api_live_AddLiveDomain .reference}

调用AddLiveDomain添加直播域名，一次只能提交一个域名。

限制条件：

-   创建直播域名之前，必须先开通live服务。
-   直播域名必须已备案完成。

**说明：** 从2019年2月19日起，调用AddLiveDomain添加的域名不支持中心推流的方式（通过CDN API添加的新域名同样不支持中心推流），请使用边缘推流创建一个推流域名（调用AddLiveDomain，业务类型为liveEdge），一个播放域名（调用AddLiveDomain，业务类型为liveVideo），并做关联（调用AddLiveDomainMapping），之前创建的域名不受影响。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=live&api=AddLiveDomain&type=RPC&version=2016-11-01)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddLiveDomain| 

 系统规定参数，取值：**AddLiveDomain**。

 |
|DomainName|String|是|live.yourdomain.com|需要接入直播的域名。

 支持泛域名，以符号“.”开头，如：.a.com。

 |
|LiveDomainType|String|是|liveVideo|域名业务类型。取值：

 -   **liveVideo**：播流域名
-   **liveEdge**：边缘推流域名

 |
|Region|String|是|cn-beijing|直播域名单元化信息。目前单元化信息取值有**cn-beijing**、**cn-shanghai**、**ap-southeast-1**。

 |
|CheckUrl|String|否|http://live.yourdomain.com/status.html|检查域名是否能正常访问url。

 |
|Scope|String|否|domestic|加速区域。国际用户、国内L3及以上用户设置有效。取值范围：

 -   **domestic（默认值）**：国内
-   **overseas**：海外
-   **global**：全球

 |
|TopLevelDomain|String|否|www.yourTopLevelDomain|顶级调度域。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=AddLiveDomain
&DomainName=live.yourdomain.com
&LiveDomainType=liveVideo
&Region=cn-beijing
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddLiveDomainResponse>
	  <RequestId>15C66C7B-671A-4297-9187-2C4477247A74</RequestId>
</AddLiveDomainResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"15C66C7B-671A-4297-9187-2C4477247A74"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/live)查看更多错误码。


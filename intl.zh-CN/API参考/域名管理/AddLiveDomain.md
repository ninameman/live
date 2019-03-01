# AddLiveDomain {#doc_api_1033105 .reference}

添加直播域名，一次只能提交一个域名。

限制条件：

-   创建直播域名之前，必须先开通live服务。
-   直播域名必须已备案完成。

备注：从2019年2月19日起，调用AddLiveDomain添加的域名不支持中心推流的方式（通过CDN API添加的新域名同样不支持中心推流），请使用边缘推流创建一个推流域名（调用AddLiveDomain，业务类型为liveEdge），一个播放域名（调用AddLiveDomain，业务类型为liveVideo），并做关联（调用AddLiveDomainMapping），之前创建的域名不受影响。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=live&api=AddLiveDomain)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddLiveDomain| 

 操作接口名，系统规定参数。

 取值：**AddLiveDomain**

 |
|DomainName|String|是|live.yourdomain.com|需要接入直播的域名。

 支持泛域名，以符号“.”开头，如：.a.com。

 |
|LiveDomainType|String|是|liveVideo|域名业务类型

 取值：liveVideo、liveEdge，分别对应播流域名、边缘推流域名。

 |
|Region|String|是|cn-beijing|直播域名单元化信息。目前单元化信息取值有cn-beijing、cn-shanghai、ap-southeast-1。

 |
|CheckUrl|String|否|http://live.yourdomain.com/status.html|检查域名是否能正常访问url。

 |
|Scope|String|否|domestic|加速区域。

 -   取值范围：domestic、overseas、global，分别对应国内、海外、全球。
-   默认domestic。
-   国际用户、国内L3及以上用户设置有效。

 |
|TopLevelDomain|String|否|www.yourTopLevelDomain|顶级调度域

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|16A96B9A-F203-4EC5-8E43-CB92E68F4CD8|请求ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://live.aliyuncs.com/?Action=AddLiveDomain
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

[查看本产品错误码](https://error-center.aliyun.com/status/product/live)


# SDK集成指南 {#concept_pbf_t5b_pfb .concept}

本文介绍互动直播Android系统SDK集成。

## 集成环境 {#section_w2y_vvb_pfb .section}

以下要求为硬性要求：

|名称|要求|
|:-|:-|
|Android系统版本|≥Android 4.3|
|最小Android API版本|Jelly Bean \(API 18\)|
|CPU架构支持|ARM64、ARMV7|
|集成工具|Android Studio|

以下要求为开发此Demo时的开发环境，非硬性要求，目的是为了给编译运源码的人员提供参考。

|名称|要求|
|:-|:-|
|  Android Studio版本| 3.2.1|
| JRE:|1.8.0\_152-release-1136-b06 amd64|
| JVM:| OpenJDK 64-Bit |
| compileSdkVersion| 26|
| buildToolsVersion | 26.0.2 |
| minSdkVersion | 18|
| targetSdkVersion| 26|
| gradle version| gradle-4.4-all|
| gradle plugin version | com.android.tools.build:gradle:3.0.1|

## Demo下载 {#section_bjq_5nf_qgb .section}

 下载阿里云官网互动直播Android版本SDK，解压缩，Demo源码就包含在解压包的demo文件夹中。

## Demo运行 {#section_c4g_xnf_qgb .section}

打将ApsarVideoInteractiveLive的Demo工程导入到Android Studio中，其中app模块下MainActivity是页面入口Activity，如下图所示内容：

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24572/155436506438479_zh-CN.png)

其中Demo工程模块结构解释如下图所示：

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24572/155436506538480_zh-CN.png)

导入工程成功后，即可直接运行工程查看Demo效果。效果如下：

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24572/155436506538481_zh-CN.png)

## SDK文件说明 {#section_lr3_yvb_pfb .section}

使用互动直播SDK时需要集成sdk目录下所有文件到工程中。以下是官网互动直播SDK解压缩包内容。如图所示：

|文件目录|文件名称|文件说明|
|:---|:---|:---|
|apk|ApsarVideoInteractiveLive.apk|互动直播演示Demo APP安装文件|
|demo|ApsarVideoInteractiveLive|互动直播演示Demo源代码工程|
|doc|api.zip|互动直播API JavaDoc|
|sdk|interactive-liveroom-sdk-1.2.2.aar|互动直播间SDK|
|AlivcCore.jar|推流基础组件|
|live-face-beauty-3.3.7.aar|推流美颜组件|
|live-pusher-3.3.7.aar|推流SDK|
|AlivcReporter-1.2.0.aar|上报组件|
|AlivcPlayer-3.4.6.aar|播放器SDK|

**导入SDK**

正式集成SDK之前需要在主模块（一般是app \) 的build.gradle中 的 dependencies下添加如下依赖：

```
implementation 'org.eclipse.paho:org.eclipse.paho.client.mqttv3:1.1.0'
implementation 'org.apache.httpcomponents:httpcore:4.4.1'
```

**传统方式集成**

将所有SDK目录下文件拷贝到自己工程对应lib目录下，并修改主模块\(一般是app \) 的**build.gradle**中 的 **dependencies**，然后同步工程，如下图所示：

```
implementation fileTree(dir: 'libs', include: ['*.jar', '*.aar'])
```

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24572/155436506538488_zh-CN.png)

**maven仓库方式集成（推荐）**

在工程级目录下的 **build.gradle** 文件中添加maven仓库地址，在主模块（一般是app）的 **build.gradle** 中 的 **dependencies** 下添加依赖，然后同步工程。复制以下代码，添加到指定位置，如下图所示：

maven仓库地址：

```
maven {
    url "http://maven.aliyun.com/nexus/content/repositories/releases"
}
```

依赖语句：

```
implementation 'com.alivc.live:AliyunInteractiveLive:1.2.2'

```

**说明：** 本文档中使用的是 **implementation** 而非 **complie** , 这是gradle3.0+的新特性, 具体可查阅 [Google官方文档](https://developer.android.com/studio/build/gradle-plugin-3-0-0-migration?hl=zh-cn)，您可根据AndroidStudio版本自行选择。

工程级目录下的 **build.gradle** 文件：

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24572/155436506538490_zh-CN.png)

模块的 **build.gradle** 文件：

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/24572/155436506538491_zh-CN.png)

**添加权限**

在AndroidManifest文件下添加如下代码：

```
<uses-permission android:name="android.permission.INTERNET"/>
    <uses-permission android:name="android.permission.RECORD_AUDIO"/>
    <uses-permission android:name="android.permission.CAMERA"/>
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
    <uses-permission android:name="android.permission.MOUNT_UNMOUNT_FILESYSTEMS"/>
    <uses-permission android:name="android.permission.MODIFY_AUDIO_SETTINGS"/>
    <uses-permission android:name="android.permission.READ_PHONE_STATE"/>
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/>
    <uses-permission android:name="android.permission.BLUETOOTH" />
```

**说明：** 请您务必注意添加录音权限和相机权限。

**添加混淆文件**

在proguard-rules.pro文件下添加如下代码：

```
-keep class com.alivc.**{*;}
-dontwarn com.alivc.**

-keep class com.aliyun.**{*;}
-dontwarn com.aliyun.**
```


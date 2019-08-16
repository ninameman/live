# SDK integration {#concept_drc_txx_pfb .concept}

This topic describes how to integrate the Android stream ingest SDK.

## SDK information {#section_slj_dxk_nfb .section}

The following figure shows the directory structure of the downloaded **SDK** package.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40381/156593340055875_en-US.png)

-   The following figures show the directory structure of the **AlivcLivePusherSDK** folder, which does not include the Alibaba Cloud ApsaraVideo Player SDK.
    -   **aarlibs**

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40381/156593340055867_en-US.png)

    -   **jniLibs**

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40381/156593340155868_en-US.png)

    -   **libs**

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40381/156593340155869_en-US.png)

    -   **obj**, which is used to locate underlying problems

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40381/156593340155870_en-US.png)

-   The following figures show the directory structure of the **AlivcLivePusherSDK+AliyunPlayerSDK** folder, which includes the Alibaba Cloud ApsaraVideo Player SDK.
    -   **aarlibs**

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40381/156593340155871_en-US.png)

    -   **jniLibs**

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40381/156593340255873_en-US.png)

    -   **libs**

        ![](images/13972_en-US.png)

    -   **obj**, which is used to locate underlying problems

        ![](images/13973_en-US.png)

        **Note:** 

        -   To integrate the stream ingest SDK, you can import AAR packages, or JAR packages and SO files.
        -   To use the background music feature, you must integrate the Alibaba Cloud ApsaraVideo Player SDK \(AlivcPlayer.aar\) with your project. When importing AAR packages, you need to include the AlivcPlayer.aar file. When importing JAR packages and SO files, you need to import the AlivcPlayer.aar file at the application layer. In V3.2.0 and later versions, a debugging tool \(live-pusher-resources.aar\) has been added. To integrate this tool, you can import its AAR package the same way as you import the AlivcPlayer.aar file. This method also applies to the AlivcReporter.aar file.

## System requirements {#section_c4f_cyx_pfb .section}

-   Android 4.3 or a later version

-   CPU that supports ARM64 and ARMv7


## Operating environment {#section_uld_dyx_pfb .section}

-   Android 4.3 or a later version

-   Android Studio 2.3 or a later version

-   Application development environment compatible with the stream ingest SDK

-   Android SDK tools: android-sdk\_25.0.0

    -   minSdkVersion 18

    -   targetSdkVersion 23


## Integrate the SDK {#section_vf2_fyx_pfb .section}

To download a stream ingest SDK package, click [Download SDKs](https://help.aliyun.com/document_detail/45270.html?spm=a2c4g.11186623.2.30.6284161cvDZvBu).

1.  Create a project in Android Studio.

    ![](images/13974_en-US.png)

2.  Copy JAR packages and SO files.

    ![](images/13975_en-US.png)

3.  Configure the project.

    ``` {#codeblock_orr_5qu_u22}
    dependencies {
     implementation fileTree(dir: 'libs', include: ['*.jar'])
    }
    ```

    By default, SO files are stored in the jniLibs folder. To specify another folder to store SO files, you can add the following code to the build.gradle file of your application.

    ``` {#codeblock_mxa_6mz_yhk}
    sourceSets{ 
    main{ 
       jniLibs.srcDirs = ['libs'] 
    } 
    }
    ```

4.  Click Rebuild Project to compile the project.


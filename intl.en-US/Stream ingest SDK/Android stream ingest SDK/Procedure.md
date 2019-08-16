# Procedure {#concept_t4k_zwx_pfb .concept}

This topic describes how to use the Android stream ingest SDK during the basic stream ingest procedure and the live Q&A procedure.

## Basic stream ingest procedure {#section_s5s_r5k_fb .section}

1.  A user's application sends a request to the application server to obtain an ingest URL.
2.  The application server generates an ingest URL and returns it to the application.
3.  The application uses this URL to configure the stream ingest SDK and starts stream ingest.
4.  The stream ingest SDK ingests live streams to CDN.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20914/156592285013963_en-US.png)


## Live Q&A procedure {#section_pd2_kxx_pfb .section}

To implement live Q&A, you need to use the stream ingest SDK, the custom OBS, or an Alibaba Cloud API to insert SEI \(questions\) into live streams. After a user's player receives and parses the SEI, it sends a callback event notification to the user's application. Then, the user can receive and answer questions to participate in the live Q&A. The following figure shows the detailed procedure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/20914/156592285013964_en-US.png)

For more information about how to implement live Q&A, see [Live Q&A solution](https://help.aliyun.com/document_detail/66082.html?spm=a2c4g.11186623.2.18.6284161cM5dhId). You need to submit a ticket following instructions. For more information about the player, see [Basic player \(Live Q&A\)](https://help.aliyun.com/document_detail/61908.html?spm=a2c4g.11186623.2.19.6284161cM5dhId). For more information about OBS-based stream ingest, see [OBS-based live Q&A](https://help.aliyun.com/document_detail/66134.html?spm=a2c4g.11186623.2.20.6284161cM5dhId).


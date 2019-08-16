# Procedure {#concept_m5k_dsw_pfb .concept}

This topic describes how to use the iOS stream ingest SDK during the basic stream ingest procedure and the live Q&A procedure.

## Basic stream ingest procedure {#section_sfs_hsw_pfb .section}

1.  A user's application sends a request to the application server to obtain an ingest URL.
2.  The application server generates an ingest URL and returns it to the application.
3.  The application uses this URL to configure the stream ingest SDK and starts stream ingest.
4.  The stream ingest SDK ingests live streams to CDN.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40317/156593768355939_en-US.png)


## Live Q&A procedure {#section_oj3_msw_pfb .section}

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/40317/156593768355940_en-US.png)

To implement live Q&A, you need to use the stream ingest SDK, the custom OBS, or an Alibaba Cloud API to insert SEI \(questions\) into live streams. After a user's player receives and parses the SEI, it sends a callback event notification to the user's application. Then, the user can receive and answer questions to participate in the live Q&A. The following figure shows the detailed procedure.

For more information about how to implement live Q&A, see [Live Q&A solution](../../../../intl.en-US/Best Practices/Live Q&A scheme/Introduction.md#). You need to submit a ticket following instructions. For more information about the player, see [Basic player \(Live Q&A\)](https://help.aliyun.com/document_detail/61431.html?spm=a2c4g.11186623.2.20.310b592cC4piqk). For more information about OBS-based stream ingest, see [OBS-based live Q&A](../../../../intl.en-US/Best Practices/Live Q&A scheme/OBS-based live Q&A.md#).


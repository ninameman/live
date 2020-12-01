Bind a sub-streaming domain to a main streaming domain 
===========================================================================

This topic describes how to bind a sub-streaming domain to a main streaming domain, view the binding between streaming domains, and unbind a sub-streaming domain from its main streaming domain. To bind an ingest domain to multiple streaming domains, you must bind one or more sub-streaming domains to a main streaming domain.

Prerequisites 
----------------------------------

At least two streaming domains are available. For more information, see [Add a domain name](/intl.en-US/User Guide (New console)/Domain names management/Manage a domain name/Add a domain name.md).

Background information 
-------------------------------------------

After you bind one or more sub-streaming domains to a main streaming domain, an ingest domain can be bound to all these streaming domains.

An ingest domain can be bound to only one main streaming domain. To play an ingested stream by using multiple streaming domains, specify one of them as a main streaming domain and bind the others as sub-streaming domains to the main streaming domain.

![Main streaming domain and sub-streaming domain](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2295976061/p132145.png)
**Notice**

* Sub-streaming domains inherit the settings of the main streaming domain, such as the settings of stream ingest and transcoding. The settings that you configure for sub-streaming domains are invalid. For example, transcoding templates are valid only for main streaming domains.

  

* A sub-streaming domain cannot be nested to any other sub-streaming domains.

  

* After a streaming domain is configured as a sub-streaming domain, the business settings of the streaming domain become invalid. Before you perform this operation, make sure that no important online business exists. To avoid faults, we recommend that you use a new domain as a sub-streaming domain.

  




Configure a sub-streaming domain 
-----------------------------------------------------

1. Log on to the [ApsaraVideo Live console](https://live.console.aliyun.com/).

   

2. In the left-side navigation pane, click **Domains** .

   

3. On the **Domain Management** page, find the required main streaming domain and click **Domain Settings** in the Actions column.![Domains ](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7785976061/p184057.png)

   

4. On the **Basic Settings** page, click the **Streaming Information** tab and then **Configure Sub-streaming Domain** .![Streaming Information tab](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3295976061/p184164.png)

   

5. Select the required sub-streaming domain and click **OK** .![Add a domain](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3295976061/p184165.png)

   




View binding 
---------------------------------

1. Log on to the [ApsaraVideo Live console](https://live.console.aliyun.com/).

   

2. In the left-side navigation pane, click **Domains** .

   

3. On the **Domain Management** page, find the required main streaming domain and click **Domain Settings** in the Actions column.

   

4. On the **Basic Settings** page, click the **Streaming Information** tab to view the configuration.

   The following figure shows the streaming information about the main streaming domain and its sub-streaming domains.![View a main streaming domain and its sub-streaming domains](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3295976061/p184166.png)
   




Unbind a sub-streaming domain from its main streaming domain 
---------------------------------------------------------------------------------

1. Log on to the [ApsaraVideo Live console](https://live.console.aliyun.com/).

   

2. In the left-side navigation pane, click **Domains** .

   

3. On the **Domain Management** page, find the required main streaming domain and click **Domain Settings** in the Actions column.![Domains ](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7785976061/p184057.png)

   

4. On the **Basic Settings** page, click the **Streaming Information** tab, find the required sub-streaming domain, and then click **Unbind** .![Unbind](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3295976061/p184167.png)

   




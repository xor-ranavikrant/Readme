#**Analytics in the Microsoft Intelligent Data Platform**

*The estimated time to complete this lab is 45-60 minutes.*

##**Table of contents**

[***Exercise 1: Data ingestion from a spectrum of analytical and operational data sources into the Lakehouse***](#exercise-1-data-ingestion-from-a-spectrum-of-analytical-and-operational-data-sources-into-the-lakehouse)
  - Task 1.1: Explore a streaming data and analytics pipeline using ADX for a near real-time analytics scenario.
  - Task 1.2: Explore a few Synapse pipelines that ingest raw data from analytical data sources to the bronze layer of the Data Lake.
  - Task 1.3: Explore a few Synapse pipelines that ingest raw data from operational data sources to the bronze layer of the Data Lake.
	
[***Exercise 2: Explore the offline data and analytics pipeline using open Delta format and Azure Databricks Delta Live Tables. Stitch streaming and non-streaming data (landed earlier) to create a combined data product and build a simple Lakehouse***](#exercise-2-explore-offline-data-and-analytics-pipeline-using-open-delta-format-and-azure-databricks-delta-live-tables-stitch-streaming-and-non-streaming-data-landed-earlier-to-create-a-combined-data-product-to-build-a-simple-lakehouse)
  - Task 2.1: Set up an Azure Databricks environment.
  - Task 2.2: Review Sentiment Analysis model training.
  - Task 2.3: Create a Delta Live Table pipeline.
	
[***Exercise 3: Explore Machine Learning and Business Intelligence scenarios on the Lakehouse***](#exercise-3-explore-machine-learning-and-business-intelligence-scenarios-on-the-lakehouse)
  - Task 3.1: Review MLOps pipeline using the Azure Databricks managed MLflow.
  - Task 3.2: Leverage Power BI to derive actionable insights from data in the Lakehouse.
  - Task 3.3 (OPTIONAL): Explore SQL Analytics with Azure Synapse Serverless.
  - Task 3.4 (OPTIONAL): Explore SQL Analytics with Azure Databricks.
	
[***Exercise 4: Glimpse of Purview to govern the overall data and analytics estate***](#exercise-4-glimpse-of-purview-to-govern-the-overall-data-and-analytics-estate)

===

#**Overview**

![Analytics in MIDP](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/arch_1.png?raw=true)

The demo/lab showcases Analytics in the Microsoft Intelligent Data Platform. The Analytics solution pattern is a cost-effective, performance-optimized, and cloud-native architecture which helps our customers unify their data estate to accelerate data value creation. The visual here shows the Microsoft Analytics Solution pattern. 
The solution layers depicted here are as follows:

**1. Implementing a Lake First Data Foundation for Analytics**

Microsoft’s overall approach is based on an open and governed Data Lakehouse foundation for analytics. The open and governed Data Lakehouse foundation is a cost-effective and performance-optimized fabric for business intelligence, machine learning, and AI workloads at any scale. It is the foundation for migrating and modernizing existing analytics solutions, whether this be data appliances or traditional data warehouses. Finally, the Data Lakehouse is foundational for integrating data across a broad spectrum of emerging operational databases and systems including modern analytics applications

**2. Implementing an Open and Governed Data Lakehouse**

With raw data landed in the data lake, the next step is to transform and prepare the data for analytics applications. We believe the best solution for data transformation and preparation is to anchor to an open and governed data Lakehouse. This provides a unified approach to serve the full spectrum of BI, ML, and AI applications. In the past, data lakes were used to serve data science applications, data warehouses, and datamarts for BI applications. They relied on complex ETL pipelines to move data between, and across, the fabrics. Now, with the data Lakehouse foundation, we have a unified foundation to serve the most demanding BI, ML, and AI applications while also optimizing for performance and cost.

**3. Machine Learning and Data Analysis in the Microsoft Intelligent Data Platform**

**Machine Learning:** Data scientists can bring their preferred compute frameworks, languages, runtimes, and tools to the data Lakehouse to access data prepared for ML applications. In addition, they can further refine and enhance the data through feature engineering and additional statistical techniques. In most environments, experiments are performed iteratively to produce machine learning models which provide the desired business outcomes.

**Data Analysis:** Ad-hoc and interactive data analysis using notebooks is a top line workload and experience for data analysts. While data analysts can also use the Spark modalities generally used by data scientists, it is more common for data analysts to prefer SQL modalities. Up until recently, there was no clean solution to enable ad-hoc and interactive SQL data analysis directly on data in a data lake. With recent advances, we now have solutions to address this need with the following customer options in the Microsoft Intelligent Data Platform: 

- Synapse Serverless SQL notebooks 
- Azure Databricks SQL Analytics notebooks

**4. Business Intelligence in the Microsoft Intelligent Data Platform**

The Microsoft Intelligent Data Platform offers best-in-class integrated solutions to responsibly democratize business intelligence with self-serve tools and experiences for data analysts and data citizens.

**5. Data Governance in the Microsoft Intelligent Data Platform**

Microsoft Purview is the single-pane data governance solution in the Microsoft Intelligent Data Platform. Seamlessly integrate Purview with the Databricks catalog and metastore to enable a single pane governance solution. Microsoft Purview provides a unified data governance experience that spans the MIDP analytics estate across Azure Data Lake, Synapse, Azure Databricks, Power BI, and Azure Machine Learning. 
 
===

#Introduction

![Analytics in MIDP - Interactive Lab Experience](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img_labexp.png?raw=true)

In this interactive demo/lab, you will experience an integrated, open, and governed Data Lakehouse foundation based on the Microsoft Analytics Solution pattern.  
We will cover the following:

**Exercise 1:** First, we will look at data ingestion from a spectrum of analytical and operational data sources into the Lakehouse.
- We start with streaming data and analytics pipeline using ADX for a near real-time analytics scenario. 
- Then we will use Synapse pipelines that ingest raw data from analytical/operational data sources into the bronze layer.
	   
**Exercise 2:** Second, we will explore offline data and analytics pipelines using open Delta format and Azure Databricks Delta Live Tables for data transformation.
- We will stitch streaming and non-streaming data (landed earlier), to create a combined data product and build a simple Lakehouse.  
	
**Exercise 3:** Third, we will explore ML and BI scenarios on the Lakehouse. Here we will review MLOps pipeline using the Azure Databricks managed MLFlow with Azure ML.
- Using Power BI with Synapse serverless capabilities we derive actionable insights 
- We will explore SQL Analytics with Azure Synapse Serverless and Azure Databricks.

**Exercise 4:** Finally, we will leverage Purview for data governance. 

----

### Disclaimer

This presentation, demonstration, and demonstration model are for informational purposes only and (1) are not subject to SOC 1 and SOC 2 compliance audits, and (2) are not designed, intended or made available as a medical device(s) or as a substitute for professional medical advice, diagnosis, treatment or judgment. **Microsoft makes no warranties, express or implied, in this presentation, demonstration, and demonstration model.** Nothing in this presentation, demonstration, or demonstration model modifies any of the terms and conditions of Microsoft’s written and signed agreements. This is not an offer and applicable terms and the information provided are subject to revision and may be changed at any time by Microsoft. 

This presentation, demonstration, and demonstration model do not give you or your organization any license to any patents, trademarks, copyrights, or other intellectual property covering the subject matter in this presentation, demonstration, and demonstration model.

The information contained in this presentation, demonstration and demonstration model represents the current view of Microsoft on the issues discussed as of the date of presentation and/or demonstration, for the duration of your access to the demonstration model. Because Microsoft must respond to changing market conditions, it should not be interpreted to be a commitment on the part of Microsoft, and Microsoft cannot guarantee the accuracy of any information presented after the date of presentation and/or demonstration and for the duration of your access to the demonstration model.

No Microsoft technology, nor any of its component technologies, including the demonstration model, is intended or made available as a substitute for the professional advice, opinion, or judgment of (1) a certified financial services professional, or (2) a certified medical professional. Partners or customers are responsible for ensuring the regulatory compliance of any solution they build using Microsoft technologies. 

----

**© 2023 Microsoft Corporation. All rights reserved.**

By using this demo/lab, you agree to the following terms:

The technology/functionality described in this demo/lab is provided by Microsoft Corporation for purposes of obtaining your feedback and to provide you with a learning experience. You may only use the demo/lab to evaluate such technology features and functionality and provide feedback to Microsoft.  You may not use it for any other purpose. You may not modify, copy, distribute, transmit, display, perform, reproduce, publish, license, create derivative works from, transfer, or sell this demo/lab or any portion thereof.

COPYING OR REPRODUCTION OF THE DEMO/LAB (OR ANY PORTION OF IT) TO ANY OTHER SERVER OR LOCATION FOR FURTHER REPRODUCTION OR REDISTRIBUTION IS EXPRESSLY PROHIBITED.​

THIS DEMO/LAB PROVIDES CERTAIN SOFTWARE TECHNOLOGY/PRODUCT FEATURES AND FUNCTIONALITY, INCLUDING POTENTIAL NEW FEATURES AND CONCEPTS, IN A SIMULATED ENVIRONMENT WITHOUT COMPLEX SET-UP OR INSTALLATION FOR THE PURPOSE DESCRIBED ABOVE. THE TECHNOLOGY/CONCEPTS REPRESENTED IN THIS DEMO/LAB MAY NOT REPRESENT FULL FEATURE FUNCTIONALITY AND MAY NOT WORK THE WAY A FINAL VERSION MAY WORK. WE ALSO MAY NOT RELEASE A FINAL VERSION OF SUCH FEATURES OR CONCEPTS.  YOUR EXPERIENCE WITH USING SUCH FEATURES AND FUNCITONALITY IN A PHYSICAL ENVIRONMENT MAY ALSO BE DIFFERENT.

### Feedback

If you give feedback about the technology features, functionality and/or concepts described in this demo/lab to Microsoft, you give to Microsoft, without charge, the right to use, share and commercialize your feedback in any way and for any purpose. You also give to third parties, without charge, any patent rights needed for their products, technologies and services to use or interface with any specific parts of a Microsoft software or service that includes the feedback. You may not give feedback that is subject to a license that requires Microsoft to license its software or documentation to third parties because we include your feedback in them. These rights survive this agreement.

MICROSOFT CORPORATION HEREBY DISCLAIMS ALL WARRANTIES AND CONDITIONS WITH REGARD TO THE DEMO/LAB, INCLUDING ALL WARRANTIES AND CONDITIONS OF MERCHANTABILITY, WHETHER EXPRESS, IMPLIED OR STATUTORY, FITNESS FOR A PARTICULAR PURPOSE, TITLE AND NON-INFRINGEMENT.  MICROSOFT DOES NOT MAKE ANY ASSURANCES OR REPRESENTATIONS WITH REGARD TO THE ACCURACY OF THE RESULTS, OUTPUT THAT DERIVES FROM USE OF DEMO/ LAB, OR SUITABILITY OF THE INFORMATION CONTAINED IN THE DEMO/LAB FOR ANY PURPOSE.

===

#Setting The Scene

You will work through an example of a real world implementation for the fictitious Wide World Importers enterprise.

Wide World Importers is a brick-and-mortar retailer that has hundreds of stores worldwide and a fast-growing online store. It sells a wide variety of consumer merchandise, including sunglasses, shoes, watches, wallets, books, and various beach products.

The lab scenario starts on May 30th, 2021. The company's new CEO, April, recently noticed negative trends in their KPIs, including:

- High Customer Churn
- Declining Revenue
- High Bounce Rate on their website
- Poor Customer Experience

As soon as the company saw these adverse KPI trends, they launched some traditional campaigns. On September 5 (Labor Day), the results of those campaigns were received. The company noticed that the campaigns failed to be effective.

April spoke with Rupesh, the Chief Data Officer (CDO), about these adverse KPI trends and recommended a data-driven approach.

In this exercise you will act as a data engineer. Rupesh would like you to improve the above KPIs using the following requirements:

- Leverage data from the past, present, and future (Volume).
- Enable quick turnaround time (Velocity).
- Support open standards data format (Variety).

Let’s get started with the lab.

===

#**Exercise 1: Data ingestion from a spectrum of analytical and operational data sources into the Lakehouse**

As a data engineer at Wide World Importers, you will start by landing data from a variety of sources into the Lakehouse. This data will be further cleansed, processed, and conformed by using Azure Databricks and Delta Live Tables. This is a preparation step for downstream consumption of the data by data scientists and business intelligence analysts. Data sources include data related to its customers, products, marketing campaigns, social media, and sales transactions. This data is often generated in raw files format such as CSV, JSON, unstructured files, and images. 

To boost customer satisfaction, gain a competitive advantage, and ultimately drive revenue growth, Wide World Importers wants to analyze its data to obtain meaningful insights related to their customers, marketing campaigns, and sales forecasts. Their immediate challenge is to generate and use near real-time streaming data, so they installed IoT devices in their stores to analyze customer shopping patterns and thermostat readings. They also set up Azure Data Explorer (ADX) with anomaly detection to correlate in-store traffic and store temperatures. As a result, they now have a large volume of real-time streaming data related to in-store traffic, temperature readings, and anomaly detection.

In this exercise, you will explore how to ingest near real-time data into the Lakehouse and derive actionable insights.
## Task 1.0: Log into the Azure Portal

1. Login into the VM using these credentials.

    - **Username:** +++@lab.VirtualMachine(BuildBaseVM).Username+++
    - **Password:** +++@lab.VirtualMachine(BuildBaseVM).Password+++

1. Open Edge and navigate to +++https://portal.azure.com+++

1. Sign into Azure using these credentials

    - **Username:** +++@lab.CloudPortalCredential(User1).Username+++
    - **Password:** +++@lab.CloudPortalCredential(User1).Password+++


## Task 1.1: Explore a Streaming data and analytics pipeline using ADX for a near real-time analytics scenario. <a name="streaming-data"></a>

Wide World Importers wants its customers to have a pleasant in-store shopping experience. Maintaining the optimal temperature in stores and wine coolers is one way to accomplish this objective.

Consider that the Black Friday Sale in-store event has just started at 6:00 AM EST, and customers are arriving in large numbers at the Miami store. As described earlier, thermostat data from the stores is streamed in real-time to an Azure Event Hub and then into an Azure Data Explorer (ADX) pool for analysis.

In this task, you will use ADX to explore thermostat data from the stores streamed in near real-time to an Azure Event Hub.

1. In the search results pane, select **Resource groups**.

![In the search results pane, select the Resource group](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image1107.png?raw=true)

2. On the **Resource groups** page, in the filter box, enter: **AnalyticsSolution**.

3.	In the filtered results, select the resource group name starting with **AnalyticsSolution**.

  >**Note:** Each user has their own unique instance of this resource.

![In the filtered results, select the resource group](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image1109.png?raw=true)

4. In the Resources filter box for resources, search for **app**.

5. In the filtered results, select the App Service.

![Select the app service](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/imageAppServices.png?raw=true)

6. From the overview page of the App Service, select **Browse** (on the top left). This action will start the data simulation required to execute this task successfully.

![Select Browse](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/imageclickBrowse.png?raw=true)

And, this will take you to a webpage which will confirm **Data Simulation** has started:

![Data Simulation](https://github.com/SD-14/Ignite-Demo/blob/main/media/datasimulation.png?raw=true)

7. Return to the Azure Portal session (browser tab) then select the 'AnalyticsSolution' Resource group from the top navigation bar.

![Return to Azure Portal](https://github.com/SD-14/Ignite-Demo/blob/main/media/returnToAzurePortal.png?raw=true)

8.	In the Resources filter box for resources, search for **Synapse**.

9.	In the filtered results, select the Azure Synapse resource.

![In the filtered results, select the Azure Synapse resource](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image1114.png?raw=true)

*Note: You might see a Synapse workspace resource name with a different suffix in your Azure Portal.*

10. In the Open Synapse Studio tile, select the Open link.


![Open Synapse studio](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image1115.png?raw=true)

>**Note:** Synapse Studio opens in a new web session (tab).

11.	In Synapse Studio, in the left navigation pane, select the **Data** hub icon (second from the top).

12.	In the **Data** pane, expand **Data Explorer Databases (Preview).**

13.	Expand the **analyticspool<inject key="DeploymentId"></inject>** Data Explorer pool.

14. Select the **ellipses** (the three dots next to the data explorer pool).

>**Note:** If you do not see the ellipses, expand the Data pane by dragging it to the right. 

![Expand Data Explorer Pool](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img114.png?raw=true)

15. Select **Open in Azure Data Explorer**.

>**Note:** This will open Azure Data Explorer in a new web session (tab).

![Open Azure Data Explorer](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img115.png?raw=true)

*For this lab, an ADX pool has already been created in the Azure Synapse workspace.*

*By using ADX’s powerful Kusto Query Language (KQL), you can ensure that the thresholds you have set for each device in the store are being met.*

>**Note:** Other Azure services use KQL for analytical queries. These services include Azure Monitor logs, Application Insights, and Microsoft Defender for Endpoint.

16.	In Azure Data Explorer Studio, in the left navigation pane, select the **Data** hub icon.

>**Note:** Select **Dismiss** if any pop-ups appear on your screen.

17.	In the **Data Management** page, select the **Ingest data** action.

![Paste the URI into the address bar](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image1127.png?raw=true)

18.	In the **Destination** tab, in **Cluster** dropdown list, select the Data Explorer pool starting with **analyticspool<inject key="DeploymentId"></inject>**.
     
19. In the Database dropdown, select **AnalyticsDB**. Then in the **Table** textbox, enter/type **Thermostat**.

20.	Click on  **Next: Source.**

![Click Next](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img119.png?raw=true)


![Important Note](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/imp_note.PNG?raw=true)


![Add Cluster](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/imageAddCluster.png?raw=true)

  a. Navigate to the Azure Synapse web session (tab), select **Manage** hub from the left pane.

  b. Select the **Data Explorer pools (preview)** from the **Analytics pool** pane.

  c. Select the **analyticspool<inject key="DeploymentId"></inject>**.

![manage tab](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img120c.png?raw=true)

  d. Under the **Query endpoint** copy the **URL** and select **Close** to close the pane.

![Copy URI](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img120d.png?raw=true)

  e. Go back to the **Azure Data Explorer** tab, in the **Connection URI**, enter the URI copied above.

  f. Select **Add**, continue with Step 21.

![click Add](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img120f.png?raw=true)

21.	In the **Source** tab, in the **Source** dropdown list, select **Event Hub**.

22.	In **Subscription** dropdown list, select your subscription.

![Select Eventhub](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img122.png?raw=true)

23.	In the **Event Hub namespace** dropdown list, select the Event Hub that has a name starting with **adx-thermostat-occupancy**.

24.	In the **Event Hubs** dropdown list, select **thermostat**.

25.	In **Data connection name** dropdown list, select **AnalyticsDB-thermostat**.

26.	In the **Consumer group** dropdown list, select **$Default**.

27.	From More parameters, keep **Compression** to default or **none**.

28.	Select **Next: Schema**.
!IMAGE[ADXCompression.png](ADXCompression.png)


29.	In the **Schema** tab, wait until the data preview loads (about 20 seconds).

30.	Review the event data, which comprises thermostat measures from different devices.

31.	In the **Data** format dropdown list, select **JSON.**. Keep **Nested levels** and **Mapping name** to default values.

32.	Select **Next: Start ingestion.**

!IMAGE[ADXSchema.png](ADXSchema.png)

33.	Confirm that the continuous ingestion from Event Hub has been established, and then select **Close** (located at the bottom of the page).

![Select Close](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img133.png?raw=true)

34. Return to the Synapse Studio web session (tab).

35. In Synapse Studio, on the left navigation pane, select the **Develop** hub icon (the third from the top).

36. In the **Develop** pane, expand **KQL scripts**.

37. Select the **ThermostatOccupancyScript** script.

![Select the ThermostatOccupancyScript Sript](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image1148.png?raw=true)

38. In the **Connect to** dropdown list (If you do not see this option, click on the ellipsis [...] next to Publish on the top bar), select the data explorer pool starting with **analyticspool**.

>**Note:** If required, collapse the panes on the left using the << icon at the top right of each pane.

39. In the **Use database** dropdown list, select **AnalyticsDB**.

40.	Select the query lines 4-8 under **What is the average temp every minute?**

*The query retrieves the average temperature per minute for a thermostat device (TH005) for the Miami store.*

41.	Select **Run**. 

42.	In the **Results** pane (located along the bottom), review the query result chart. Please note that it may take 2-3 minutes to accumulate data. If you do not see a result, wait few minutes and re-run the query. 

>**Note:** If your query does not run successfully, the thermostat table may not have been created successfully in the previous steps. You may have to create that table with a different name e.g. Thermostat1, update the KQL query accordingly, and re-execute the KQL query.  

![Review the query result ](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img_graph1.png?raw=true)

*Your graph may appear slightly different than the one shown above. It may take up to 60 seconds to load.*

43.	Notice that the temperature in the Miami store is oscillating between 65 and 70 degrees Fahrenheit. Based on these insights, we are able to adjust the temperatures to optimal level.

===  

## Task 1.2: Explore a few Synapse pipelines that ingest raw data from analytical data sources to the bronze layer of the Data Lake. <a name="analytical-sources"></a>

  
Your next challenge is to ingest historical data from a spectrum of data sources.  

In this task you will ingest Campaign Data from Snowflake and Customer Churn Data from Teradata into the data lake.

1. Return to the Synapse Studio web session (tab).

2. In Synapse Studio, on the left navigation pane, select the **Integrate** hub icon (fourth from the top).

3. In the **Integrate** pane, expand **Pipelines**.

4. Expand the **1 Enterprise Data Sources In The Lake** folder.

5. Expand the **Landing Analytical Store Data** folder.

6. Select the **Campaigns Data From Snowflake** pipeline.

>**Note:** If required, collapse the panes on the left using the << icon at the top right of each pane.

![Campaigns data from Snowflake ](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image1206.png?raw=true)


*The ***Campaigns Data from Snowflake*** pipeline has two activities. The first activity runs a Lookup of data at the source Snowflake connection. Next, the Copy data activity brings that data into the bronze layer in ADLS Gen2.*


7.	In the pipeline designer, select **Lookup** activity.

8.	In the pane below, select the **Settings** tab.

9.	In the **Source dataset** dropdown list, notice that **SnowflakeTable** is selected.

!IMAGE[Image12.png](instructions230217/Image12.png)

10.	In the pipeline designer, select **Copy data** activity.

11.	In the pane below, select the **Sink** tab.

12.	In the **Sink dataset** dropdown list, notice that **SnowflakeCampaignsData** is selected.

![Sink Dataset](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image1212.png?raw=true)

*Similarly, the next pipeline is designed to ingest Customer Churn Data From Teradata, and Twitter Data In Data Lake.*

>**Note:** This image is for informational purposes only. Due to time constraints, we will not explore it in the lab.

![CustomerChurn Data From Teradata](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image1213.png?raw=true)

===

  

## Task 1.3: Explore a few Synapse pipelines that ingest raw data from operational data sources to the bronze layer of the Data Lake. <a name="operational-sources"></a>

  
In this task, you will explore the design of a Synapse pipeline that is designed to ingest raw data coming from various operational sources into the data lake.

1.	In the **Integrate** pane, expand the **Landing Operational Store Data** folder, select the **Store Transactions Data from SQL DB** pipeline.

![Landing Operational Store Data](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image1309.png?raw=true)

*The **Store Transactions Data from SQL DB** pipeline has two activities. The first activity runs a Lookup of data at the source Azure SQL Database connection. Next, the Copy data activity brings that data into the bronze layer in ADLS Gen2*.

>**Note:** If required, collapse the panes on the left using the << icon at the top right of each pane.

2.	In the pipeline designer, select the Copy data activity.

3.	In the pane below, select the **Sink** tab.

4.	In the **Sink dataset** dropdown list, notice that **DestinationDataset** is selected.

![Sink dataset](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image1312.png?raw=true)

*Similarly, the next pipeline is designed to ingest Sales data from Oracle to the data lake.*

>**Note:** This image is for informational purposes only. Due to time constraints, we will not explore it in the lab.

![Sales Data](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image1302.png?raw=true)

---

Congratulations! As a data engineer you have successfully ingested streaming near real-time as well as historical data into the data lake for Wide World Importers.

===
#**Exercise 2: Explore offline data and analytics pipelines using open Delta format and Azure Databricks Delta Live Tables. Stitch streaming and non-streaming data (landed earlier) to create a combined data product to build a simple Lakehouse**

Analyzing spectrum of data sources in an integrated way has been a challenge for Wide World Importers. In the past, different teams at the company were assigned to analyze Customer Churn, social media trends, marketing campaigns, and sales forecasts. So, it was left to business analysts and executives to synthesize these datasets into a data-driven decision making solution. By delivering a lakehouse, it will become simple for teams to collaborate on a unified workspace to process, analyze, and model data.

In this exercise, you will stitch two sets of data together to generate actionable insights. You will set up an Azure Databricks Delta Live Table (DLT) pipeline to build a simple Lakehouse. The pipeline will enrich the data by scoring it with machine learning models to help better understand customers and how to reduce churn.

The data source for the pipeline is the bronze layer in ADLS Gen2, which was loaded by the Synapse pipeline in Exercise 1. This bronze layer contains Campaigns data, Customer Churn data, store transactions data, sales data, and Twitter messages.

## Task 2.1: Set up an Azure Databricks environment <a name="adb-env"></a>

In this task, you will set up the Azure Databricks environment.

1.	In the Azure portal web session (tab), in the search box (located across the top of the page), enter: **Azure Databricks**

2.	In the search results pane, select **Azure Databricks**.

![Select Azure Databricks](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image2102.png?raw=true)

3.	In the **Azure Databricks** page, select the resource that has a name starting with **databricks**.

!IMAGE[Image23.png](instructions230217/Image23.png)

>**Note:** Each user has their own unique instance of this resource. Each Azure Databricks workspace is provisioned with a full-featured development environment.

4.	In the Azure Databricks resource page, Copy resource **URL**.

!IMAGE[ADB_Pic1.png](instructions230217/ADB_Pic1.png)
5. Open new tab in your browser ,paste the **Azure Databricks Resource URL** and press **Enter**

6. Select **Sign in with Azure AD**

!IMAGE[ADB sign in.png](instructions230217/ADB sign in.png)

*You will then set up the Databricks compute ready to serve your workload.*

>**Note:** If you see a pop-up, select **Close**.

7. Select **Workspace** from the left navigation pane.

8. Select the **ADB_Initial_Setup** notebook.

> **Note: DO NOT** run this script. 
> This image is for informational purposes only. 
> Due to time constraints, we will not run this notebook in the lab session.

![ADB_Initial_Setup](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image2107.png?raw=true)


*In exercise 1, we extracted data from a spectrum of data sources and landed it into ADLS Gen 2 data lake. To access this data from ADLS Gen2 data lake, we need to mount it on Azure Databricks filesystem. Executing this script will mount ADLS Gen2 to Azure Databricks.*

---

## Task 2.2: Review Sentiment Analysis model training. <a name="sentiment-model"></a>

In this task, you will explore the Sentiment Analysis model training notebook. This notebook is used to retrieve the model ID that’s used by the DLT pipeline for further data processing.

*Sentiment Analysis identifies and extracts subjective information in source material to understand whether the underlying sentiment is positive, negative, or neutral.*

1.	To open a different workspace, on the left navigation pane, select the **Workspace** icon.

2.	Select the **02_Twitter_Sentiment_Score_Pred_Custom_ML_Model** notebook.

![Twitter_Sentiment_Score_Pred_Custom_ML_Model](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image2202.png?raw=true)

> **Note: DO NOT** run this script.
> This image is for informational purposes only.
> Due to time constraints, we will not run this notebook in the lab session.

*Running this script will generate a ML model ID. This Model ID is used by the Delta Live Pipeline that we will create in the next task to perform ML operations on Twitter data.* 

---


## Task 2.3: Create a Delta Live Table pipeline. <a name="dlt-pipeline"></a>

In this task, you will create a Delta Live Table pipeline.

*Delta Live Tables (DLT) allow you to build and manage reliable data pipelines that deliver high-quality data on Delta Lake. DLT helps data engineering teams simplify ETL development and management with declarative pipeline development, automatic data testing, and deep visibility for monitoring and recovery.*

1.	On the left navigation pane, select the **Workflows** icon.

![Select Workflows](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image2301.png?raw=true)

2.	Select the **Delta Live Tables** tab.

![Select Workflows](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img232.png?raw=true)

3.	Select **Create Pipeline**.

![Select create pipeline](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image2303.png?raw=true)

4.	In the **Create pipeline** window, in the **Pipeline name** box, enter a name like **Delta Live Table Pipeline**.

![create pipeline](https://github.com/SD-14/Ignite-Demo/blob/main/media/deltalivepipelines.png?raw=true)

5.	To set the **Notebook libraries** property, select the notebook icon.

![Notebook libraries](https://github.com/SD-14/Ignite-Demo/blob/main/media/nootbookLibraries.png?raw=true)

6.	In the **Select a notebook** window, select the **03_Sentiment_Analytics_On_Delta_Live_Tables** notebook.

>**Note:** Due to time constraints, we will only add the **03_Sentiment_Analytics_On_Delta_Live_Tables** notebook library to the pipeline in the lab session.

![Select Notebook](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/imageSelectNotebook.png?raw=true)

**(SKIP THIS STEP)** : *Similarly, we can repeat steps 5 and 6 to add the other three notebook libraries.* 
 
- 01_campaign_analytics_DLT
- Campaign Powered by Twitter
- Retail Sales Data Prep Using Spark DLT

      
7.	In the **Storage location** box, enter: **/mnt/delta-files/lakedb/**

8.	In the **Target schema** box, enter: **lakedb**

9. Select **Create**.

![Select Create](https://github.com/CloudLabsAI-Azure/Ignite-lab/raw/main/media/storagelocation,target.png?raw=true)


*Once you select **Create**, it will create the Delta Live Table pipeline with all the notebook libraries added to the pipeline.*

![Do not select Start](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img239.png?raw=true)

> **Note: DO NOT** click **Start**.

*If you click on **Start**, Databricks will start executing the pipeline which will take approximately 10 minutes.*

![Wating for the job to complete](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image2317.png?raw=true)

> **Note:** The following instructions are for informational purposes only. Due to time constraints, we will not start the pipeline in the lab session.

*The lab instructor will share the pipeline lineage with you. Please follow the lab instructor to understand the pipeline lineage in detail.*

10. After approx 10 mins, this is the view you would have seen. **Observe** the data lineage of bronze, silver and gold tables.

![Medallion Architecture](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image2318.png?raw=true)

This pipeline is based on the medallion architecture, an extremely simple but powerful design pattern for organizing your Lakehouse.

**Bronze** data is usually raw, unprocessed data from the source systems.

**Silver** data is created by cleaning and organizing raw data for further analysis and exploration.

**Gold** data are the finished analytical products – star schema tables for BI applications, engineered features for ML models, and shareable data assets for third parties, Data Mesh architectures, and other downstream consumers.

As you can see in this diagram, all the data is first landed in the Lakehouse where it is further processed into different medallion layers.

The Twitter sentiment and campaign data is stitched together to create a combined data product which is further consumed in the next exercise for machine learning and business intelligence use cases.

This information can be then piped into Microsoft Purview as a part of an overall view of your Azure data estate. By being designed around simplicity, openness, and collaboration, the Lakehouse is an extremely powerful architecture for addressing the many unique and interesting problems of a modern cloud data stack ready to be leveraged by Wide World Importers.

Congratulations! As a data engineer, you have now set up a solid foundation of fully stitched data comprised of campaign and Twitter data from disparate sources including some key data transformations.

===
# **Exercise 3: Explore Machine Learning and Business Intelligence scenarios on the Lakehouse**

## Task 3.1: Review MLOps pipeline using the Azure Databricks managed MLflow and Operationalized as an ML service in Azure ML<a name="ml-model-using-ml-flow"></a>

Now that we've ingested and processed our customer data, we want to understand what makes one customer more likely to churn than another, and ultimately see if we can produce a machine learning model that can accurately predict if a particular customer will churn.

We would also like to understand our customer's sentiment, so that we can create targeted campaigns to improve our sales.

*Architecture Diagram*

![Architecture Diagram](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3100.png?raw=true)

1. In the Databricks web session (tab), switch to the **Machine Learning** persona.

*By default, the left navigation pane appears in a collapsed state and only the icons are visible. You can hover your cursor over the pane to expand it for the full view.*

![Select the persona](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3101.png?raw=true)

2. On the left navigation pane, select the **Workspace** icon, and then select the **ML Solutions in OneBox** notebook. Once the notebook is open, click on > to expand notebooks **Table of content**.

![Select the workspaces](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3102.png?raw=true)

In this task, you won’t run any cells. Instead, you will explore the selected cells and review their outcomes.
In the scatter-plot chart below, you can see the correlation between:

- Customer Churn,
- Amount spent by the customer, and
- Number of months as a customer (tenure).

  Here you will find that most of the customers who churn are those, who spend the least amount of money and stay for fewer months.

3. Click on **Table of contents** 
4. Click on **Exploratory Data Analysis**.

   !IMAGE[Image42.png](instructions230217/Image42.png)

5. Scroll down the **Table Of contents** list
6. Click on **Compare multiple runs in the UI**

By analyzing Customer Churn data, we create multiple Machine Learning models. Runs using a parallel coordinates

!IMAGE[Image43.png](instructions230217/Image43.png)

The best ML model for Customer Churn is selected and registered with Azure model registry.

**Operationalized as an ML service using MLOps in Azure ML/AI**.

7. Scroll down the **Table Of contents** list
8. Click on **Load an Azure ML Workspace.**
!IMAGE[Image44.png](instructions230217/Image44.png)

The MLflow plugin **azureml-mlflow** is used to deploy the Customer Churn ML model to Azure ML. The deployed ML model will be used to predict Customer Churn.

**Twitter Sentiment Score Custom ML Model**

*This model helps Wide World Importers analyze the sentiment of their customers based on what's trending on social media platforms like Twitter. The popular social media sentiments can then be used to create effective marketing campaigns for the target audience.*

9. On the left navigation pane, select the small arrow to expand the sidebar, collapse the **Requirements** and select **Twitter Sentiment Score Model**.

   ![Twitter sentiment score model](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img316.png?raw=true)

10. Review the **cmd 75** cell for training and validation of customer sentiment model.
*Here the Twitter sentiment model is trained for further consumption.*

   ![Customer model train and validation](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3126.png?raw=true)


**Campaign Analytics**

11. From the sidebar, select **Campaign Analytics**.

   ![Campaign Analytics](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3128.png?raw=true)

12. Review the **cmd 88** cell.

*Wide World Importers decided to run a number of campaigns using the Twitter sentiment model which was trained in cmd 75 cell in order to reduce customer churn and increase revenue.*

![cmd 88](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3129.png?raw=true)

**Sales Forecasting**

13. From the sidebar, scroll down and select **Sales Forecasting**.

    ![Sales Forecasting](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3132.png?raw=true)

Wide World Importers used sales forecasting model to determine if their approach to reduce churn and improve sales was effective.

*Here you are forecasting sales using a Regression model and deploying it to Azure ML as a service using a model registered in Azure Databricks.*

14. Scroll down the **Table Of contents** list
15. Click on **Deploy the model to a managed endpoint**

    !IMAGE[Image45.png](instructions230217/Image45.png)

*The model is deployed to an Azure ML endpoint where it can be used to predict sales.*

16. Scroll down the **Table Of contents** list
17. Click on **Visualize predicted sales revenue**

    !IMAGE[Image46.png](instructions230217/Image46.png)

*All this analysis using MLOps helped Wide World Importers predict a positive sales forecast and a successful year ahead*.

---

## Task 3.2: Leverage Power BI to derive actionable insights from data in the Lakehouse. <a name="power-bi-report-to-analyse-data-in-the-Lakehouse"></a>

For this task, the date is November 1. Wide World Importers now needs to prepare for a successful Cyber Monday sales event. Good news! The enriched datasets sourced from spectrum of data sources and the best performing model outputs have now been placed in the Lakehouse for Power BI consumption.

In this task, you will work with Power BI to reveal some actionable insights.

> **Note:** Please make sure you are **logged into the VM** for the following steps.

1.	Open a new web session (tab) in the VM, and then enter: **https://app.powerbi.com**

> **Note:** Dismiss any pop-ups that may appear on your screen.

2. In the workspaces pane, select **My Workspace**.

![Select New Workspace](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/imageMyWorkspace.png?raw=true)

3. To upload a Power BI Desktop file, on the **Upload** dropdown menu, select **Browse**.

> **Note:** Please make sure you are **logged into the VM** for the following steps.

!IMAGE[Image53.png](instructions230217/Image53.png)

4.	Select the **Local File** tile.

5.	In the **Open** window, navigate to the **C:\MIDP-Assets\artifacts\reports** folder, and then select the **AnalyticsDemoReport.pbix** file.

6.	Select **Open**.

!IMAGE[Image54.png](instructions230217/Image54.png)

7.	Notice that a Power BI report and dataset have been added to your workspace.

8.	To open the report, select the **AnalyticsDemoReport**.

![Power BI report added to your workspace.](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3212.png?raw=true)

> **Note:** If needed, collapse the left navigation pane using the << icons on the top right of the pane. This will maximize the screen and provide a better visual.

9. This report has three sections:
 - Churn Analysis
 - Campaign Analytics
 - Website Analytics
 

![PowerBI Report Name](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3227.png?raw=true)

10.  Lets navigate to the **Churn Analysis Tab,** where we analyze Customer Churn. This report along with the Campaign Analytics and Website Analytics reports in Power BI are using data from the data Lakehouse that we created earlier.


![PowerBI Report Buttons](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img3210.png?raw=true)


11. In the scatter plot, the black dots represent customers more likely to churn, and the blue dots represent customers less likely to churn.
Notice that when the customer tenure is low and their spend amount is low, customers are more likely to churn.

12. With this insight, Wide World Importers decides to target customers with lesser tenure and lesser spend amounts through their new campaigns.


![Scatter chart](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3229.png?raw=true)


Now, let's go the Campaign Analytics. 


13.  Select the **Campaign Analytics** tab from the top right pane to navigate to the Campaign Analytics report.

![Select Campaigns Analytics](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3238.png?raw=true)

14. In this Campaign Analytics report, the Bar chart shows that the most popular campaigns launched were **gogreen** and **sustainablefashion**. 


![Campaigns report - Bar chart](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3239.png?raw=true)


15. Select **Website Analytics** from the top right pane to navigate to the Website Analytics Report.

![Website Analytics](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/imageWebsiteAnalytics.png?raw=true)

Here we see an immediate problem for Wide World Importers.
The bounce rate is high. It looks like a large population of their customers/visitors leave their website without much activity.

As per this donut chart it seems that the bounce rate is high because around 57 % of the online customers are not happy. 

![Website Analysis Report page](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3242.png?raw=true)

Let's understand more about these **Not Happy** customers.  

16. Click on **Not Happy** on the donut chart to filter the report page.

![Not Happy Customers](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/imageDonutChart.png?raw=true)
  
The **site visitors by age group** chart shows that most of the "Not Happy" customers are in the 31 to 40 age group. It seems that the millennials make up the majority of unhappy online customers. Now, let's see what these millenials typically shop for online.
 
![Site visitors by age group](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/imageAgeGroup.png?raw=true)

*Hover over the bars to see the visuals of the products bought by repeat customers.*

![Repeat customers](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/imageSurfingBoard.png?raw=true)

17.  We know that the millenials from the biggest customer segment are "Not Happy" when:

- They do not find the product they searched for on the website.
- They were redirected to Wide World Importers website from a third party website.
- The website user experience on their mobile phones is poor.
- They are not able to find discounts on the website.

![Repeat Customers Chart](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/imageRepeatCustomersGraph.png?raw=true)

As a result, we can say that we need to improve the user experience on the website for product search and make sure that it renders correctly on mobile phones.
  
Now, let's navigate to the key influencers.

18. Select **Top Segments** to show the details.

![Key influencers Chart](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/websiteAnalytics-keyInfluencers.png?raw=true)

19. Click on the first bubble to see the details for Segment 1.

![Top Segments](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3248.png?raw=true)

*Segment 1 shows that it comprises of 94.5% customers who are not happy. It also shows that 94.5 % of the "Not Happy" customers experienced failed product searches. These are the millennials who are using their mobile devices.*


![Millenials using mobile phone](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/imagePowerBI.png?raw=true)
 

Using these actionable insights, Wide World Importers was able to reduce their bounce rate. Further they implemented a mobile-friendly website with fast product searches, focusing on high demand products for the millenials. These changes not only improved the bounce rate dramatically, but also rewarded Wide World Importers with uprecedented sales at their Cyber Monday sales event. 

Now, let's see how, on an ongoing basis, if there are any business needs to run adhoc time-critical queries, it can be achieved via custom queries. 

We will discuss that in more detail in the next task.

------------- 

## Task 3.3 (OPTIONAL): Explore SQL Analytics with Azure Synapse Serverless. <a name="sql-analytics-with-synapse"></a>

Data engineers are often required to support ad hoc and time-critical queries in addition to regular scheduled reports.

In this task, you will learn how to perform custom SQL and business intelligence workloads on the data lake. You will query the data lake by using Azure Synapse Analytics. Specifically, you will rely on Azure Synapse serverless SQL pools, which is a service that queries data in a data lake. It’s important to understand that the data can be queried without the need to move it into tables.



1. In the search box of the Azure portal (tab), enter: **Synapse Analytics**.

2. In the search results pane, select **Azure Synapse Analytics**.

![Select Azure Synapse Analytics](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img332.png?raw=true)

3.	In the filtered results, select the Azure Synapse resource.

![Select Azure Synapse resource](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3303.png?raw=true)

*Note: You might see Synapse workspace resource name with a different suffix in your Azure Portal.*

4. In the **Open Synapse Studio** tile, select the **Open** link.

![Open Synapse studio](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3304.png?raw=true)

*Synapse Studio opens in a new web session (tab).*

5. In Synapse Studio, on the left navigation pane select the **Develop** hub icon (the third from the top).

*In Synapse Studio, you can use T-SQL to directly query data in a data lake by using a serverless SQL pool. That way, you can achieve rapid data exploration.*

6. On the left navigation pane, select **Develop** hub, then expand **SQL scripts**.

7. Select the **1 Query Campaign And Twitter Data Using T-SQL Language** script.

![Query Campaign And Twitter Data Using TSQL Language](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3307.png?raw=true)

*You can directly query external files stored in ADLS Gen2 storage without first copying or loading the data into a specialized store. You can query the data by using the familiar T-SQL syntax.*

8. In the **Connect to** dropdown list, ensure that **Built-in** is selected. 

*You will use the built-in endpoint for this service that’s provided within every Azure Synapse workspace. It’s a Synapse serverless SQL pool.*

> **Note:** Collapse the navigation pane on the left by selecting the << icon on the top right of the panes.

9.	In the **Use database** dropdown list, ensure that **AnalyticsServerlessPool** is selected.

10.	To query the first 100 campaigns, in the script file, select lines 5-12.

11.	Select **Run**.

12.	Review the query result in the lower pane.

>[!alert] Please update the storage URI (line 9 in the SQL script) with +++https://storage@lab.LabInstance.Id.dfs.core.windows.net/data-source/Campaign Data/campaign-data2.csv+++

![Select Run](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img3312.png?raw=true)

Using familiar T-SQL, we can also directly query external files stored in Azure storage without copying or loading data. This is a quick and easy way to read the content of the files without pre-configuring a dedicated SQL pool. Azure Synapse Analytics comes with built-in serverless SQL endpoint.

*Now you will create a view of the campaign files saved in Azure Storage.*

13. To create a view that queries the first 100 rows of campaign data, select lines 35-44 in the script file.

14.	Select **Run** to create a view of the Campaign file in Serverless pool.

>[!alert] Please update the storage URI (line 41 in the SQL script) with +++https://storage@lab.LabInstance.Id.dfs.core.windows.net/data-source/Campaign Data/campaign-data2.csv+++

![Select Run](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3314.png?raw=true)

With the relevant metadata placed in an Azure storage account, the views will allow us to reuse those queries in other places like Power BI, in conjunction with serverless SQL pool.

*Executing ad hoc queries and creating views over data in the data lake by using a Synapse serverless SQL pool is straightforward*.

Now you will verify the view that was just created.

15. Select **Data** hub from the left navigation pane.
16. Under **SQL Database**, expand **AnalyticsServerlesspool(SQL)**, then expand the **Views** folder.
17. Expand **dbo.Vw_CampaignData** to open the **Columns** folder and review the columns.
 
 ![The view created by running the query](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img3317.png?raw=true)

We can do similar SQL based Analytics with Azure Databricks. Let's see how.

----  


## Task 3.4 (OPTIONAL): Explore SQL Analytics with Azure Databricks. <a name="explore-sql-analytics-with-azure-databricks"></a>


Azure Databricks provides an environment that allows you to run quick ad hoc SQL queries on your data lake. Queries support multiple visualization types that help you explore query results from different perspectives.

In this task, you will explore some SQL analytics features of Azure Databricks, including export, import, and running a workbook.

1. In the search box of Azure portal(tab), enter: **Azure Databricks**

2. In the search results pane, select Azure Databricks.

![Select Azure Databricks](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3402.png?raw=true)

3. In the **Azure Databricks** page, select the resource that has a name starting with **databricks**.

*Note: Each user has their own unique instance of this resource. Each Azure Databricks workspace is provisioned with a full-featured development environment.*

![Select Azure Databricks resource](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img343.png?raw=true)

4. In the Azure Databricks resource page, **launch Databricks workspace in new tab using URL**.

!IMAGE[databricksWorkspace.png](instructions230217/databricksWorkspace.png)

*Now you will export a Databricks notebook in HTML format to your local machine.*

5. In the Databricks web session (tab), select **Workspace** from left navigation.


6. Select the **04_SQL_Analytics_On_Delta_Live_Tables** notebook.

![Go to 04_SQL_Analytics_On_Delta_Live_Tables](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3405.png?raw=true)

7. Review cmd 4 cell.

**Raw Twitter Data - Bronze**

*The bronze layer stores the raw, unprocessed data from Twitter API pulls. By leaving it in its raw state, there's an option to reprocess it for different purposes in the future. Thanks to Azure Data Lake Gen2, it is possible to maintain this data for as long as possible at a very low cost.*
*The bronze layer is usually the domain of data engineers who build pipelines to refine this data and forward it into the silver layer.*

![Raw Twitter data](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3406.png?raw=true)

8. Review cmd 7 cell.

**Filtered Twitter Data - Silver**

*In the silver layer, the raw Twitter data is curated into something more usable for data scientists.*
*They can use this clean data product to develop features for machine learning models and aggregated analytical datasets for data analysts*.

![Filtered Twitter data](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3407.png?raw=true)

9. Review cmd 9 cell.

**Curated Twitter Data - Gold**

*The gold layer is used to enhance and refine the silver layer datasets even further so it's ready for fit-for-purpose tables and views for specific analytical needs.*
*Here we've augmented the Twitter data with a machine learning model to identify the sentiment (positive, neutral, or negative) of each tweet.*

![Curated Twitter data](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3408.png?raw=true)

10. Review cmd 11 cell.

**Aggregations are a Great User Experience Enhancement**

*By pre-emptively aggregating the data that rarely or slowly changes, it provides a great performance benefit to end users.*
*The DLT pipeline performs this aggregation of hashtag counts by the geolocation of the tweets.*
By updating this everytime more tweets are ingested, it can keep the aggregation table up-to-date and then quickly consume and visualize it in tools like Power BI. One nice feature of Databricks notebooks is, if a cell produces a DataFrame output (like the one below), you can  profile the data and generate quick visualizations. Throw in Markdown and comments, and notebooks are a convenient way to collaborate and communicate with your team, leadership, customers, and other stakeholders.

![Aggregations Are A Great User Experience Enhancement](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3410.png?raw=true)


11. Review cmd 20 cell.

**Z-Order Optimization**

*Z-Ordering is a technique to co-locate related information in the same set of files.*
*This co-locality is automatically used by Delta Lake on Databricks data-skipping algorithms.*
*This behavior dramatically reduces the amount of data that Delta Lake on Databricks needs to read.*

![Z-Order Optimization](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3411.png?raw=true)

12. Review cmd 22 cell.

**Caching**

*Caching reduces scanning of the original files in future queries. It caches contents of a table in Apache Spark cache. If a query is cached, then a temperoray view is created for this query.*

![Caching](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3412.png?raw=true)

13.  Review cmd 24 cell.

**Time Travel**

*In the audit history we can see the history of the different versions of a table. You can also load and display any of those versions.*

![Time Travel](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image3413.png?raw=true)

===
# **Exercise 4: Glimpse of Purview to govern the overall data and analytics estate**

In Exercise 1, you loaded raw data into the Lakehouse. Then, in Exercise 2, you used a Delta Live Table pipeline to transform it into a data product for downstream consumption by analysts. 

In Exercise 3, you applied machine learning operations on this data product to build a customer sentiment model. This sentiment analysis allows Wide World Importers to determine which hashtags are trending so they can customize their campaigns to improve their sales while retaining their existing customers.

Meanwhile, Microsoft Purview provides a unified data governance service that helps manage and govern Wide World Importers’ data, which is stored in multi-cloud environments and in data sources such as Oracle, Teradata, ADLS Gen2, and Azure SQL Database.

In this exercise, you will explore Wide World Importers data estate that’s registered in Microsoft Purview.

1.	In the seaarch box of Azure portal (tab), enter: **Microsoft Purview**.

2.	In the search results pane, select **Microsoft Purview accounts**.

![Search Microsoft Purview](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img402.png?raw=true)

3.	In the **Microsoft Purview accounts** page, select the resource that has a name starting with **purviewanalytics**.

>**Note:** Each user has their own unique instance of this resource.


![Select the resource](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/img403.png?raw=true)

4.	In the Microsoft Purview accounts resource page, in the **Open Microsoft Purview Governance Portal** tile, select the **Open** link. This opens Microsoft Purview Governance Portal.

![Open Microsoft Purview](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image4004.png?raw=true)

5.	In the Microsoft Purview Governance Portal (tab), select the [**Documentation** link](https://docs.microsoft.com/en-us/azure/purview/use-azure-purview-studio)

*The Microsoft Purview documentation can help you learn how to:*

- Create a holistic, up-to-date map of your data landscape with automated data discovery, sensitive data classification, and end-to-end data lineage.
- Enable data curators to manage and secure your data estate.
- Empower data consumers to find valuable, trustworthy data.

![select the documentation link](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image4005.png?raw=true)


6. In the Microsoft Purview Governance Portal (tab), at the left, select the **Data map**.

*Data map makes your data meaningful by graphing your data assets and their relationships across your data estate. Use data map to discover data and manage access to that data.*

7.	In the left pane, select **Sources**.

![Select Sources](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image4008.png?raw=true)

8. In the map view, for the root collection item, select the plus (+) icon to reveal the collections.

![Select the + icon](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image4009.png?raw=true)

9.	Expand each of the collections to review specific sources related to those collections.

![Sources related to the collection](https://github.com/SD-14/Ignite-Demo/blob/main/media/images/image4010.png?raw=true)

----

Congratulations! You as Data Engineers, have helped Wide World Importers gain actionable insights from its disparate data sources, thereby contributing to future growth, customer satisfaction, and competitive advantage.

===

In this lab we experienced the creation of a simple, integrated, open and governed Data Lakehouse foundation using the Microsoft Analytics Solution Pattern. 

In this lab we covered the following: 
1.	First, we looked at data ingestion from a spectrum of analytical and operational data sources into the Lakehouse. We started with streaming data and analytics pipeline using ADX for a near real-time analytics scenario, followed by Synapse pipelines that ingested raw data from analytical/operational data sources to the Bronze layer. 

2.	Second, we explored offline data and analytics pipeline using open Delta format and Azure Databricks Delta Live Tables. We stitched streaming and non-streaming data (landed earlier) together, to create a combined data product to build a simple Lakehouse.

3.	Third, we explored ML and BI scenarios on the Lakehouse. Here we reviewed MLOps pipeline using the Azure Databricks managed MLflow with Azure ML. Then, using Power BI with Synapse serverless SQL pool capabilities, we derived actionable insights. We explored SQL Analytics with Azure Databricks and Azure Synapse Serverless. 

4. Finally, we leveraged Purview for data governance. 

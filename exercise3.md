
## Exercise 3: Building an AI-Powered Chatbot with Microsoft Fabric and Azure AI Studio

Contoso encountered a major issue with customer churn, especially among millennials. The executives at Contoso struggled to understand this customer segment and figure out how to earn their loyalty. Despite having extensive data from customer interactions, surveys, and market research, Contoso found it difficult to pinpoint the root cause of the churn and determine effective solutions. 

The main problem was the lack of integration in their existing systems. This prevented Contoso's executives from utilizing their data for root cause analysis and strategic insights, which in turn, hampered their ability to improve marketing strategies, product offerings, and customer experiences. 

To solve the data silos issue, Contoso implemented an advanced AI solution using Azure OpenAI, Azure AI Search, and Microsoft Fabric. Once the team discovered that millennials were leaving because they couldn't find products, they developed an Azure OpenAI-powered shopping assistant to help with product search and recommendations. 

In this exercise, we will learn how they achieved this! 

### Task 3.1: Integrate Fabric data with Azure AI Studio using Azure AI Search

Let's step into the shoes of Eva, the Data Engineer, as she launches Azure AI Studio and leverages data stored in Microsoft OneLake as knowledge base.

1. Navigate back to the Microsoft Fabric tab on your browser (https://app.fabric.microsoft.com).
 
2. Click on **Workspaces** and select **ContosoSales@lab.LabInstance.Id**.
 
![task-1.3.02.png](media/task-1.3.02.png)

3. Click **Manage access**.

![th07.png](media/th07.png)

4. Click **+ Add people or groups**.

![th08.png](media/th08.png)

5. Type +++srch-@lab.LabInstance.Id+++, select **Contributor** from the permission dropdown, and then click **Add**.

![th09.png](media/th09.png)

6. Click on **ContosoSales@lab.LabInstance.Id** from the left-hand side menu, then select **Lakehouse**.

![th03.png](media/th03.png)

7. Copy the **browser URL** as shown in the screenshot, and paste it into your notepad for later use.

![th04.png](media/th04.png)

8. Navigate to the Azure portal (+++Portal.azure.com+++), search for +++**rg-build25-@lab.LabInstance.Id**+++, and select it.

![th01.png](media/th01.png)

9. Search for **Search service**, and select the appropriate +++**srch-@lab.LabInstance.Id**+++ service from the results.

![th02.png](media/th02.png)

10. In the Search service, click on the **Import data** option to begin setting up the data source.

![th05.png](media/th05.png)

11. In the **Existing data source** dropdown, select the **OneLake files (preview)** option.

![th06.png](media/th06.png)

12. In the Connect to your data section, configure the following fields:

- **Data Source**: Select **OneLake files (preview)**.

- **Data source name**: Enter +++**onelake**+++.

- **Data to extract**: Select **All metadata**.

- **Parsing mode**: Select **JSON array**.

- **Connect by**: Choose **Lakehouse URL**.

- **Lakehouse URL**: Paste the Lakehouse URL you copied in the **Step 7**.

- **Lakehouse folder/shortcut**: Enter +++**products**+++.

- **Managed identity authentication**: Select **System-assigned**.

13. Click on **Next: Add cognitive skills (Optional)** to proceed.

![th20.png](media/th20.png)

14. Click on **Skip to: Customize target index** to proceed.

![th10.png](media/th10.png)

15. Set **Index name** to +++onelake-index+++.

16. Set the **Key** field to ``id``.

![th11.png](media/th11.png)

17. For the fields listed, configure the following:

- **productId**: Enable **Searchable**.

- **product**: Enable **Retrievable**, **Filterable** and **Searchable**.

- **color**: Enable **Retrievable**, **Filterable** and **Searchable**.

- **imageUrl** : Enable **Retrievable**.

- **Price** : Enable **Retrievable** and **Sortable**.

- **gender**: Enable **Retrievable**, **Filterable** and **Searchable**.

- **MasterCategory**: Enable **Searchable**.

- **subCategory**: Enable **Searchable**.

- **color**: Enable **Retrievable**, **Filterable** and **Searchable**.

- **Description** : Enable **Retrievable** and **Searchable**.

- **caption**: Enable **Searchable***.

- **Vector_embedding**: Enable **Retrievable**.

- **AzureSearch_DocumentKey**: Enable **Retrievable**.


18. Once the field settings are configured, click on **Next: Create an indexer** to proceed.

![st05.png](media/st05.png)

19. Enter the name of the indexer as **onelake-indexer** and click on the **Submit** button.

![th13.png](media/th13.png)


---

### Task 3.2: Establish Azure OpenAI, Azure AI Content Safety, and AI Search Connections in Azure AI Studio

Contoso integrated all of their data sources using Microsoft Fabric, including customer feedback, sales records, social media interactions, and encompassing internal company policy documents such as SOPs and research articles on customer behavior into Azure AI Search. 
This created a unified, searchable knowledge base. 

Let's step into Data Engineer, Eva's shoes to see how.

1. In a new tab of your VM browser enter the URL +++https://ai.azure.com/manage/projects+++ and press **Enter** key. Now, in the Azure AI studio click on **prj-build-@lab.LabInstance.Id** project.


![th2.png](media/th2.png)

>**Note:** Close any pop-up that appears on the screen throught the lab.

![st04.png](media/st04.png)

>**Note:** Click on the **Expand** icon, if the left navigation is hidden.

![prjexpand.png](media/prjexpand.png)

2. Scroll down and click on the **Management center** from the bottom of the navigation menu.

![th14.png](media/th14.png)

3. Click **Connected resources** and select **New connection**.

![th15.png](media/th15.png)

3. Select **Azure OpenAI Service**.

![ai_4.png](media/ai_4.png)

4. You will find an Azure OpenAI resource with gpt-4o and text-embedding-ada-002 model deployment. Create a connection by clicking on the **Add connection** button.

![st07.png](media/st07.png)

5. Once the **OpenAI services are connected**, click on **Back to select an asset type**.

![st08.png](media/st08.png)

6. Click on **Azure AI Search**.

![st008.png](media/st008.png)

7. Click on **Add connection**.

![st009.png](media/st009.png)

8. Once the **AI Search is connected**, click on the **Close** button.

![st09.png](media/st09.png)

9. Notice that **Azure Open AI** and **Azure AI Search** connections are established successfully.

![st10.png](media/st10.png)

---
<!--
### Task 3.3: Create and configure a Vector Index in Azure AI Studio with Azure AI Search and OpenAI Connections

Contoso indexed OneLake data in Azure AI Studio to improve the efficiency of searching and retrieving large datasets, enabling faster, data-driven decision-making across the organization. This approach enhances accessibility, scalability, and workflow for data scientists and analysts, while also providing a better user experience and reducing operational costs.. 

Let's see how Eva, the Data Engineer, indexed OneLake data in Azure AI Studio.

1. In the left navigation pane, click on **Go to Project** button.
  
![prj-nv3.png](media/prj-nv3.png)

2. Scroll down in the left navigation pane and click on **Data + indexes**, switch to **Indexes** tab then click on the **+ New index** button.

![prj-nv4.png](media/prj-nv4.png)

3. In the Data source dropdown, select **Azure AI search**.

![23.png](media/23.png)

4. Click on the **Next** button.

![24.png](media/24.png)

5. In the Select Azure AI Search service dropdown, select **srch@lab.LabInstance.Id**.

6. In the Select Azure AI Search index dropdown, select **cosmosdb-index** and then click on the **Next** button.

**Note:** If you get an error like "Unable to load search service indexes.Request failed with status code 403." please proceed by selecting Index.

![25_1.png](media/25_1.png)

7. In the Azure OpenAI connection dropdown, select **openAIResource2@lab.LabInstance.Id**  and then click on the **Next** button.

![26_1.1.png](media/26_1.1.png)

8. Click on the **Next** button.

![27_1.png](media/27_1.png)

9. Click on the **Create vector index** button.

![28_1.png](media/28_1.png)

> [!IMPORTANT]
> *Please wait for the index to load. It takes approximately 1-2 minutes.*

10. The screen displayed will resemble the image below, featuring the message **Index not found**. This is normal. Please wait for a few moments, then click on **Data + indexes**.

![prj-nv5.png](media/prj-nv5.png)

11. Click on **Indexes** tab and check the **Status** which will show as **Ready**. Continue with the next task.

![prj-nv7.png](media/prj-nv7.png)

---
-->

### Task 3.3: Setup and use Prompt Flow in Azure AI Studio

Prompt flow in Azure AI Studio offers a comprehensive, streamlined environment for creating AI applications. It provides a visual interface for orchestrating flows, and enables iterative prompt engineering. Azure AI Studio includes built-in evaluation tools, seamless deployment options, and integration with Azure's ecosystem. It also offers enterprise-level security and scalability, making it ideal for developing, testing, and deploying sophisticated AI solutions efficiently. Let's explore how Contoso deployed and tested a Prompt flow.

1. In the left navigation pane, click on **Go to Project** button.

![st06.png](media/st06.png)

2. Click on **Prompt flow** from the left navigation pane and then click on the **+ Create** button.

![st11.png](media/st11.png)

3. Scroll down and click on the **Upload** button in the Upload from local section.

![31.png](media/31.png)

4. Click on the **Zip file** radio button and then click on **Browse**.

![32.1.png](media/32.1.png)

5. Copy the path +++C:\Lab Assets\01_Main_Lab_Assets\artifacts\aistudio+++, paste it in the **File name** textbox and then click on the **Open** button.

 ![32.1.1.png](media/32.1.1.png)

6. Click on **shopping-assistant-prompt-flow** and then click on the **Open** button.

   ![promptziploc.png](media/promptziploc.png)

7. In the Select flow type dropdown, select **Chat flow** and then click on the **Upload** button.

![st12.png](media/st12.png)

>**Note:** If clicking on the Upload button doesn't redirect you to the Prompt Flow screen, click the Upload button again. If it still doesn't work, refresh the page and try uploading again.

8. Click on the **Start compute session** button.

**Note:** It will take approximately **2-3 minutes** to start the compute session. Please wait for some time.

![35_1.png](media/35_1.png)

9. Scroll down to the **lookup** node in the Prompt flow graph and click on it.

10. Click on the edit icon (shaped like a pencil) to modify the value for **mlindex_content** as shown in the below screenshot.

![st13.png](media/st13.png)

11. Click on the **acs_index_connection** dropdown and select the **srch@lab.LabInstance.Id**.

12. Click on the **acs_index_name** dropdown and select the **onelake-index**.

13. Click on the **embedding_type** dropdown and select the **Azure OpenAI**.

14. Click on the **aoai_embedding_connection** dropdown and select the **openAIResource2@lab.LabInstance.Id**.

15. Click on the **Save** button.

![st14.png](media/st14.png)

16. In the **lookup** node, set **query_type** to **Keyword**.

![st15.png](media/st15.png)

17. Click on **prompt_for_looks** in the Graph, click on the **Connection** dropdown and then select **openAIResource2@lab.LabInstance.Id**.

18. In the **Deployment_name** dropdown, select **gtp-4o**.

![st16.png](media/st16.png)

19. Click on the **Chat** button.

![prj-nv10.png](media/prj-nv10.png)

20. Click **+ icon** to start a new session and replace the default **prompt** and paste the **prompt** given below in chat box.

```
Can you show me some Indian dresses for a wedding in Udaipur?
```
21. Click on the **send** icon.

![prj-nv11new.png](media/prj-nv11new.png)

22. Observe the **response**.

![39_1.png](media/39_1.png)

Once the Prompt flow is deployed as an endpoint, It can be consumed in the webapplication. Let's see how the response look like in the webapp.
 
23. Open a new tab, click on browser address bar, and click +++app-shopping-copilot-@lab.LabInstance.Id.azurewebsites.net+++ and then press Enter.

![Contosoterms.1.png](media/Contosoterms.1.png)

24. Click on the **terms and conditions checkbox** and then click on the **Login** button.

![Contosoterms.png](media/Contosoterms.png)
 
25. Click on the **Copilot icon** at the bottom right of the page.
 
![Copiloticonwebapp.png](media/Copiloticonwebapp.png)

26. Click on any of the **pre-populated questions**.
 
![question1webapp.png](media/question1webapp.png)
 
27. Observe the **response**.
  
![Answer1webapp.png](media/Answer1webapp.png)
 
With their new Shopping Copilot, Contoso was able to provide their customers with an online shopping experience that has an in-store feel. This simulates a personalized shopping experience that helps increase customers' engagement with enhanced data insights.

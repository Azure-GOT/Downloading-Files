**Q1.** You need to build a chatbot that meets the following requirements:
- Supports chit-chat, knowledge base, and multilingual models
- Performs sentiment analysis on user messages
- Selects the best language model automatically

What should you integrate into the chatbot?

1. QnA Maker, Language Understanding, and Dispatch
2. Translator, Speech, and Dispatch
3. Language Understanding, Text Analytics, and QnA Maker	
4. Text Analytics, Translator, and Dispatch

**Ans: 3. Language Understanding, Text Analytics, and QnA Maker**

**Explanation:** Language Understanding- Used to selects the best language model automatically, Text Analytics- Used to perform sentiment analysis, QnA Maker- Used to create a natural conversational layer over data so it would be helpful in supporting chit-chat, knowledge base, and multilingual models

---

**Q2.** Your company wants to reduce how long it takes for employees to log receipts in expense reports. All the receipts are in English.
You need to extract top-level information from the receipts, such as the vendor and the transaction total. The solution must minimize development effort.

Which Azure Cognitive Services service should you use?
1. Custom Vision
2. Personalizer
3. Form Recognizer
4. Computer Vision

**Ans: 3. Form Recognizer**

**Explanation:** Azure Form Recognizer identify and extract text, key/value pairs, selection marks, tables, and structure
from documents. Form Recognizer is composed of custom document processing models, prebuilt models for invoices, receipts, 
IDs and business cards, and the layout model.

---

**Q3.** You are developing a new sales system that will process the video and text from a public-facing website.
You plan to monitor the sales system to ensure that it provides equitable results regardless of the user's location or background.

Which two responsible AI principles provide guidance to meet the monitoring requirements? Each correct answer presents part of the solution. (Choose two.)
1. transparency
2. fairness
3. inclusiveness
4. reliability and safety
5. privacy and security

**Ans: 2. fairness and 4. reliability and safety**

**Explanation:** AI systems should treat all people fairly. AI systems should perform reliably and safely.

---

**Q4.** You successfully run the following HTTP request.
POST https:// management.azure.com /subscriptions/18c51a87-3a69-47a8-aedc-a54745f708a1/resourceGroups/RG1/providers/Microsoft.CognitiveServices/accounts/contosol/regenerateKey?api-version=2017-04-18 
Body{"keyName": "Key2"}

What is the result of the request?
1. A key for Azure Cognitive Services was generated in Azure Key Vault.
2. A new query key was generated.
3. The primary subscription key and the secondary subscription key were rotated.
4. The secondary subscription key was reset.

**Ans: 2. A new query key was generated**

---

**Q5.** A customer uses Azure Cognitive Search.
The customer plans to enable a server-side encryption and use customer-managed keys (CMK) stored in Azure.

What are three implications of the planned change? Each correct answer presents a complete solution.
1. The index size will increase
2. Query times will increase
3. A self-signed X.509 certificate is required
4. The index size will decrease
5. Query times will decrease
6. Azure Key Vault is required

**Ans: 1. The index size will increase, 2. Query times will increase, 6. Azure Key Vault is required**

---

**Q6.** You have to notify users that their data has been processed by the sales system(process the video and text from a public-facing website).

Which AI principle is resposible for that?
1. transparency
2. fairness
3. inclusiveness
4. reliability and safety

**Ans: 1. transparency**

---

**Q7.** Consider the following scenario: You create a web app named **app1** that runs on an Azure virtual machine named **vm1**. Vm1 is on an Azure virtual network named **vnet1**.
You plan to create a new Azure Cognitive Search service named **service1**.
You need to ensure that **app1** can connect directly to **service1** without routing traffic over the public internet.

**Solution 1:** You deploy **service1** and a public endpoint to a new virtual network, and you configure Azure Private Link

**Ans: Yes**

**Solution 2:** You deploy service1 and a public endpoint, and you configure an IP firewall rule

**Ans: No** 

**Solution 3:** You deploy service1 and a public endpoint, and you configure a network security group (NSG) for vnet1

**Ans: No**

---

**Q8.** You plan to perform predictive maintenance.
You collect IoT sensor data from 100 industrial machines for a year. Each machine has 50 different sensors that generate data at one-minute intervals. In total, you have 5,000 time series datasets.
You need to identify unusual values in each time series to help predict machinery failures.

Which Azure Cognitive Services service should you use?
1. Anomaly Detector
2. Cognitive Search
3. Form Recognizer
4. Custom Vision

**Ans: 1. Anomaly Detector**

---

**Q9.** You plan to provision a QnA Maker service in a new resource group named RG1.
In RG1, you create an App Service plan named AP1.

Which two Azure resources are automatically created in RG1 when you provision the QnA Maker service? 
1. Language Understanding
2. Azure SQL Database
3. Azure Storage
4. Azure Cognitive Search
5. Azure App Service

**Ans: 4. Azure Cognitive Search, 5. Azure App Service**

---

**Q10.** You are building a language model by using a Language Understanding service.
You create a new Language Understanding resource.
You need to add more contributors.

What should you use?
1. A conditional access policy in Azure Active Directory (Azure AD)
2. The Access control (IAM) page for the authoring resources in the Azure portal
3. The Access control (IAM) page for the prediction resources in the Azure portal

**Ans: 2. The Access control (IAM) page for the authoring resources in the Azure portal**

---

**Q11.** You have a Video Indexer service that is used to provide a search interface over company videos on your company's website.
You need to be able to search for videos based on who is present in the video.

What should you do?
1. Create a person model and associate the model to the videos
2. Create person objects and provide face images for each object
3. Invite the entire staff of the company to Video Indexer
4. Edit the faces in the videos
5. Upload names to a language model

**Ans: 1. Create a person model and associate the model to the videos**

---

**Q12.** You use the Custom Vision service to build a classifier.
After training is complete, you need to evaluate the classifier.

Which two metrics are available for review?
1. recall
2. F-score
3. weighted accuracy
4. precision
5. area under the curve (AUC)

**Ans: 1. recall, 4. precision**

---

**Q13.** You are building a Language Understanding model for an e-commerce platform.
You need to construct an entity to capture billing addresses.

Which entity type should you use for the billing address?
1. machine learned
2. Regex
3. geographyV2
4. Pattern.any
5. list

**Ans: 2. Regex**

---

**Q14.** You need to upload speech samples to a Speech Studio project.

How should you upload the samples?
1. Combine the speech samples into a single audio file in the .wma format and upload the file
2. Upload a .zip file that contains a collection of audio files in the .wav format and a corresponding text transcript file
3. Upload individual audio files in the FLAC format and manually upload a corresponding transcript in Microsoft Word format
4. Upload individual audio files in the .wma format

**Ans: 2. Upload a .zip file that contains a collection of audio files in the .wav format and a corresponding text transcript file**

---

**Q15.** You have a chatbot that was built by using the Microsoft Bot Framework.
You need to debug the chatbot endpoint remotely.

Which two tools should you install on a local computer?
1. Fiddler
2. Bot Framework Composer
3. Bot Framework Emulator
4. Bot Framework CLI
5. ngrok
6. nginx

**Ans: 3. Bot Framework Emulator, 5. ngrok**

---

**Q16.** You need to measure the public perception of your brand on social media by using natural language processing.

Which Azure Cognitive Services service should you use?
1. Text Analytics
2. Content Moderator
3. Computer Vision
4. Form Recognizer

**Ans: 1. Text Analytics**

---

**Q17.** You build a language model by using a Language Understanding service. The language model is used to search for information on a contact list by using an intent named FindContact.
A conversational expert provides you with the following list of phrases to use for training.
- Find contacts in London.
- Who do I know in Seattle?
- Search for contacts in Ukraine.

You need to implement the phrase list in Language Understanding

**Solution 1:** You create a new intent for location

**Ans: Yes**

**Solution 2:** You create a new entity for the domain

**Ans: No**

**Solution 3:** You create a new pattern in the FindContact intent

**Ans: No**

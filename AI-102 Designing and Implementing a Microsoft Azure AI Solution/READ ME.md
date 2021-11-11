Q1. You need to build a chatbot that meets the following requirements:
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

Q2. Your company wants to reduce how long it takes for employees to log receipts in expense reports. All the receipts are in English.
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

Q3. You are developing a new sales system that will process the video and text from a public-facing website.
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

Q4. You successfully run the following HTTP request.
POST https:// management.azure.com /subscriptions/18c51a87-3a69-47a8-aedc-a54745f708a1/resourceGroups/RG1/providers/Microsoft.CognitiveServices/accounts/contosol/regenerateKey?api-version=2017-04-18 
Body{"keyName": "Key2"}

What is the result of the request?
1. A key for Azure Cognitive Services was generated in Azure Key Vault.
2. A new query key was generated.
3. The primary subscription key and the secondary subscription key were rotated.
4. The secondary subscription key was reset.

**Ans: 2. A new query key was generated**

---

Q5. A customer uses Azure Cognitive Search.
The customer plans to enable a server-side encryption and use customer-managed keys (CMK) stored in Azure.

What are three implications of the planned change? Each correct answer presents a complete solution.
1. The index size will increase
2. Query times will increase
3. A self-signed X.509 certificate is required
4. The index size will decrease
5. Query times will decrease
6. Azure Key Vault is required

**Ans: 1. The index size will increase, 2. Query times will increase, 3. Azure Key Vault is required**

---

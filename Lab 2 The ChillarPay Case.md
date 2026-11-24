# ASSESSMENT 1 – LAB 2 **<u>FROM ZERO-SHOT TO FEW-SHOT: THE CHILLARPAY CASE</u>** 

**_Name:_** _Himanshi_ 

**_Course:_** _BBA (FinTech)_ **_University:_** _Chitkara University_ **_Subject:_** _Generative AI / Prompt Engineering_ **_Assessment:_** _Individual – 3 Marks_ **_Tool Used:_** _ChatGPT_ 

**_Date:_** _November 2026_ 

## <u>STEP 1: CASE STUDY</u> 

### **<mark>Introduction to ChillarPay</mark>** 

ChillarPay is a fictional UPI payments application based in Jaipur. It is mainly used by college students and small shopkeepers. The application has approximately 8 lakh users and receives around 2,000 customer support messages every day in English and Hinglish. 

The company has a six-member customer support team that struggles to handle all customer complaints. Sometimes urgent fraud-related complaints get mixed up with simple questions. 

The Head of Customer Experience wants to know whether AI can help classify customer messages, assign priorities and draft replies. 

### **<mark>Business Problem</mark>** 

The main problem is that ChillarPay receives too many customer support messages, making it difficult to identify urgent complaints quickly. 

AI can help by: 

- Classifying customer complaints into categories. 

- Identifying high-priority complaints. 

- Drafting short and polite customer replies. 

- Reducing the workload of the support team. 

### **<mark>ChillarPay Support Rules</mark>** 

### **<u><mark>Category Description</mark></u>** 

Failed Payment Payment failed or money was deducted without successful payment. 

Refund Customer is asking about a refund or refund status. 

Fraud Alert Unauthorised transactions or suspicious account activity. 

Account & KYC Login problems, account issues and KYC-related problems. 

### **<mark>Priority Rules</mark>** 

|**Priority**|**Meaning**|
|---|---|
|High|Money lost without customer's consent or account<br>blocked.|
|Medium|Money stuck or delayed, or refund pending.|
|Low|Information request or profile update.|
|**Custome**|**r Reply Rules**|



|1. Replies should be polite and short.|
|---|
|2. Use the customer's first name if provided.|
|3. Never promise a refund date.|
|4. Reply in Hinglish if the customer writes in Hinglish.|



## <u>STEP 2: CREATE A SYNTHETIC CUSTOMER DATASET</u> 

### **<mark>Objective</mark>** 

The objective is to create 12 fictional customer support messages to test how AI handles different types of customer complaints. 

Synthetic data is used because real customer information is private and should not be exposed during AI testing. 

### **<mark>Prompt Used</mark>** 

You are helping me build a realistic test dataset for a business case study. 

ChillarPay is a fictional UPI payments app in Jaipur used by college students and small shopkeepers. Its support categories are: Failed Payment, Refund, Fraud Alert, Account & KYC. 

Create 12 synthetic customer messages that ChillarPay's support team might receive. 

### **<mark>Rules:</mark>** 

- Fictional only: no real names, phone numbers, account numbers or UPI IDs. 

- 8 messages in English and 4 in Hinglish. 

- Cover all 4 support categories. 

- Include 3 tricky messages: one that could fit two categories, one that is very short or unclear, and one from an angry customer. 

- Do NOT show the category, priority or any reply. 

- Output a table with these columns: ID (M01 to M12) | Customer message | Channel (App chat / Email / Twitter). 

|**Gener**|**ated Dataset**||
|---|---|---|
|**ID**|**Customer Message**|**Channel**|
|M01|My UPI payment failed, but ₹2,000 was deducted from my bank account.|App chat|
|M02|I requested a refund five days ago, but I still haven't received my money.|Email|
|M03|Someone made a transaction from my account without my permission. I did not<br>approve it.|App chat|
|M04|I am unable to log in to my ChillarPay account after changing my mobile device.|App chat|
|M05|How can I update my registered email address in the application?|Email|
|M06|My KYC verification keeps getting rejected even though I uploaded a clear PAN<br>document.|App chat|
|M07|Money deducted, payment failed, refund bhi nahi aaya. Please help!|Twitter|
|M08|Bhai, mere account se paise kat gaye, maine koi transaction nahi kiya.|App chat|
|M09|Refund?|App chat|
|M10|Your app is useless! My payment has been stuck for three days, and nobody is<br>helping me.|Twitter|
|M11|I paid a shopkeeper through UPI, my account was debited, but the shopkeeper<br>never received the payment.|Email|
|M12|Mera account block ho gaya hai aur main login nahi kar paa raha. Please help karo!|App chat|
|**Datase**|**t Observation:**||
|The da   i<br>covers       f     i|taset contains 12 fictional customer messages, including English and Hinglish compl<br>all four support categories and includes difficult messages to test AI classification ac|i       aints. It<br>f     i curacy.|
|STEP|3: PREPARE THE CORRECT ANSWER KEY||



### **<mark>Objective</mark>** Before testing AI, a correct answer key is prepared using ChillarPay's business rules. This helps compare AI-generated answers with the expected answers. **<mark>Correct Answer Key</mark>** 

|**ID**|**Correct Category**|**Correct Priority**|
|---|---|---|
|M01|Failed Payment|Medium|



|M02|Refund|Medium|
|---|---|---|
|M03|Fraud Alert|High|
|M04|Account & KYC|Low|
|M05|Account & KYC|Low|
|M06|Account & KYC|Low|
|M07|Failed Payment|Medium|
|M08|Fraud Alert|High|
|M09|Refund|Low|
|M10|Failed Payment|Medium|
|M11|Failed Payment|Medium|
|M12|Account & KYC|High|



### **<mark>Reasoning:</mark>** 

- M01: Money is deducted but payment failed, so **medium** priority. 

- M02: Refund is pending, so **medium** priority. 

- M03: Unauthorised transaction, so **High** priority. 

- M04: Login issue after changing device, so **low** priority. 

- M05: Email update is an information request, so **low** priority. 

- M06: KYC rejection is an account-related issue, so **low** priority. 

- M07: Failed payment and refund complaint, so Failed Payment and **medium** priority. 

- M08: Unauthorised money deduction, so Fraud Alert and High priority. 

- M09: Only asks about a refund without explaining a pending transaction, so **low** priority. 

- M10: Payment is stuck, so **medium** priority. 

- M11: Money is deducted but shopkeeper has not received it, so **medium** priority. 

- M12: Account is blocked, so **high** priority. 

## <u>STEP 4: ZERO-SHOT PROMPTING – SUMMARISATION</u> 

### **<mark>Objective</mark>** 

Zero-shot prompting means giving AI instructions without providing any solved examples. 

In this step, AI is asked to summarise all 12 customer messages in one short line. 

**<mark>Prompt Used</mark>** 

Summarise each ChillarPay customer message below in one short line (maximum 12 words). Output a table: ID | Summary 

Messages: Use the 12 customer messages from Step 2. 

|**AI-Gen**|**erated Output**|
|---|---|
|**ID**|**Summary**|
|M01|UPI payment failed despite ₹2,000 being deducted.|
|M02|Refund has not arrived after five days.|
|M03|Unauthorised transaction occurred without customer<br>permission.|
|M04|Customer cannot log in after changing devices.|
|M05|Customer wants to update their registered email.|
|M06|KYC rejected despite uploading a clear PAN document.|
|M07|Payment failed, money deducted, and refund not received.|
|M08|Customer reports an unauthorised money deduction.|
|M09|Customer requests information about a refund.|
|M10|Customer is angry about a payment stuck for three days.|
|M11|Shopkeeper did not receive money despite successful debit.|
|M12|Customer's account is blocked, preventing login.|



### **<mark>Observation</mark>** 

Zero-shot prompting successfully summarised all 12 customer messages in short and understandable sentences. 

The AI understood the main problem without needing any examples. This shows that zero-shot prompting works well for simple and common tasks like summarisation. 

## <u>STEP 5: ZERO-SHOT PROMPTING – CUSTOMER SUPPORT TRIAGE</u> 

### **<mark>Objective</mark>** 

In this step, AI is asked to classify customer messages, assign priorities and generate customer replies using only instructions. 

The purpose is to check whether zero-shot prompting can follow ChillarPay's specific business rules. 

### **<mark>Prompt Used</mark>** 

You are a customer-support assistant for ChillarPay, a UPI payments app. 

For each customer message below, give: 

1. Category: one of Failed Payment, Refund, Fraud Alert, Account & KYC. 

2. Priority: High, Medium or Low, using these rules: 

   - **High** = money lost without the customer's consent, or account blocked. 

   - **Medium** = money stuck or delayed, refund pending. 

   - **Low** = information request or profile update. 

3. Reply: a reply in ChillarPay's tone: polite and short; use the customer's first name if given; never promise a refund date; reply in Hinglish if the customer writes in Hinglish. 

Output a table: ID | Category | Priority | Reply (maximum 25 words). 

Messages: Use the same 12 customer messages from Step 2. 

|**AI-Ge**|**nerated Output**|||
|---|---|---|---|
|**ID**|**Category**|**Priority**|**Reply**|
|M01|Failed Payment|Medium|Sorry for the inconvenience. Please share your transaction ID<br>so we can investigate the deducted amount.|
|M02|Refund|Medium|We apologise for the delay. Please share your refund<br>reference so we can check its status.|
|M03|Fraud Alert|High|We are sorry. Please immediately block UPI transactions in<br>the app. Our fraud team will investigate.|
|M04|Account & KYC|Low|Please try logging in using your registered mobile number and<br>follow the device verification process.|
|M05|Account & KYC|Low|You can update your registered email under Profile Settings in<br>the ChillarPay app.|
|M06|Account & KYC|Low|Sorry for the inconvenience. Please check your PAN details<br>and resubmit your KYC application.|
|M07|Failed Payment|Medium|Sorry for the trouble. Please share your transaction ID so we<br>can investigate your failed payment.|
|M08|Fraud Alert|High|Humein khed hai. Kripya turant app mein UPI block karein.<br>Hamari fraud team aapki complaint check karegi.|
|M09|Refund|Medium|Please share your transaction details so we can understand<br>your refund concern and assist you.|
|M10|Failed Payment|Medium|We apologise for the inconvenience. Please share your<br>transaction ID so our team can investigate the delay.|
|M11|Failed Payment|Medium|Sorry for the trouble. Please share your transaction ID so we<br>can track the payment.|



Humein khed hai. Kripya apni account details verify karein. Hamari team aapka blocked account check karegi. 

M12 Account & KYC High 

### **<mark>Evaluation</mark>** 

|**ID**|**Category**|**Priority**|**Evaluation**|
|---|---|---|---|
|M01|✔|✔|Correct|
|M02|✔|✔|Correct|
|M03|✔|✔|Correct|
|M04|✔|✔|Correct|
|M05|✔|✔|Correct|
|M06|✔|✔|Correct|
|M07|✔|✔|Correct|
|M08|✔|✔|Correct|
|M09|✔|✘|Priority should be Low|
|M10|✔|✔|Correct|
|M11|✔|✔|Correct|
|M12|✔|✔|Correct|



### **<mark>Observation:</mark>** 

Zero-shot prompting correctly classified most customer messages. However, it assigned Medium priority to M09 even though the message did not clearly mention a pending refund. 

It also replied in English to the Hinglish message M07. This shows that instructions alone may not always be enough for company-specific tasks. 

## <u>STEP 6: FEW-SHOT PROMPTING – CUSTOMER SUPPORT TRIAGE</u> 

### **Objective** 

Few-shot prompting means providing AI with instructions along with a few solved examples. 

In this step, three examples are added to the previous zero-shot prompt. The objective is to check whether examples improve AI's classification and customer replies. 

### **Prompt Used** 

You are a customer-support assistant for ChillarPay, a UPI payments app. 

For each customer message below, give: 

1. **Category:** one of Failed Payment, Refund, Fraud Alert, Account & KYC. 

2. **Priority:** High, Medium or Low, using these rules: 

   - High = money lost without the customer's consent, or account blocked. 

   - Medium = money stuck or delayed, refund pending. 

   - Low = information request or profile update. 

3. **Reply:** a reply in ChillarPay's tone: polite and short; use the customer's first name if given; never promise a refund date; reply in Hinglish if the customer writes in Hinglish. 

**Output a table:** ID | Category | Priority | Reply (maximum 25 words). 

Learn from these examples and follow the same style exactly: 

### **Example 1** 

**Message:** Bhai mere account se ₹3,000 kat gaye, maine koi payment nahi kiya! 

Output: Fraud Alert | High | Humein afsos hai. Turant app mein UPI block karein; hamari fraud team ise priority par check kar rahi hai. 

Example 2 

**Message:** Paid ₹450 to a shop, money debited but the shop did not get it. I want a refund. 

Output: Failed Payment | Medium | Sorry for the trouble. Failed payments usually reverse automatically; please share the transaction ID so we can track it. 

### **Example 3** 

Message: How do I change my registered email? 

Output: Account & KYC | Low | You can update your email under Profile > Settings in the ChillarPay app. 

**<mark>Messages:</mark>** <mark>Use the SAME 12 customer messages from Step 2.</mark> 

### **<mark>AI-Generated Output</mark>** 

|**ID**|**Category**|**Priority**|**Reply**|
|---|---|---|---|
||||Sorry for the trouble. Failed payments usually reverse|
|M01|Failed Payment|Medium|automatically; please share your transaction ID so we can<br>track it.|
|M02|Refund|Medium|We apologise for the delay. Please share your refund reference<br>so we can check its status.|
|M03|Fraud Alert|High|We are sorry. Immediately block UPI transactions in the app.<br>Our fraud team is checking your complaint.|
|M04|Account & KYC|Low|Please log in using your registered mobile number and follow<br>the device verification process.|



|M05|Account & KYC|Low|You can update your registered email under Profile Settings in<br>the ChillarPay app.|
|---|---|---|---|
|M06|Account & KYC|Low|Sorry for the trouble. Please verify your PAN details and<br>resubmit your KYC application.|
||||Sorry for the trouble. Failed payments usually reverse|
|M07|Failed Payment|Medium|automatically; please share your transaction ID so we can<br>track it.|
|M08|Fraud Alert|High|Humein afsos hai. Turant app mein UPI block karein; hamari<br>fraud team aapki complaint check kar rahi hai.|
|M09|Refund|Medium|Please share your transaction details so we can understand<br>your refund concern and assist you.|
|M10|Failed Payment|Medium|We apologise for the inconvenience. Please share your<br>transaction ID so our team can investigate the delay.|
||||Sorry for the trouble. Failed payments usually reverse|
|M11|Failed Payment|Medium|automatically; please share your transaction ID so we can<br>track it.|
|M12|Account & KYC|High|Humein afsos hai. Kripya app mein apne account ki details<br>verify karein. Hamari team aapki madad karegi.|



|**Evalua**|**tion**<br>|||
|---|---|---|---|
|**ID**|**Category**|**Priority**|**Evaluation**|
|M01|✔|✔|Correct|
|M02|✔|✔|Correct|
|M03|✔|✔|Correct|
|M04|✔|✔|Correct|
|M05|✔|✔|Correct|
|M06|✔|✔|Correct|
|M07|✔|✔|Correct|
|M08|✔|✔|Correct|
|M09|✔|✘|Priority should be<br>Low|
|M10|✔|✔|Correct|
|M11|✔|✔|Correct|



Correct 

M12 

✔ 

✔ 

### **<mark>Observation:</mark>** 

Few-shot prompting provided more consistent replies by showing AI examples of how ChillarPay handles customer complaints. 

However, the AI still assigned the wrong priority to M09 and replied in English to M07. This shows that few-shot prompting can improve response consistency but cannot guarantee completely correct results. 

## <u>STEP 7: SCORECARD AND REFLECTION</u> 

### **<mark>A. Comparison Scorecard</mark>** 

The outputs from both experiments are compared with the correct answer key prepared in Step 3. 

|**What to Check**|**Zero-shot**|**Few-shot**|
|---|---|---|
|Correct category (out of 12)|12/12|12/12|
|Correct priority (out of 12)|11/12|11/12|
|Reply follows ChillarPay tone (out of 12)|11/12|11/12|
|Table format followed (out of 12)|12/12|12/12|



### **<mark>B. Four Refection Questions</mark> l** 

### **1. Where was zero-shot good enough, and why?** 

Zero-shot prompting was good enough for summarising customer messages because summarisation is a common task. AI understood the main problem in each message without requiring any examples. 

### **2. Which messages did few-shot fix? Give the message IDs.** 

Few-shot prompting did not completely fix any incorrect category or priority in this experiment. However, it improved the consistency of replies for messages such as M01, M07 and M08 by demonstrating the expected response style. 

### **3. Did the Hinglish and tricky messages improve with examples?** 

The Hinglish fraud messages M08 and M12 received appropriate Hinglish replies. However, M07 still received an English reply. The unclear message M09 also remained incorrectly classified as Medium priority. Therefore, examples improved consistency but did not solve every problem. 

### **4. As ChillarPay's Business Analyst, which prompt would you recommend for daily support, and why?** 

I would recommend few-shot prompting for daily customer support because examples help AI understand company-specific rules, categories and response styles. However, AI-generated replies should be checked by human employees, especially for urgent fraud complaints and unclear customer messages. 

### <mark>C. Conclusion</mark> 

This assessment helped me understand the difference between **zero-shot** and **few-shot** prompting. **Zero-shot prompting** is useful for simple tasks such as summarising messages. **Few-shot prompting** is more useful when AI needs to follow specific business rules and response styles. 

I learned that adding examples can improve AI output, but it does not guarantee complete accuracy. Human verification is still important before using AI in real business operations. 


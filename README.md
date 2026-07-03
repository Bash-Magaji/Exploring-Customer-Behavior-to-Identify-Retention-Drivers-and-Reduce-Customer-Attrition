**Exploring Customer Behavior to Identify Retention Drivers and Reduce Customer Attrition**

<img width="749" height="1238" alt="Glo Customer Churn Analysis Dashboard" src="https://github.com/user-attachments/assets/c152ab9d-cbb0-4d35-9374-feb4f1db64d9" />

**1. Introduction**

Customer retention remains a critical challenge in the telecommunications industry, where intense competition and evolving customer expectations often lead to high rates of customer attrition. Understanding the factors that influence customer churn is essential for organizations seeking to maintain a stable customer base, improve service delivery, and maximize long-term profitability.
This analysis examines customer subscription patterns and the key factors associated with churn within a telecommunications company. The dataset provides insights into various customer characteristics and service-related attributes, including contract type, payment method, internet service, online security, technical support, customer tenure, monthly charges, total charges, and support call interactions.
The analysis reveals a compelling story about customer attrition, particularly among subscribers utilizing services such as internet connectivity, online security, and technical support. It also highlights how contract arrangements, billing preferences, service tenure, and customer support experiences influence retention outcomes. By exploring the relationships between these variables and customer churn behavior, the study aims to identify the primary drivers of retention and uncover opportunities for reducing customer loss.
The insights generated from this analysis can help telecommunication service providers develop targeted retention strategies, improve customer satisfaction, enhance service offerings, and ultimately reduce churn while fostering long-term customer loyalty.

 
**2. Story of Data**

**Data Source:** This dataset is a synthetic customer churn dataset designed to simulate real-world telecom customer behavior. It is generated using business-driven rules based on customer tenure, billing amount, contract type, service usage, and support interactions. Controlled randomness and noise are added to avoid perfect patterns and make the dataset suitable for realistic machine learning classification tasks. The dataset is ideal for beginners to practice exploratory data analysis, feature engineering, and customer churn prediction using machine learning models. It is obtained from kaggle.com

**Data Structure:** The dataset is organized in a tabular format consisting of rows and columns, where each row represents an individual customer and each column represents a specific customer attribute or service characteristic. Key features included in the dataset are Customer ID, Contract Type, Payment Method, Internet Service, Technical Support, Online Security, Churn Status, Customer Tenure, Monthly Charges, Total Charges, and Support Calls. These variables provide valuable insights into customer demographics, service usage patterns, billing information, customer support interactions, and subscription behavior, enabling a comprehensive analysis of the factors influencing customer retention and attrition within the telecommunications industry.

**Story Data is Telling:** The dataset tells a compelling story about customer attrition within the telecommunications industry, revealing patterns in subscription cancellations across key service offerings such as Internet Service, Online Security, Technical Support, and Customer Support Interactions. The analysis highlights how customers' decisions to remain with or leave the company are influenced by various factors, including the type of services they subscribe to, the frequency of support calls, and their overall experience with the provider. Additionally, the dataset emphasizes the role of contract type, customer tenure, and payment method in shaping customer retention outcomes. By examining these factors alongside churn behavior, the analysis provides valuable insights into the underlying drivers of customer attrition and identifies opportunities for improving customer satisfaction, strengthening loyalty, and reducing churn rates.

**3. Data Splitting and Preprocessing**

**Data Cleaning:** To ensure a smooth and reliable analysis process, the dataset was first validated in Microsoft Excel to identify any missing values, empty rows, or duplicate records. The verification process confirmed that the dataset was clean and requiring no additional cleansing. After completing the validation stage, the dataset was imported into the Power BI environment, where further data transformation, modeling, and analysis were performed to generate insights into customer churn and retention patterns.

**Data Transformation:** During the transformation phase, a calculated column named Loyalty was created to categorize customer tenure into yearly segments, providing a clearer understanding of customer loyalty and retention patterns over time. Additionally, several measures were developed, including Churn Count, Churn Rate, Total Churn Revenue, and other key performance indicators, to facilitate the calculation of critical metrics and support deeper analysis. These transformations enabled a more comprehensive evaluation of customer behavior, churn trends, and the factors influencing customer retention within the telecommunications business.

**Calculated Column**

Loyalty = SWITCH(TRUE(),'customer_churn_dataset'[tenure]<=12,"<1 year",'customer_churn_dataset'[tenure]<=24,"< 2 years",'customer_churn_dataset'[tenure]<=36,"< 3 years",'customer_churn_dataset'[tenure]<=48,"< 4 years", 'customer_churn_dataset'[tenure]<=60,"< 5 years",'customer_churn_dataset'[tenure]<=72,"< 6 years")

**Measures**

churn count = CALCULATE(COUNT('customer_churn_dataset'[churn]), ALLSELECTED('customer_churn_dataset'[churn]),'customer_churn_dataset'[churn] = "Yes")

Churn Rate % = DIVIDE(CALCULATE(COUNT('customer_churn_dataset'[churn]), 'customer_churn_dataset'[churn] = "yes" ), COUNT('customer_churn_dataset'[churn]), 0)

Online security in % = DIVIDE(CALCULATE(COUNT(customer_churn_dataset[online_security]), 'customer_churn_dataset'[online_security] ="Yes", 'customer_churn_dataset'[online_security]="Yes"),CALCULATE(COUNT(customer_churn_dataset[online_security]),'customer_churn_dataset'[online_security]="Yes"),0)

Tech Support in % = DIVIDE(CALCULATE(COUNT(customer_churn_dataset[tech_support]), 'customer_churn_dataset'[tech_support] ="Yes", 'customer_churn_dataset'[tech_support]="Yes"),CALCULATE(COUNT(customer_churn_dataset[tech_support]),'customer_churn_dataset'[tech_support]="Yes"),0)

Total Churn = COUNT(customer_churn_dataset[churn])


**Data Splitting:** To allowed for a more focused analysis and offered clearer insights into a distinctive aspect of the dataset is divided into two main categories.

**A. Category One — Independent value**

Contract 

Payment Method 

Internet Service 

Tech Support 

Online Security 

Churn

**B. Category Two — Dependent value**

Tenure

Monthly Charge

Total Charge

Support Call

**Industry Context:** The dataset and analysis relate to Telecommunications Industry and Tech Hubs. 

**Stakeholders:** The stakeholders of this project include the Chief Executives Officers, Marketing/Retention teams, Customer Support Managers, and Data Analysts team.

**Value to the Industry:** Success in the telecom industry means delivering reliable, high-quality connectivity while retaining customers, minimizing churn, and achieving sustainable, profitable growth in a competitive market.

**4. Potential-Analysis**

The main areas identified for potential analysis during the pre-analysis phase are outlined below.

•	Contract by Tenure

•	Contract by Monthly Charge

•	Contract by Total Charge

•	Contract by Support Calls

•	Payment Method by Tenure 

•	Payment method by Monthly Charge

•	Payment Method by Total Charge

•	Payment Method by Support Calls

•	Internet by Tenure

•	Internet Service by Monthly Charge

•	Internet Service by Total Charge

•	Internet Service by Support Calls 

•	Tech Support by Tenure

•	Tech Support by Monthly Charge

•	Tech Support by Total Charge

•	Tech Support by Support Calls

•	Online Security by Tenure 

•	Online Security by Monthly Charge

•	Online Security by Total Charge

•	Online Security by Support Calls

•	Churn by Tenure

•	Churn by Monthly Charge

•	Churn by Total Charge

•	Churn by Support Calls

**Initial Insights**

•	Finetune contract by tenure to determine whether higher-paying customers prefer longer-term contracts

•	Analyze Contract by Support Calls to show whether Month-to-month customers may make more support calls before churning 

•	Investigate Payment Method by Tenure to determine which payment methods are associated with longer retention

•	Finetune Payment Method by Total Charge to determine which payment types are most critical to retain

•	Investigate Payment Method by Support Calls to determine whether some payment groups experience more technical or billing issues

•	Internet by Tenure to understand the average retention per internet service type (Fibre, DSL, None)

•	Finetune Internet Service by Support Calls to determine which service types generating more support demand

•	Investigate Tech Support by Tenure to determine whether tech support subscriptions correlate with longer retention

•	Investigate Tech Support by Total Charge to determine which customer segment generates most revenue with tech support

•	Finetune Tech Support by Support Calls to determine frequency of support calls among tech support subscribers

•	Analyze Online Security by Support Calls to determine number of support calls among security subscribers

•	Finetune Churn by Tenure to determine Critical periods for early churn (e.g., 1–2 years)

•	Investigate Churn by Monthly Charge to determine whether high-paying customers are more or less likely to churn

•	Investigate churn by Support Calls to determine whether frequent support calls correlate with higher churn

**5. In-Analysis**

**•	Analysis -** Support Calls by Customer

**Observations**

A small number of customers recorded very high support interactions, with 3 customers making 8 support calls each, followed by 15 customers with 7 calls and 76 customers with 6 calls each. Moderate support usage was observed among 330 customers who made 5 calls, 901 who made 4 calls, and 2,580 who made 3 calls. The majority of customers had low support interaction, with 5,025 making 2 calls, 6,622 making 1 call, while 4,448 customers did not contact support at all.

**Insight**

The distribution shows that while most customers require minimal support, a small but significant group repeatedly contacts support, which may indicate unresolved technical issues or service dissatisfaction. These high frequency callers represent a critical churn risk segment that would benefit from proactive technical intervention and service quality improvements.

**•	Analysis -** Customer by Tenure

**Observations**

The highest proportion of customers (17.37%) have a tenure of two years, followed closely by five-year (17.01%) and six-year (16.49%) tenures. Customers with four-year and three-year tenures account for 16.45% and 16.36% respectively, while one-year tenure represents the smallest share at 16.33%.

**Insight**

The relatively even distribution of customers across tenure groups suggests stable retention over time, but the slightly lower proportion of one-year customers indicates higher vulnerability to early churn, highlighting the need for targeted retention strategies during the initial contract period.

**•	Analysis -** Payment Method by Total charge

**Observations**

Cash payments generate the highest total revenue, exceeding $12.9 million, with debit card payments closely following at over $12.7 million. Credit card and UPI payments each contribute slightly more than $12.6 million in total revenue.

**Insight:**

The close revenue gap across payment methods indicates diversified and stable payment behavior among customers. However, the marginal lead of cash and debit payments suggests these channels may offer stronger reliability and could be prioritized for retention incentives and payment optimization strategies.

**•	Analysis -** Contract by Count of Customer

**Observations**

Month-to-month contracts have the largest customer base, with over 12,000 subscribers, followed by one-year contracts at more than 5,000 customers, while two-year contracts account for just over 3,000 customers.

**Insight**

The strong dominance of month-to-month contracts indicates customer preference for flexibility but also signals a higher potential churn risk, suggesting that incentivizing longer-term contracts could improve retention and revenue stability.

**•	Analysis -** Internet Service by Count of Customer

**Observations**

More than 50% of customers subscribe to fibre-optic services, reflecting its superior speed, reliability, and symmetrical performance. This is followed by DSL users at approximately 40%, while about 10% of customers do not use any internet service.

**Insight**

The strong adoption of fibre-optic services highlights growing demand for high-performance connectivity, while the substantial DSL segment suggests an opportunity for targeted upgrades to fibre, which could enhance customer satisfaction and reduce churn.

**•	Analysis -** Online Security by Count of Customer

**Observations**

Only 40% of customers subscribe to online security services, while the remaining 60% do not have any online security add-on.

**Insight**

The low adoption of online security suggests an underutilized value-added service and a potential upselling opportunity; increasing awareness or bundling security with core services could enhance customer protection, improve perceived value, and strengthen customer retention.

**•	Analysis -** Tech Support by Count of Customer

**Observations**

35% of customers have an active tech support subscription, while 65% do not subscribe to tech support services.

**Insight**

The low uptake of tech support may expose a large portion of customers to unresolved technical issues, potentially increasing dissatisfaction and churn. Promoting bundled or affordable tech support options could improve service experience and retention.

**6. Post-Analysis and Insights**

•	Among churned customers, a small group showed very high engagement with support services, with 3 customers making 8 support calls each, 9 customers making 7 calls, and 44 customers making 6 calls. A larger proportion recorded moderate interaction, including 200 customers with 5 calls, 514 with 4 calls, and 1,505 with 3 calls. Meanwhile, 1,414 customers made 2 calls, 1,886 made one call each, and 1,263 customers churned without contacting support at all.
This highlight gaps in unresolved issues or recurring service issues and customer engagement prior to churn.

•	The highest levels of customer churn occur within the first one to two years, accounting for 22.10% and 16.45% respectively indicates that customers are most vulnerable to churn during the early stages of their subscription. Churn gradually declines for longer-tenured customers, with five-year tenure accounting for 15.78%, while six-year tenure records the lowest churn at 14.80%.

•	Churn related revenue is evenly distributed at approximately $4.6 million across UPI, credit card, and debit card payment methods, while cash payments record the highest churn related revenue at about $4.7 million, indicating weaker customer commitment to automated billing.

•	Month-to-month contracts experience the highest customer churn, accounting for 75.36% of all churned customers. This is followed by one-year contracts at 15.26%, while two-year contracts record the lowest churn at 9.38%. The dominance of churn among month-to-month customers highlights the strong link between contract flexibility and customer attrition. Longer-term contracts appear to enhance customer commitment and stability

•	Among customers who churned, 50% were subscribed to fibre-optic services, approximately 40% were DSL users, and about 10% had no internet service subscription.
The high proportion of churn among fibre-optic users suggests that churn may not only be driven by service type but other factors such as pricing, service expectations, or support quality. 

•	40% of customers churn subscribe to online security services, while the remaining 60% do not have any online security.
The higher share of churn among customers without online security suggests that the absence of value-added services may reduce customer attachment to the provider.
Customers with online security appear slightly more retained, indicating that bundled services can enhance perceived value and strengthen customer retention.

•	Among churned customers, 79% did not subscribe to any tech support services, while only 21% had access to tech support.
The predominance of churn among customers without tech support suggests that limited access to technical assistance may contribute to unresolved issues and customer frustration. Tech support services appear to play a protective role in customer retention.

•	Approximately 6,843 customers churned, representing a churn rate of 34.2% of the total customer base. This level of churn results in an estimated monthly revenue loss of over $546,000 and a cumulative total revenue loss of about $18.59 million. This translates directly into substantial revenue leakage, indicating that customer attrition poses a significant financial risk to the business.

**7. Post Analysis Recommendations**

•	Service providers may introduce early warning triggers for customers with multiple support calls to ensure faster resolution and escalation. At the same time, usage monitoring should be used to identify and engage silent customers before they churn, helping to improve retention across board.

•	To reduce early-stage churn, providers should offer personalized incentives or discounts during the first one to two years to encourage longer tenure and strengthen retention.
Proactively monitor customer satisfaction, and provide responsive support to quickly resolve issues.

•	Telecom providers should promote digital and automated payment options such as debit cards, UPI, or auto-pay to reduce churn associated with cash payments by offering incentives, discounts, ultimately lower churn-related revenue loss.

•	Service provider should actively encourage month-to-month customers to subcribe to longer-term contracts by offering incentives such as discounted yearly rates and bundled services, combined with proactive engagement and personalized retention offers, this can help reduce churn and improve long-term customer stability.

•	A more robust focus should be on service quality assurance and proactive support for fibre-optic customers, including faster fault resolution and performance monitoring.  this can help align customer expectations with service delivery and reduce churn across high value segments.

•	Providers should promote bundled packages that include online security, especially for customers at risk, and raise awareness of its benefits. Offering free trials or discounted security add-ons could strengthen customer engagement, increase service stickiness, and help reduce churn.

•	Providers should encourage greater adoption of tech support through bundled offerings, free introductory support periods, or targeted promotions for high-risk customers. 

•	Prioritize data driven churn prevention strategies, focusing on high-risk segments such as early tenure and month-to-month customers. Investing in proactive retention programs, personalized offers, and improved service support could significantly reduce churn and recover a large portion of the lost revenue.


**8.	Conclusion**

The analysis reveals that customer churn is a major challenge for the telecommunications company, with 6,843 customers leaving the service, representing a churn rate of 34.2% and resulting in an estimated monthly revenue loss of over $546,000 and a cumulative revenue loss of approximately $18.59 million. The findings show that customers are most vulnerable to churn during their first two years of subscription, highlighting the importance of effective onboarding and early customer engagement strategies. Month-to-month contract holders account for the majority of churned customers, indicating that contract flexibility is strongly associated with customer attrition, while longer-term contracts promote greater customer loyalty and retention.
The analysis also reveals that customers without value-added services such as online security and technical support are more likely to churn, suggesting that these services enhance perceived value and strengthen customer commitment. Additionally, the high volume of support calls among many churned customers points to unresolved issues and service-related dissatisfaction prior to cancellation. Fibre-optic subscribers represent the largest share of churned customers, indicating potential concerns regarding service quality, pricing, or customer expectations. Overall, the results demonstrate that customer attrition is influenced by a combination of contract type, tenure, support experience, service adoption, and billing behavior, emphasizing the need for targeted retention initiatives focused on improving customer experience, encouraging long-term subscriptions, enhancing support services, and proactively addressing customer concerns before they lead to churn.

**9. 	References**

Kaggle.com

# 3.1 - Understand the Industry
The whole process when a payment is made, also known as credit card transaction flow or authorization flow will involve the following agents, steps or processes: 

- Customer (cardholder);
- Merchant;
- Checkout + Point of Sale terminal (POS);
- Acquirer;
- Payment Schemes:
- Issuer (for credit card account validation);

Acquirer has the function of settling the financial transactions carried out through the credit and/or debit card. They communicate directly with the card brands/flags and the issuing banks.

When the purchase is approved between the card association and the financial institution, the acquirer receives the money from the card issuer and passes it on to the merchant.

In the case of sub acquirers, institutions such as "PagSeguro", Paypal, among others, are responsible for intermediating payments between all parties involved, such as acquirers, merchants and customers. 
This service is directed at data security with protection against fraud, encompassing all stages of the process, including the gateways.

Therefore, the payment gateways have the role of processing the information at the moment the purchase is finalised at the checkout. In other words to effect the purchase.

The KYC (Know Your Customes) is the process of analysis of customer data that is consistent with the movements and origins of their financial resources, verifying the authenticity of the information and data validation. 

For institutions to know their customers in depth, it is necessary to establish which data will be collected and stored. For example, information on income, assets and investments. This way, the bank can point out suspicious transactions. 

It is a security measure for institutions and is part of the compliance policies and programs to avoid financial losses, fraud prevention and possible scams, judicial convictions and damage to the image and fight the promotion of illicit activities such as money laundering and corruption.

# 3.2 - Get your hands dirty
## Process

### 1: 
- Firstly I selected all data from the table in order to analyze and present few conclusions;

- I noticed few "Null" values which I changed into "0" in order to prevent any malfunction during any process;

- It is possible to observe that the data present during the day a quadratic function line with positive delta, in other words, they start the day selling a certain number of POS that ends up going down in the following hours, but that soon after increases exponentially its sales curve throughout the day. It is worth mentioning that in the last hour of service (at 4pm) there is a significant drop in sales;

- Another possible observation is that it is more accurate to compare today's data with the same day from last week and not with yesterday's, as we must take into account the seasonality of the days. Use the rest of yesterday's data and the other averages to create comparative metrics.

### 2: 
- After evaluating the data in SQL, I connected the file with Python to plot the graph so I could get more insights. In this one I ended up running the same modification of NaN data to 0;

- After having the graphic visualisation, it was possible to notice some situations known as outliers: 

| | when | time | what_happened | 
| ------ | ------ | ------ | ------ |
1 | today | 06h | increase of 242% of avg_month sales|
2 | today | 13h | decrease of 27% of avg_month sales|
3 | yesterday | 13h | increase of 16% of avg_month sales|
4 | same_day_last_week | 15h | increase of 16% of avg_month sales|

- It is possible to notice changes in sales behaviour both for better and for worse. This can be due to the day of the week as well as events or special dates (changes in competitors' prices, strikes etc). These are the factors that we should study, analyse and try to take advantage of in order to forecast and profit as best as possible.


# 3.3 - Solve the problem
## Process

*to maintain a standard, I used upper and lower limits in all comparative cases, even though I knew that for "approved" cases there should only be lower limits and for cases like "denied, reversed and failed" only upper limits

### 1: 

After having all the tables assembled by SQL queries, I made the necessary adjustments (NaN values, Integer type, among others) and organized the information in the following way to create the alert:

- I grouped the data (using .rolling from the last 15 minutes) to create an average line from which I would use as a parameter to compare the data and create the necessary alerts;

- To identify unusual cases (outliers), I gave whoever was using the query the freedom to filter 3 types of data: upper limit, lower limit and starting time. And for each of these filters, I used widgets resources for better interactivity and control of the data for analysis;

- With all these resources, I used plot functions to transform my data into graphs and have visibility of all the details (average line, upper and lower limit), as well as an alert table that will inform the user how many cases were outside the established standard.

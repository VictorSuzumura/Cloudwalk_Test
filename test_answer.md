**Name:** Victor Gabriel Suzumura Cintra <br>
**Cloudwalk - Risk Analyst – Test**

# Understand the Industry

### **Explain the money flow and the information flow in the acquirer market and the role of the main players.**

The acquirer market revolves around three mains players, which are the acquirers themselves, the credit card brands and the issuing banks. It’s also important to mention the presence of customers and merchants, the people who will use the payment system. There are also the sub-acquirers and the payment gateways, which will be elucidated in the following answer. 

The acquirers are companies that process payments, allowing merchants to accept different types of payment methods. After processing the payment data of a purchase, they communicate with the credit card brands and issuing banks to validate the information, so they can complete the transaction.

Credit card brands are responsible for regulating the payment market, defining rules for credits cards, for example. They define how the acquirers must process the purchases. Those brands will receive information from the acquirers and check if they are valid. If so, then they will contact the issuing banks to confirm if the buyer has enough resources to complete the transaction.

Finally, Issuing Banks are the financial institutions responsible for the payment method (a credit card for example). They will check if the buyer has enough funds to complete the purchase and will allow or deny the transaction. Their answer is then sent back through the chain, and the acquirer will be able to allow or cancel the operation. If the purchase is confirmed, then the money goes from the Issuing Bank account to the credit card company and then to the acquirer, who will be responsible to transfer those resources to the merchant.

### **Explain the difference between acquirer, sub-acquirer and payment gateway and how the flow explained in question 1 changes for these players.**

Sub-acquirers are companies that specialize in the merchant end of the system, for whom they will provide services like those of an acquirer, but with relative ease when compared to them, allowing smaller businesses to join the payment system. When used, they send payment data to acquirers, starting the process described in the previous answer. In the same way of an acquirer, they will receive the payment and then transfer it to the merchant. 
Gateways are used in online payments. Like sub-acquirers, they need to contact acquirers to send data to them. Their main function is to collect payment information and then transfer it to the acquirer, which will validate the transaction. Their main advantage resides in the fact that the transaction amount is directly transferred to the merchant.

There are also some differences in what they offer and how much they charge. A sub-acquirer may provide fraud detection and risk management services, which are not present in gateways. As one could imagine, this could increase its costs when compared to a gateway. Nevertheless, choosing to use a gateway instead of a sub-acquirer may demand other services to secure transactions in e-commerce, increasing the cost for the merchant. 

### **Explain what chargebacks are, how they differ from cancellations and what is their connection with fraud in the acquiring world.**

Chargebacks happen when a cardholder asks its issuing bank to reverse a purchase. They are mainly used when the cardholder doesn’t recognize a transaction made with its card but can happen when there’s a problem in the transaction that can’t be solved in a friendly way. While it protects the customer by avoiding frauds like credit card cloning, it can be used in ways that may be harmful to merchants, by simply canceling normal transactions and making the merchant take all the loss. 

Cancellations differ from chargebacks because the former is a friendly way to solve a problem between the merchant and the customer, avoiding the action of third parties and generally applying rules that will reduce the effects of the cancellation to the merchant revenue. Chargebacks, on the other hand, can be very harmful and will demand the action of the issuing bank to force the reversal of the payment.

# Get your hands dirty

### Analyze the data provided and present your conclusions (consider that all transactions are made using a mobile device).

At first, I analyzed the data to get basic insight. Noticing the chargeback flag and considering that it could indicate fraudulent transactions, I correlated some of the dataset variables to this information.  The following conclusions have been extracted in this process:

- Transactions that result in chargebacks occur mostly during the night period.
- Considering the transactions that were preceded by another purchase of the same client, 53% had chargebacks.
- 37% of the chargeback cases were of clients with previous chargebacks.

While the analysis above is useful, it is not specific to the dataset: some payment systems apply time restrictions to transactions, and historic data is frequently used in score models. Focusing on the dataset samples, some detailed information was observed:

- There are clients with multiple cards with high chargebacks amounts. This could indicate the malicious intent of the customer, making chargebacks purposely from different virtual cards after a card is blocked. It also could indicate that someone got hold of the user’s bank account, making multiple cards to avoid security measures. 

<div align="center">

|      User    |     Number   of cards used    |     Chargeback   Amount    |     Regular   amount    |     Chargeback   (%)    |
|:------------:|:-----------------------------:|:--------------------------:|:-----------------------:|:-----------------------:|
|     11750    |               31              |          14.899,93         |         2.916,33        |            84%          |
|     91637    |               22              |          15.352,11         |         1.983,40        |            89%          |
|     79054    |               15              |          30.360,31         |         5.137,62        |            86%          |
|     96025    |               10              |          30.149,51         |           50,71         |           100%          |
|     78262    |               10              |          35.198,34         |         3.996,79        |            90%          |
|      7695    |                7              |           2.447,52         |         1.806,67        |            58%          |
|     67519    |                6              |          11.576,05         |          106,39         |            99%          |
  
</div>

-	Some clients with considerable chargeback amounts use more than one mobile device. While someone could have more than one smartphone, it’s somewhat odd that all of them are used to make purchases.  

<div align="center">
  
|      User    |     Number of devices   used    |     Chargeback Amount    |     Regular Amount    |     Chargeback (%)    |
|:------------:|:-------------------------------:|:------------------------:|:---------------------:|:---------------------:|
|     11750    |                 4               |         14.899,93        |        2.916,33       |           84%         |
|     99396    |                 3               |         10.059,33        |            0          |          100%         |
|     90182    |                 2               |          3.782,17        |          20,25        |           99%         |
|     92034    |                 2               |          3.876,08        |         213,31        |           95%         |
|     83258    |                 2               |          3.204,00        |            0          |          100%         |
  
</div>

- In both analyses, user 11750 seems to have malicious intent and should be investigated further. 

### In addition to the spreadsheet data, what other data would you look at to try to find patterns of possible frauds?

-	Geopositioning: if the purchase is done from a different location than the client’s usual area, it could indicate fraud.
-	Card vulnerability: there are pastebins of cybercriminals that list different card numbers and transaction information. If a card has been on a list like this, it should be handled with caution and the user must be notified.
-	User and merchant score: using models to calculate a score for clients is standard practice in risk management.
-	Merchant average ticket: if a purchase deviates from the standard value of a merchant’s transactions, it should be investigated further. 
-	Merchant segment average ticket: this information could be used alongside the merchant average to create a more precise analysis. 
-	User income: if a transaction represents a significant part of the user income, it could indicate that someone else got hold of the client card. 


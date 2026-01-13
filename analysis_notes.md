**What I’ve Got On My Hands**

Column - What it means in product terms
Invoice - A completed user action (one purchase session)
StockCode - Item-level interaction
Description - Product metadata (mostly ignorable)
Quantity - Intensity of engagement (and returns if negative)
InvoiceDate - Event timestamp (this is the backbone)
Price - Value generated
Customer ID - User identity

So this is not just a Sales dataset, it's a User event data where the value section is purchase.

Going through the data I can ascertain, to an extent that:
1. Product is an online retail platform
2. Users are the registered customers identified using the Customer ID
3. Core value action is completing a purchase. That's seen using the invoice
4. Activation point is the user's first successful purchase
5. Retention is the repeat purchases over time
6. Business goal is to increase the number of users who return repeatedly after their first purchase.

So this analysis is supposed to answer these (for now):

- how many users return after their first purchase?
- how quickly do they repeat their actions
- where is the largest drop-off in repeat usage.
...it will probably increase or change in one way or the other sha.

THE METRICS
The FOCUS METRIC is:
- the percentage of the activated users that make an extra purchase within 30 days after their first purchase.

I think this clearly tells us who is contributing to our monthly income, and how we can think from there to increase them based on the info we gather.

We can't look at daily or weekly cos it's too short a time to measure repeat purchasers. People can interact witht he website everyday but won't buy necessarily everyday unless they are resellers.


To properly explain this FOCUS we can look at these:
1. percentage of users make their first purchase
2. time between first and the second purchase. We can check the median.
3. how many purchases we usually have every 30 days. We will just use the average.

We can't use total revenue when our focus is more purchases since the revenue might be coming from only a few repeat users.
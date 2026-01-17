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


On this note, I'd try to answer a few questions using this anlysis:
1. how many users return after their first complete purchase?
because that directly influences my FOCUS METRIC

2. how quickly do they return for the second purchase?
cos this helps us more than checking volume

3. where do people dropoff the most after that first purchase?
so we can plug user leakages and bring more people to the finish line

4. what distinguishes the one-time buyers from the repeat buyers?
so I can see what way I can make the one-time guys more like the repeat buyers

5. and do those that return to make the second purchase keep returning?
so I can focus on the guys that are truly repeat buyers, not just accidental repeats. shey you get?

From the dataset we were abe to find that:  
- The dataset spans from December 2009 till December 2011. That's 2 years
- We have 5,942 unique customers across 5,305 unique products (based on stock code) and 53,628 unique invoices. That looks like a good thing for us.
- We have 229,950 negative quantities. Those should be returns or cancellations.
- There are entries, about 242,000 rows without Customer IDs. How did we know what customer that is. We will exclude them from the analysis.
- Some descriptions are missing. Not a big deal though.
- We have annexes in 43 countries.
- One invoice can have multiple items.




The dataset has a few issues with regards to the identification of customers and description of the products.
For the product description, we could say it is an oversight and use the stock code to trace it and find the product description and use that to fill in those missing sections but it kind of shows the point.
For the customer ID, we could use the invoice number to find the customer ID and use that to fill in the missing sections.

But solving it is not the issue, that it was missing is the issue. While percentage-wise it's a small amount, the absolute amount is on the high side. If it was a smaller dataset and these were missing it'd be disastrous.

It shows that their system needs automation on the data entry side especially since they have annexes in 43 countries.

THe sheer amount of products they have is large (5698) so they definitely need that automation.

That aside, the number of returns and cancellations are disturbing. It would be even worse if it was in only a few countries or if it was only a few products. We would have to remove that product from that annex or drop that product completely based on the respective suspicion.

Then again, I won't use everything here in the analysis.
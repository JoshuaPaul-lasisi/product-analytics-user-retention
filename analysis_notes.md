*What I’ve Got On My Hands*
Column - What it means in product terms
Invoice - A completed user action (one purchase session)
StockCode - Item-level interaction
Description - Product metadata (mostly ignorable)
Quantity - Intensity of engagement (and returns if negative)
InvoiceDate - Event timestamp (this is the backbone)
Price - Value generated
Customer ID - User identity

So this is not just a *Sales dataset*, it's a *User event data where the value section is purchase.*

Going through the data I can ascertain, to an extent that:
1. Product is an online retail platform
2. Users are the registered customers identified using the Customer ID
3. Core value action is completing a purchase. That's seen using the invoice
4. Activation point is the user's first successful purchase
5. Retention is the repeat purchases over time
6. Business goal is to increase the number of users who return repeatedly after their first purchase.
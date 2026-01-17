### Analysis Synthesis

#### What Surprised Me
- A relatively small number of users (~5900) generated a large volume of invoices (~53,000), indicating repeat purchasing behavior.
- The volume of negative quantities is significant, suggesting that returns and cancellations are a big part of user behavior, not just rare edge cases.
- A substantial portion of the transactions lack a Customer ID, limiting how much of the data can be used for user-level retention analysis.

#### What Looks Messy
- The customer identification has a large absolute number of rows missing.
- Returns and cancellations are recorded alongside the successful purchases without clear separation or tags.
- One purchase event (invoice) can span multiple product rows, creating a risk of overcounting user actions if not handles carefully.

#### What Excites Me
- The dataset spans over two years, making retention and cohort analysis meaningful rather than superficial.
- THe ratio of invoices to users suggests clear behavioral differences between one-time purchasers and repeat purchasers.
- The structure resembles real internal transactional event data used by e-commerce teams.

#### What Worries Me
- Returns need to be handles explicitly so retention metrics are not distorted.
- A small group of highly active users may dominate aggregate metrics, masking poor retention among the majority.
- Excluding rows with Customer ID is necessary but materially reduces the usable dataset and must be acknowldeged when interpreting results.
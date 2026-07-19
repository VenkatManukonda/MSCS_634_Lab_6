# MSCS_634_Lab_6

## Purpose

The goal of this lab was to compare Apriori and FP-Growth using the Online Retail dataset. Rather than focusing only on the number of patterns discovered, I wanted to understand how data preparation and support thresholds influenced the results, whether both algorithms identified the same product combinations, and how support, confidence, and lift could be used together to interpret customer purchasing behavior.

## What I Observed

The first thing that stood out was the concentration of transactions in the United Kingdom. After cleaning the dataset and removing administrative entries, the UK subset contained 17,903 transactions and 3,988 unique products. The White Hanging Heart T-Light Holder appeared most frequently in transactions, while the co-occurrence analysis showed that the Black Skull and Red Retrospot lunch bags were frequently purchased together.

Testing several support thresholds also produced a noticeable difference. At a 3% support threshold, Apriori identified 146 frequent itemsets. Reducing the threshold to 2% increased the result to 399 itemsets, while 1% produced 2,057. I selected 2% because it preserved a useful range of product combinations without producing an unnecessarily large output.

Apriori and FP-Growth both discovered the same 399 frequent itemsets and generated 75 rules using a 50% confidence threshold. Many of the strongest rules involved coordinated products, including Scandinavian Christmas decorations, Regency teacups, lunch boxes, and jumbo bags. The strongest association connected the Wooden Star Christmas Scandinavian and Wooden Heart Christmas Scandinavian products, with a lift of approximately 27.02.

## What I Learned

One of the main lessons from this lab was that the results of association rule mining depend heavily on how transactions are prepared. Canceled invoices, returns, duplicate records, and administrative charges could have created patterns that did not represent actual customer purchases. Cleaning these records before constructing the transaction basket made the final rules more meaningful.

I also learned that support, confidence, and lift describe different parts of a relationship. Support shows how often a combination appears across all transactions, while confidence measures how consistently the consequent appears when the antecedent is present. Lift adds important context by showing whether the relationship is stronger than expected given the products' individual popularity. Considering all three measures prevented a rule from appearing important based on confidence alone.

## Challenges and Decisions

The main challenge was balancing the number of discovered patterns with processing time. A low support threshold returned many itemsets, while a higher threshold removed potentially useful combinations. Testing three thresholds made it easier to justify 2% as a practical middle point.

Another challenge was controlling the size of the transaction matrix. Products appearing on fewer than 1% of invoices were excluded because they did not meet any of the tested support thresholds. I also removed administrative entries using exact descriptions rather than broad keywords, so that genuine products containing similar words were not accidentally removed.

Apriori completed the analysis in approximately 1.81 seconds, while FP-Growth required about 9.73 seconds. Although FP-Growth is often expected to be faster, Apriori performed better on this filtered basket because the selected support threshold limited the number of qualifying combinations. This reinforced that algorithm performance depends on the structure of the data and the conditions of the analysis.

Overall, this lab showed how association rule mining can move beyond identifying popular products and reveal which items are meaningfully connected within customer transactions. Both algorithms produced consistent results, but Apriori was the more efficient option for this particular analysis.

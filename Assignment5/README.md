# Assosciative rule mining

---

Assosciative rule mining is an unsupervised machine learning algorithm similar to Clustering and Dimensionality reduction. It is a descriptive method used to discover relationship hidden in large datasets. There are tghree types of assosciative rule mining techniques:


*   Apriori
*   ECLAT
*   FP-Growth

### Metrics

All the assosciative techniques are based on the following techniques#

*   **Support:**  Number of times a product or multiple products are purchased out of total transactions.
*   **Confidence:** Number of times a second product is pruchased after the purchase of the first product.
*   **Lift:** Ratio of support of two products being purchased together to the support of the two products purchased independently.

# Apriori algorithm

Apriori algorithm utilizes the support, confidence, and lift for all possible combinations of the products such that they satisfy a minimum threshold of support and confidence. This avoids generating way too many combinations and avoid computations.

On a broader view, the algorithm performs the following steps.


*   Find out the frequent combinations of items called as 'itemsets' such that it satisfy the minimum support threshold.
*   Generate assosciation from frequent itemsets rules considering the minimum confidence threshold.


# FP-Growth Algortihm

FP-Growth or Frequent Patterns Growth utilizes a special tree structure called as FP-Tree that stores the frequent patterns at one place. FP-Tree helps reduce the need for scanning data drastically. Hence it is faster than Apriori algorithm. However, FP-Growth algortihms are not suitable for larger datasets.

Similar to Apriori, FP-Growth genrate assosciation or rules in the following steps.

*   Find frequent combinations called as 'itemsets' that satisfy minimum support threshold. 
*   Generate rules from frequent itemsets utilizing FP-Tree.

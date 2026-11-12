# Customer Behaviour Analytics at Scale — PySpark
## Project explanation and interview preparation

### Project summary

This project uses Apache Spark to analyse e-commerce transaction and customer-survey data. It explores when people buy, which products and categories perform well, how purchasing differs by geography, and how customer value can be described using RFM segmentation. Market basket analysis looks for products that are frequently purchased together.

**60-second interview pitch**

“I used PySpark to analyse e-commerce purchase records alongside customer-survey and field data. After inspecting and cleaning the data, I engineered purchase and revenue features and carried out exploratory analysis across time, product and geography. I then used RFM segmentation to classify customers by recency, frequency and monetary value, and market basket analysis to identify products that were frequently purchased together. The objective was to turn transaction patterns into practical ideas for inventory planning, targeted marketing and customer retention.”

### Business problem

The project looks beyond total sales to understand purchase timing, product performance, geography, customer value, repeat purchasing and product combinations.

### Data understanding

The project documentation identifies three inputs: `amazon-purchases.csv`, `survey.csv` and `fields.csv`. The data is described as US Amazon purchase activity from 2018–2022. The source CSVs are not currently stored in the repository, so verify actual counts, field types, join keys and missingness from the original data before quoting detailed figures.

### Methodology

- Inspect the schema and grain of each table, then validate keys and data types.
- Check missing values, duplicates and invalid price/quantity combinations.
- Engineer revenue, purchase frequency, recency and monetary value where source fields support them.
- Explore purchase distributions by time, product, category and geography.
- Segment customers using RFM.
- Use market basket analysis to identify product combinations.
- Translate patterns into inventory, retention and cross-sell recommendations.

**RFM:** Recency is the time since the customer's last purchase; frequency is the number of purchases in the observation period; monetary value is the total spending. Document the observation date and scoring rules because they influence the segment definitions.

**Market basket measures:** support measures how common an item set is; confidence measures the frequency of B among baskets containing A; lift compares that conditional frequency with B's baseline frequency. Lift above 1 indicates positive association, not causation.

### Business interpretation

- Inventory can be planned around seasonal and category patterns.
- Retention campaigns can be tailored to RFM segments.
- Common product combinations can inform bundle or recommendation tests.
- Geographic differences can guide further market analysis.
- Suspected irregular transactions should be reviewed before being described as fraud.

### Interview questions and suggested answers

**1. Why use PySpark instead of Pandas?**  
Pandas is suitable for data that fits in local memory. PySpark distributes processing across partitions and nodes, which is useful for larger workloads. Spark adds setup and execution overhead, so it is not automatically preferable for every small dataset.

**2. What is a Spark DataFrame?**  
A distributed collection of data organised into named columns and a schema. Spark can optimise many DataFrame operations and execute them across partitions.

**3. What is lazy evaluation?**  
Spark records transformations as a logical plan and generally runs them when an action is triggered, such as count or write. This allows Spark to optimise the execution plan.

**4. What is the difference between a transformation and an action?**  
Transformations such as filter, select and groupBy define a new dataset. Actions such as count, show and write trigger computation or return a result.

**5. Explain RFM analysis.**  
RFM scores customers based on how recently they purchased, how frequently they buy and how much they spend. It offers interpretable customer segments for retention and marketing.

**6. Why does RFM need a reference date?**  
Recency is measured relative to an observation date. Defining that date makes the metric reproducible and ensures segments are comparable across runs.

**7. Explain support, confidence and lift.**  
Support measures the overall frequency of an item set; confidence measures the proportion of baskets containing B among baskets containing A; lift compares that conditional frequency with B's overall frequency.

**8. Does a high-lift product pair prove that one product causes another to sell?**  
No. It shows association. Seasonality, customer type, discounts and product placement can influence co-purchases. A controlled experiment is needed to test causality.

**9. How do you handle missing transaction values?**  
First understand why the value is missing and how the field is used. I would define field-specific handling rules, record how many rows are affected and compare outputs before and after cleaning. Missing values should not automatically become zero.

**10. What is data skew in Spark?**  
Data skew occurs when some partitions contain much more data than others, often because a few join keys are very frequent. It can cause a small number of tasks to dominate execution time. Broadcast joins, partitioning choices or salting may help depending on the case.

**11. Why avoid collect() on a large DataFrame?**  
It transfers all selected rows to the driver and can exhaust driver memory. I would aggregate or sample in Spark and collect only a small, bounded result.

**12. How would you validate RFM segments?**  
Inspect segment sizes and spending distributions, compare repeat-purchase and retention behaviour, check segment stability over time and confirm the groups lead to different actions.

### Limitations to be ready to discuss

- Raw source CSVs are not in the repository.
- Confirm customer identifiers, join keys and data grain before presenting detailed counts.
- Document the basket definition and RFM reference date.
- Treat product combinations as associations rather than causal evidence.
- Do not label transactions fraudulent without a validated fraud process.

### Resume bullet

Applied PySpark to e-commerce transaction data, performing data cleaning, exploratory analysis, RFM segmentation and market basket analysis to derive recommendations for retention, merchandising and inventory planning.

### Files

- [Analysis notebook](../Big+Data+Assignment+_+Customer+Behaviour+Analysis+_+Starter+Notebook1.ipynb)
- [Project report](../Big%20Data%20Assignment%20-%20Customer%20Behavior%20Analysis.pdf)
- [Monthly trend](../monthly_trend.png)
- [Yearly trend](../yearly_trend.png)
- [Purchase distribution](../purchase_distribution.png)

# Customer Behaviour Analytics at Scale — PySpark

A big-data analytics project exploring e-commerce transactions, customer value, product combinations and purchasing patterns using Apache Spark.

**Tools:** PySpark · Python · Pandas · NumPy · Matplotlib · Seaborn

## Business question

How can an e-commerce business use transaction and customer-survey data to understand buying behaviour, identify valuable customer segments and improve merchandising, inventory planning and retention?

## Data

The project describes US Amazon purchase records from 2018–2022 and related survey/field data:

- `amazon-purchases.csv` — transaction data.
- `survey.csv` — customer survey responses.
- `fields.csv` — field descriptions and attributes.

These source CSVs are not currently included in this repository. A local copy is required to reproduce the analysis end to end.

## Analysis

- Data inspection, cleaning and validation.
- Exploratory analysis of purchase timing, products, categories and geography.
- Feature engineering for revenue and purchase behaviour.
- **RFM segmentation** using recency, frequency and monetary value.
- **Market basket analysis** to identify product combinations.
- Business recommendations for inventory, retention and cross-selling.

## Business relevance

The analysis is intended to help align inventory with seasonal demand, target customer segments more thoughtfully and use product associations to inform cross-selling. Irregular transactions should be treated as review candidates, not labelled as fraud without a validated fraud definition.

## Repository contents

- `Big+Data+Assignment+_+Customer+Behaviour+Analysis+_+Starter+Notebook1.ipynb` — analysis notebook.
- `Big Data Assignment - Customer Behavior Analysis.pdf` — project report.
- `monthly_trend.png`, `yearly_trend.png`, `purchase_distribution.png` — supporting visuals.
- `docs/PROJECT_GUIDE_AND_INTERVIEW_QUESTIONS.md` — project explanation and interview preparation.

## Reproducibility

Set up a compatible Spark/PySpark environment and place the source CSV files in the paths expected by the notebook, or update those paths. The original CSVs are not stored in this repository.

## Interview preparation

See [Project explanation and interview questions](docs/PROJECT_GUIDE_AND_INTERVIEW_QUESTIONS.md).

## Author

**Eshwar Ramesh** · [GitHub](https://github.com/EshwarRamesh7) · [Portfolio](https://eshwarrameshportfolio.netlify.app) · [LinkedIn](https://www.linkedin.com/in/eshwar-ramesh-9a4652251)

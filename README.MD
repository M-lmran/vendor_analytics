# Vendor Performance Analytics & Tier Assignment System

A data analytics pipeline that evaluates vendor performance across multiple business dimensions, assigns performance tiers, identifies high- and low-performing suppliers, and generates reports to support procurement decisions.

## Overview

The Vendor Performance Analytics & Tier Assignment System combines purchase order data, vendor master data, statistical analysis, machine learning, and data visualization to provide a structured view of supplier performance.

The system evaluates vendors across six dimensions:

- **Quality:** Quality scores, rejection rates, and consistency.
- **Delivery:** On-time delivery, fulfillment rates, and delivery delays.
- **Price:** Price competitiveness and price stability.
- **Responsiveness:** Response times, communication, and query resolution.
- **Invoice Accuracy:** Invoice errors, payment-term compliance, and documentation completeness.
- **Sustainability:** Certifications, environmental performance, and compliance violations.

Vendor performance is summarized using a weighted composite score and a tier-assignment mechanism.

## Key Features

- **CSV Integration:** Upload vendor master and purchase order datasets.
- **Sample Data Generation:** Generate synthetic vendor and purchase order data when CSV data is unavailable.
- **Data Quality Assessment:** Inspect missing values, data types, duplicate records, numeric ranges, date consistency, and vendor references.
- **Data Enhancement:** Generate additional quality, delivery, responsiveness, invoice, and sustainability metrics.
- **Vendor Scoring Engine:** Calculate dimension-specific scores and weighted composite scores.
- **Tier Assignment:** Classify vendors into three performance tiers.
- **Vendor Ranking:** Rank vendors overall and within their categories.
- **Risk Assessment:** Calculate a risk score based on composite performance.
- **Data Visualization:** Generate charts for tier distribution, score distributions, category performance, geographical performance, and metric correlations.
- **Advanced Analytics:** Generate vendor radar charts, performance trends, and interactive Plotly visualizations.
- **Report Generation:** Export analytical results and generate executive summaries and text reports.

## Technology Stack

- Python
- Pandas and NumPy
- SciPy and Scikit-learn
- Matplotlib and Seaborn
- Plotly
- XGBoost
- SHAP
- Missingno
- Google Colab

## System Architecture

The pipeline follows these stages:

1. **Data Ingestion:** Load vendor master data and purchase order records.
2. **Data Quality Checks:** Inspect data completeness, consistency, and validity.
3. **Data Enhancement:** Add analytical metrics and merge datasets.
4. **Feature Engineering:** Derive performance indicators from purchasing and vendor data.
5. **Vendor Scoring:** Calculate quality, delivery, price, responsiveness, invoice, and sustainability scores.
6. **Tier Assignment:** Calculate composite scores, ranks, and risk scores.
7. **Advanced Analytics:** Generate visualizations, trends, and predictive analyses.
8. **Report Generation:** Export reports and summarize findings.

## Vendor Scoring Methodology

The system calculates a weighted composite score using the following default weights:

| Performance Dimension | Weight |
|---|---:|
| Quality | 25% |
| Delivery | 25% |
| Price | 20% |
| Responsiveness | 15% |
| Invoice Accuracy | 10% |
| Sustainability | 5% |
| **Total** | **100%** |

The composite score is calculated as:

`Composite Score = Σ (Dimension Score × Dimension Weight)`

### Vendor Performance Tiers

| Tier | Composite Score | Interpretation |
|---|---:|---|
| Tier 1 – Strategic | 85 and above | High-performing vendors |
| Tier 2 – Preferred | 70 to below 85 | Vendors with satisfactory performance and improvement opportunities |
| Tier 3 – Transactional | Below 70 | Vendors requiring closer monitoring and improvement |

The system also calculates overall rank, category rank, gap to the next tier, and risk score.

`Risk Score = 100 − Composite Score`

## Installation and Execution

The notebook is designed to run in Google Colab.

### 1. Open Google Colab

Visit [Google Colab](https://colab.research.google.com/) and upload or open the project notebook.

### 2. Install Dependencies

Run the notebook's package installation cell:

```bash
pip install pandas numpy scipy scikit-learn seaborn matplotlib plotly xgboost shap missingno
```

### 3. Upload Input Data

When prompted, upload the vendor master CSV and purchase order CSV files.

The pipeline expects vendor data containing fields such as supplier code, vendor name, category, location, and payment terms. Purchase order data includes fields such as purchase order number, supplier code, goods receipt date, ordered quantity, received quantity, rate, item value, moved value, and delivery status.

Ensure that the column names and date formats match the notebook's expectations.

### 4. Run the Notebook

Execute the cells sequentially, starting with data loading and continuing through data quality checks, data enhancement, scoring, visualization, predictive analytics, and report generation.

If the CSV upload flow is unavailable, the notebook includes fallback logic for generating sample data.

## Generated Outputs

The notebook is designed to generate:

- **Excel report:** `vendor_analysis_report_YYYYMMDD_HHMMSS.xlsx`
- **Text report:** `vendor_report_YYYYMMDD_HHMMSS.txt`
- **Visualizations:** Charts and dashboards displayed within the notebook.
- **Executive summary:** Key findings, vendor rankings, and performance insights.
- **Presentation summary:** Suggested presentation slides covering the analysis and strategic recommendations.

Generated filenames may include timestamps.

## Business Applications

This system can support procurement and supply chain teams by helping them:

- Identify strategic and preferred suppliers.
- Compare vendor performance across categories and locations.
- Detect quality, delivery, pricing, and invoice-related risks.
- Prioritize supplier improvement initiatives.
- Support data-driven procurement decisions.
- Establish a repeatable framework for vendor performance reviews.

## Important Notes and Limitations

- Some analytical dimensions are generated synthetically when corresponding real-world data is unavailable. These values should not be treated as verified supplier performance.
- Sample data is intended for demonstration and testing, not production decisions.
- Scoring thresholds and weights are configurable business assumptions and should be validated against organizational requirements.
- Predictive analytics results depend on the quality, quantity, and representativeness of the input data.
- The notebook should be validated and tested before being integrated into a production procurement system.

## Future Enhancements

- Integrate with ERP and procurement systems.
- Automate scheduled data ingestion and report generation.
- Replace simulated metrics with verified operational data.
- Add a web-based dashboard for interactive vendor monitoring.
- Introduce alerts for declining performance and high-risk suppliers.
- Store historical scores to track long-term supplier performance.

## Conclusion

The Vendor Performance Analytics & Tier Assignment System provides a structured framework for assessing vendor performance using data analytics, weighted scoring, visualizations, and predictive techniques. By combining multiple performance dimensions into a composite score, it helps procurement teams compare suppliers, identify risks, and prioritize improvement opportunities.


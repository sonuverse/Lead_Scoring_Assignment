# Lead Scoring Assignment — X Education

A machine-learning case study to identify leads with a higher likelihood of converting into customers, using exploratory data analysis and logistic regression.

## Project Overview

X Education receives leads through multiple channels, but not every lead becomes a paying customer. The purpose of this assignment is to analyze lead data, identify patterns associated with conversion, build a logistic-regression model, and translate predicted conversion probabilities into lead scores from 0 to 100. The scores can help the sales team prioritize follow-ups.

**Target variable:** `Converted`
- `1` — the lead converted
- `0` — the lead did not convert

## Business Objectives

- Understand the characteristics and behaviours associated with lead conversion.
- Explore conversion patterns across lead origin, lead source, occupation, website engagement, and activity.
- Prepare the dataset for predictive modelling.
- Build and evaluate a logistic-regression model.
- Generate lead scores based on predicted conversion probabilities.
- Recommend different lead-contact strategies depending on sales capacity and business targets.

## Repository Contents

The project files in this repository are intended to cover the analysis, modelling, written assignment answers, presentation, and source data.

| File | Purpose |
|---|---|
| `Lead_Scoring_Assignment_Python_SAKSHI_GHODESWAR.ipynb` | Main Jupyter notebook containing data understanding, cleaning, EDA, model building, evaluation, lead scoring, and recommendations. |
| `Leads.csv` | Lead-level source dataset used by the notebook. |
| `Leads Data Dictionary.xlsx` | Data dictionary describing the dataset fields. |
| `Lead_Scoring_Assignment_Report_SAKSHI_GHODESWAR.pdf` | Summary report describing the business problem, data preparation, EDA, modelling approach, evaluation, and recommendations. |
| `Lead_Scoring_Assignment_Subjective_SAKSHI_GHODESWAR.pdf` | Written responses to the assignment’s subjective questions. |
| `Lead_Scoring_Assignment_Presentation_SAKSHI_GHODESWAR.pdf` | Presentation deliverable exported as PDF. |

> Keep the filenames in the table aligned with the actual filenames in the repository. If you rename files during upload, update this table too.

## Dataset Description

The notebook and summary report describe the original dataset as **9,240 rows and 37 columns**. The target field is `Converted`. The notebook loads the source data with:

```python
leads = pd.read_csv("Leads.csv")
```

The CSV should be kept in the same directory as the notebook for this relative path to work. The Excel data dictionary is provided as a reference for interpreting the columns.

The report records an initial conversion rate of approximately **38.54%**. The notebook's EDA section describes 3,561 converted leads and 5,679 non-converted leads. These figures are reported from the submitted project materials.

## Tools and Libraries

- Python
- Jupyter Notebook
- Pandas and NumPy
- Matplotlib and Seaborn
- Scikit-learn
- Statsmodels

The notebook uses these tools for data preparation, visualization, feature selection, logistic regression, and model evaluation.

## Workflow

### 1. Data Understanding

- Load the lead dataset.
- Inspect its dimensions, columns, data types, descriptive statistics, and target distribution.
- Review missing-value percentages and identify the target variable.

### 2. Data Cleaning and Preparation

The notebook includes steps to:

- Treat the placeholder value `Select` as missing information.
- Review duplicate rows.
- Drop columns with high proportions of missing values.
- Remove identifier columns such as `Prospect ID` and `Lead Number`.
- Remove columns with very little variation.
- Impute remaining categorical missing values using the mode and numerical missing values using the median.
- Prepare categorical variables for modelling with dummy encoding.

### 3. Exploratory Data Analysis (EDA)

The notebook explores:

- The distribution of converted and non-converted leads.
- Conversion by lead origin.
- Conversion by lead source.
- Website time spent and conversion.
- Website visit behaviour.
- Current occupation.
- Last activity and last notable activity.
- `Do Not Email` status.
- Correlations among model variables.

### 4. Model Preparation and Training

- Create dummy variables for categorical features.
- Split the data into training and test sets using a 70:30 split.
- Scale selected numerical variables with `StandardScaler`.
- Use Recursive Feature Elimination (RFE) for feature selection.
- Fit logistic-regression models.
- Review p-values and Variance Inflation Factor (VIF) when refining the model.

### 5. Model Evaluation

The notebook evaluates model performance using classification metrics, a confusion matrix, ROC curve, and ROC-AUC. It also examines the classification cutoff rather than relying only on the default probability threshold.

The summary report records the following results for the selected model:

| Metric | Training data | Test data |
|---|---:|---:|
| Accuracy | 80.1% | 80.2% |
| Sensitivity | 83.8% | 83.7% |
| Specificity | 77.7% | 77.9% |
| ROC-AUC | 0.88 | 0.88 |

These values are transcribed from the submitted summary report and should be interpreted in the context of that report's chosen model and cutoff.

### 6. Lead Scoring

The model's predicted conversion probabilities are multiplied by 100 to create a lead score on a 0–100 scale. Higher scores indicate a higher model-estimated likelihood of conversion.

## Key Findings Reported in the Assignment

The submitted notebook and reports identify these patterns:

- Leads associated with **Lead Add Form** showed a high conversion rate in the EDA.
- **Working Professionals** were identified as a promising segment.
- **Welingak Website** was highlighted as a lead source associated with higher conversion likelihood.
- Time spent on the website was treated as a useful engagement signal.
- Last activity and last notable activity were explored as additional indicators of lead behaviour.

These are associations observed in the assignment data; they should not be interpreted as proof that any single attribute causes conversion.

## Business Recommendations

The assignment recommends adapting the classification cutoff to the business situation:

- **During an aggressive conversion period:** use a lower cutoff to identify more potential leads and prioritize sensitivity, accepting that more calls may be required.
- **After a quarterly target has been achieved:** use a higher cutoff to focus on leads with stronger predicted conversion likelihood and reduce unnecessary calls.
- Prioritize leads from the segments highlighted in the model, while continuing to monitor actual conversion outcomes.

The selected cutoff should be validated against real operational capacity, the cost of a sales call, and the relative cost of missing a potential customer.

## How to Run the Notebook

1. Clone or download this repository.
2. Keep `Leads.csv`, `Leads Data Dictionary.xlsx`, and the notebook in the same folder unless you update the paths.
3. Open the notebook in Jupyter Notebook or VS Code with the Python and Jupyter extensions installed.
4. Ensure the required libraries are installed.
5. Select the correct Python kernel.
6. Run the notebook from top to bottom.

Example installation command:

```bash
python -m pip install pandas numpy matplotlib seaborn scikit-learn statsmodels jupyter
```

The notebook's relative CSV path expects `Leads.csv` to be in the notebook's working directory.

## Limitations and Notes

- Model results depend on the dataset, preprocessing decisions, feature selection, train/test split, and classification cutoff.
- A higher or lower cutoff changes the balance between sensitivity and specificity; the appropriate choice depends on the business objective.
- The analysis describes patterns in historical data and does not guarantee that a lead will convert.
- Dataset files should only be shared publicly if their licence, source terms, and any applicable privacy requirements permit it.

## Suggested Repository Structure

```text
Lead_Scoring_Assignment/
├── README.md
├── Lead_Scoring_Assignment_Python_SAKSHI_GHODESWAR.ipynb
├── Leads.csv
├── Leads Data Dictionary.xlsx
├── Lead_Scoring_Assignment_Report_SAKSHI_GHODESWAR.pdf
├── Lead_Scoring_Assignment_Subjective_SAKSHI_GHODESWAR.pdf
└── Lead_Scoring_Assignment_Presentation_SAKSHI_GHODESWAR.pdf
```

## Project Summary

This assignment applies an end-to-end classification workflow to a lead-conversion business problem: understand and clean the data, explore conversion patterns, build and evaluate a logistic-regression model, convert probabilities into lead scores, and recommend sales-prioritization strategies.

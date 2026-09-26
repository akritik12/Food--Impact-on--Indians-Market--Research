# Consumer Food Preferences Analysis

![Orange](https://img.shields.io/badge/Orange-Data%20Mining-orange)
![PCA](https://img.shields.io/badge/Method-PCA-blue)
![EDA](https://img.shields.io/badge/EDA-Exploratory%20Analysis-green)
![Visualization](https://img.shields.io/badge/Data-Visualization-purple)

An end-to-end consumer analytics project that explores food preferences, dietary habits, and lifestyle patterns of **17,686 survey respondents** using **Orange Data Mining**. It combines exploratory data analysis, **Principal Component Analysis (PCA)**, and visual analytics to test which consumer behaviour patterns the data actually supports.

The whole analysis is built as a visual Orange workflow, so every step is reproducible without writing code.

---

## Why analyze consumer food preferences?

Food choices are shaped by lifestyle, health, region, and habits. Understanding these links helps businesses position products, segment customers, and target marketing.

Rather than only summarizing survey responses, this project uses PCA and visual analytics to check whether the data contains **real, usable patterns** before drawing business conclusions.

---

## TL;DR

* **Who the respondents are:** 54% vegetarian, 49% sedentary, and 47% in the obese BMI range, with diabetes the most reported condition (15%).
* **Diet and exercise are unrelated:** about half of every diet group is sedentary, so knowing someone's diet tells you nothing about how much they exercise.
* **Health conditions don't change exercise habits either:** about half of people in every disease group are sedentary.
* **Region doesn't predict cuisine:** each of the 7 cuisines makes up 13–15% of respondents in every region (χ² = 17.44, p = 0.829). For example, South Indian cuisine is no more common in the South than in the North.
* **PCA found no dominant patterns:** the first two components explain only **9.2%** of the variance, and even 20 components explain only about 69%.
* **Conclusion:** the variables appear to be **independent and randomly generated**. The dataset is useful for practising Orange workflows but should not be used for real business decisions.

---

## Dataset

| Detail | Value |
| --- | --- |
| Source | [Food Impact on Indians (Kaggle)](https://www.kaggle.com/datasets/harry5760/food-impact-on-indians) |
| File | `data/food_impact_india.csv` |
| Size | 17,686 rows × 16 columns, no duplicates |

| Category | Variables |
| --- | --- |
| Demographics | Age (18–69), Gender, Region (North, South, East, West, Central) |
| Diet Type | Vegetarian, Non-Vegetarian, Vegan |
| Food Preferences | Primary Cuisine (7 regional cuisines), Spice Level, Sugar Intake, Salt Intake |
| Eating Habits | Daily Calorie Intake (1,200–3,500), Food Frequency (1–6 meals/day) |
| Lifestyle | Exercise Level (Sedentary, Moderate, Active) |
| Health | BMI, Health Score (1–100), Health Impact, Common Diseases (Diabetes, Obesity, Hypertension, Cardiac Issues) |

`Common_Diseases` is blank for 60% of respondents. These rows were kept and read as "no disease reported," since removing them would discard most of the data.

---

## Method

The analysis was built entirely in Orange Data Mining as a visual workflow:

1. **Data preprocessing:** load the CSV and use **Select Columns** to ignore `Person_ID` and set `Health_Score` as the target.
2. **Exploratory data analysis:** use **Distributions** to examine each variable and split it by group.
3. **Principal Component Analysis:** use **PCA** (with normalized variables) to measure how much of the variation a few components can capture.
4. **Behavioural analysis:** use **Box Plot** and **Distributions** to compare exercise, BMI, and health across diet groups.
5. **Regional analysis:** compare cuisine preferences across the five regions.
6. **Insight generation:** turn the visual patterns into findings, and check whether they are strong enough to act on.

---

## Key Objectives

* Profile consumer food preferences and lifestyle habits
* Test whether PCA can reduce the data to a few meaningful dimensions
* Analyze the relationship between diet and exercise
* Compare regional cuisine preferences across India
* Show how Orange's visual workflow supports consumer analytics

---

## Results

| Analysis | Question | Finding |
| --- | --- | --- |
| Consumer Profile | Who are the respondents? | Mostly vegetarian (54%), sedentary (49%), and obese by BMI (47%) |
| PCA | Can a few components summarize the data? | No. PC1 and PC2 explain only 9.4% of the variance. |
| Diet vs Exercise | Do diet groups exercise differently? | No. Sedentary share is 49–51% in every diet group. |
| Regional Cuisine | Does region predict cuisine? | No. Every cuisine is 13–15% of every region. |

---

## Analysis Preview

### Orange Workflow

The full analysis was built with Orange's visual programming interface, covering preprocessing, exploratory analysis, PCA, and behavioural visualization.

![Orange Workflow](outputs/figures/workflow.png)

### Consumer Profile

| Attribute | Breakdown |
| --- | --- |
| Gender | Female 48.2% · Male 47.6% · Non-Binary 4.2% |
| Diet Type | Vegetarian 54.4% · Non-Vegetarian 40.6% · Vegan 4.9% |
| Spice Level | Medium 49.6% · High 25.5% · Low 24.9% |
| Exercise Level | Sedentary 49.5% · Moderate 30.3% · Active 20.2% |
| BMI | Normal 29.4% · Overweight 23.8% · Obese 46.8% |
| Reported Disease | None 60.2% · Diabetes 14.9% · Obesity 9.9% · Hypertension 9.8% · Cardiac 5.2% |

### Principal Component Analysis (PCA)

PCA was applied to all 14 features. Categorical variables were one-hot encoded, giving 41 columns, and all columns were normalized.

| Components | Variance Explained |
| --- | ---: |
| PC1 | 4.7% |
| PC1 + PC2 | 9.4% |
| Components needed for 50% | 14 |
| Components needed for 80% | 24 |

In a dataset with strong patterns, the first few components usually explain most of the variance and the curve rises steeply. Here, the variance is spread almost evenly across components and the curve rises slowly. This means there are **no dominant underlying patterns** for PCA to compress.

![PCA Explained Variance](outputs/figures/pca_analysis.png)

### Diet Type and Exercise Patterns

| Diet Type | Sedentary | Moderate | Active |
| --- | ---: | ---: | ---: |
| Vegetarian | 49.8% | 30.4% | 19.8% |
| Non-Vegetarian | 48.9% | 30.2% | 20.9% |
| Vegan | 50.5% | 30.6% | 19.0% |

Sedentary behaviour is the most common exercise level in every diet group. However, the three groups are almost identical, which shows that **diet type and exercise level are not related** in this dataset.

![Diet Type vs Exercise Level](outputs/figures/diet_exercise_analysis.png)

### Regional Cuisine Preferences

Each of the seven cuisines accounts for between **12.9% and 15.3%** of respondents in every region. In real data, you would expect regional cuisines to dominate their home regions, for example Bengali cuisine in the East or South Indian cuisine in the South. That pattern does not appear here.

![Regional Cuisine Preferences](outputs/figures/regional_cuisine_preferences.png)

---

## Key Insights

1. **Clear consumer profile:** most respondents are vegetarian, eat medium-spice food, and are sedentary. These would be useful targeting facts **if the data were real**.
2. **No links between behaviours:** diet, exercise, region, and cuisine are all independent of each other.
3. **PCA confirms it:** with variance spread evenly across dozens of components, there are no hidden patterns to find.
4. **Validate before you recommend:** checking relationships first prevented this project from presenting random variation as consumer insight.

---

## Business Applications

With real survey data, this same Orange workflow could support:

* Consumer segmentation
* Food product marketing and positioning
* Lifestyle-based customer targeting
* Regional menu and product planning
* Data-quality checks before survey results are used for decisions

---

## Skills Demonstrated

* Orange Data Mining
* Exploratory Data Analysis (EDA)
* Principal Component Analysis (PCA)
* Consumer and Survey Data Analysis
* Data Visualization
* Data Quality Assessment
* Market Research
* Business Insight Generation

---

## Quickstart

1. Install [Orange Data Mining](https://orangedatamining.com/download/).
2. Open `orange_workflow/food_preferences_analysis.ows` in Orange.
3. In the **File** widget, select `data/food_impact_india.csv`.
4. Open any widget to view its output and regenerate the figures.

---

## Project Structure

```
consumer-food-preferences-analysis/
├── data/
│   ├── food_impact_india.csv
│   └── dataset_readme.md
├── orange_workflow/
│   └── food_preferences_analysis.ows
├── outputs/
│   └── figures/
│       ├── workflow.png
│       ├── pca_analysis.png
│       ├── diet_exercise_analysis.png
│       └── regional_cuisine_preferences.png
└── README.md
```

---

## Future Improvements

* Repeat the analysis on a real consumer survey with spending and purchase data
* Apply clustering to test for consumer segments
* Build a predictive model for food preference classification
* Compare Orange workflows with Python implementations
* Create an interactive dashboard for exploring consumer groups

---

## Disclaimer

Educational portfolio project demonstrating consumer analytics, exploratory data analysis, and Orange Data Mining techniques. The dataset appears to be synthetic, so its findings should not be applied to the real Indian population.

---

## Author

**Akriti Kachroo**
Portfolio: [akritik12.github.io](https://akritik12.github.io/)

# Food Impact on Indians: Consumer Behaviour & Market Segmentation

> A market research project that analyzes food preferences and consumer behaviour across India, and groups respondents into actionable customer segments using **K-Means clustering** in **Orange Data Mining**.

![Orange](https://img.shields.io/badge/Orange-Data%20Mining-orange)
![Method](https://img.shields.io/badge/Method-K--Means%20Clustering-blue)
![Domain](https://img.shields.io/badge/Domain-Market%20Research-green)

<!--
  HOW TO USE THIS TEMPLATE
  Every value in [square brackets] is a placeholder. Replace each one with your real
  results from Orange before publishing, and delete any row you don't have data for.
  Delete this comment when you're done.
-->

---

## Project Overview

Food choices in India vary widely by age, income, region, and lifestyle. Businesses that treat all consumers the same miss these differences. This project uses survey data to answer three questions:

1. **What** do Indian consumers prefer to eat, and how often?
2. **How** do these preferences change across demographic groups?
3. **Which** distinct customer segments exist, and how should a business target each one?

The analysis is done entirely in **Orange Data Mining**, a visual, no-code analytics tool, which makes every step easy to follow and reproduce.

---

## Business Questions

| # | Question | Method |
| --- | --- | --- |
| 1 | What does the typical respondent look like? | Distributions |
| 2 | How do preferences differ by age, gender, and occupation? | Box Plot, Distributions |
| 3 | How are behaviour variables related? | Scatter Plot |
| 4 | What natural customer segments exist? | K-Means Clustering |
| 5 | How should each segment be targeted? | Segment profiling |

---

## Dataset

| Detail | Value |
| --- | --- |
| Source | [Food Impact on Indians (Kaggle)]([ADD KAGGLE LINK]) |
| Type | Consumer survey |
| Raw size | [17,686] responses × [N] columns |
| After cleaning | [N] responses |
| Key variables | [e.g. Age, Gender, Occupation, City, Food Preference, Frequency of Eating Out, Monthly Food Spend] |

### Data preparation

* Removed [N] rows with missing values
* Selected [N] relevant columns with **Select Columns**
* Converted categorical answers to numeric features with **Continuize** (one-hot encoding)
* Scaled all features with **Normalize** so no single variable dominates the clustering

---

## Orange Workflow

```
File → Select Columns → Continuize → Normalize → K-Means → Data Table
  │                                                 │
  ├→ Distributions                                  ├→ Scatter Plot (colored by cluster)
  ├→ Box Plot                                       └→ Box Plot (compare clusters)
  └→ Scatter Plot
```

![Orange Workflow](outputs/orange_workflow.png)

The full workflow file is available at [`orange_workflow/food_impact.ows`](orange_workflow/food_impact.ows).

---

## Exploratory Analysis

### Age Distribution
![Age Distribution](outputs/age_distribution.png)

[One or two sentences on what the chart shows, e.g. "Most respondents are aged 18–30, so results lean toward younger consumers."]

### Food Preference Distribution
![Food Preference Distribution](outputs/food_preference_distribution.png)

[e.g. "[X]% of respondents are vegetarian, [Y]% non-vegetarian."]

### Spending Behaviour
![Spending Behaviour](outputs/spending_boxplot.png)

[e.g. "Working professionals spend a median of ₹[X] per month on food, about [Y]% more than students."]

---

## Customer Segmentation (K-Means)

### Choosing the number of clusters

K-Means was run for k = 2 to [8]. The value of k with the highest silhouette score was selected.

| k | Silhouette Score |
| ---: | ---: |
| 2 | [0.00] |
| 3 | [0.00] |
| 4 | [0.00] |
| 5 | [0.00] |

**Selected k = [N]** because [it had the highest silhouette score / it gave the clearest, most usable segments].

![Cluster Scatter Plot](outputs/kmeans_clusters.png)

### Segment Profiles

| Segment | Name | Size | Typical Age | Food Preference | Spending | Key Behaviour |
| --- | --- | ---: | --- | --- | --- | --- |
| C1 | [e.g. Budget Students] | [N] ([X]%) | [18–24] | [ ] | [Low] | [ ] |
| C2 | [e.g. Health-Conscious Professionals] | [N] ([X]%) | [25–35] | [ ] | [High] | [ ] |
| C3 | [e.g. Traditional Home Cooks] | [N] ([X]%) | [35+] | [ ] | [Medium] | [ ] |
| C4 | [ ] | [N] ([X]%) | [ ] | [ ] | [ ] | [ ] |

---

## Key Insights

1. **[Headline finding]:** [Supporting number, e.g. "Segment C2 is only 18% of respondents but accounts for 35% of total food spending."]
2. **[Headline finding]:** [Supporting number]
3. **[Headline finding]:** [Supporting number]
4. **[Headline finding]:** [Supporting number]

---

## Recommendations

| Segment | Recommended Strategy |
| --- | --- |
| [Budget Students] | [e.g. Value combos, student discounts, and delivery offers during exam season] |
| [Health-Conscious Professionals] | [e.g. Premium healthy meal subscriptions and nutrition labelling] |
| [Traditional Home Cooks] | [e.g. Quality staples, bulk packs, and regional recipe marketing] |
| [ ] | [ ] |

---

## Repository Structure

```
Food-Impact-on-Indians-Market-Research/
├── data/               # Raw and cleaned survey CSV files
├── orange_workflow/    # Orange workflow file (.ows)
├── outputs/            # Charts, cluster plots, and workflow screenshot
├── report/             # Full written report (PDF)
└── README.md
```

---

## How to Reproduce

1. Install [Orange Data Mining](https://orangedatamining.com/download/) (version [3.x]).
2. Clone this repository:
   ```bash
   git clone https://github.com/akritik12/Food-Impact-on-Indians-Market-Research.git
   ```
3. Open `orange_workflow/food_impact.ows` in Orange.
4. In the **File** widget, select the CSV from the `data/` folder.
5. Open any widget to view its output.

---

## Tools Used

* **Orange Data Mining [3.x]:** data preparation, visualization, and clustering
* **[Excel / Python]:** initial data cleaning *(remove if not used)*

---

## Limitations

* **Self-reported data:** survey answers may not match real behaviour.
* **Sample bias:** respondents may not represent India's full population across regions, incomes, and ages.
* **K-Means assumptions:** it works best with round, similar-sized clusters and is sensitive to scaling and the choice of k.
* **Encoded categories:** one-hot encoding survey answers can give some questions more weight than others in the clustering.

---

## Future Improvements

* [ ] Build an interactive dashboard in Power BI or Tableau
* [ ] Compare K-Means with Hierarchical Clustering and DBSCAN
* [ ] Add region-level analysis across Indian states
* [ ] Predict segment membership for new customers with a classification model

---

## Author

**Akriti Kachroo**
Portfolio: [akritik12.github.io](https://akritik12.github.io/)

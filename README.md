# Google Play Store - Exploratory Data Analysis (EDA)

> A complete, structured exploratory data analysis on the Google Play Store dataset, covering data cleaning, feature engineering, correlation analysis, missing value treatment, and 10+ business-driven insights.

---

##  Project Structure

```
eda-google-playstore/
├── googleplaystore_new.csv      # Raw dataset (scraped from Google Play Store)
│    
├── EDA-google-playstore.ipynb   # Main analysis notebook (175 cells)
│    
└── README.md                    # Project documentation (this file)
```

---

##  About the Dataset

- **Source:** [Kaggle - Google Play Store Apps](https://www.kaggle.com/datasets/lava18/google-play-store-apps/)
- **Records:** 10,841 rows × 13 columns (raw)
- **Cleaned Records:** ~9,634 unique apps after deduplication

### Columns

| Column | Description |
|---|---|
| `App` | App name |
| `Category` | App category (e.g., Game, Tools) |
| `Rating` | Average user rating (1–5) |
| `Reviews` | Total number of user reviews |
| `Size` | App size (converted to bytes/MB) |
| `Installs` | Number of installs (cleaned to integer) |
| `Type` | Free or Paid |
| `Price` | App price in USD |
| `Content Rating` | Target audience (e.g., Everyone, Teen, Mature 17+) |
| `Genres` | App genre(s) |
| `Last Updated` | Date of last update |
| `Current Ver` | Current app version |
| `Android Ver` | Minimum Android version required |

---

##  Data Cleaning & Preprocessing

| Step | Details |
|---|---|
| **Size column** | Converted `M` → bytes, `k` → bytes; `"Varies with device"` → `NaN` |
| **Installs column** | Removed `+` and `,`; converted to `int` |
| **Price column** | Stripped `$` symbol; converted to `float` |
| **New columns** | `Size_in_MB`, `Installs_Category` (binned into 8 tiers) |
| **Missing values** | Dropped rows with <1% missing; imputed `Rating` via group mean by `Installs_Category` |
| **Duplicates** | Removed 483 exact duplicates; resolved near-duplicates by keeping highest-review record per app |

---

## Exploratory Insights (10 Questions Answered)

| # | Question | Key Finding |
|---|---|---|
| 3.1 | Which category has the most apps? | **Family** (~1,900 apps) |
| 3.2 | Which category has the most installs? | **Game** (13B+) |
| 3.3 | Which category has the most reviews? | **Game** - highest user engagement |
| 3.4 | Which category has the highest rating? | **Events, Art & Design, Books & Reference** (~4.4–4.5 avg) |
| 3.5 | Which category generates most revenue (paid)? | **Family** - by a large margin |
| 3.6 | Do free apps have better ratings than paid? | **Paid** apps rate slightly higher and more consistently |
| 3.7 | Which content rating group dominates? | **Everyone** - Play Store is primarily family-friendly |
| 3.8 | Which genres have the most high-rated apps? | **Board;Pretend Play**, **Comics;Creativity** (4.8 avg) |
| 3.9 | Does app size affect rating? | **No strong relationship** - UX matters more than size |
| 3.10 | Does price affect installs? | **Yes** - Higher price = sharply fewer installs |

---

## Statistical Analysis

- **Pearson Correlation** between `Reviews` and `Installs`: **r ≈ 0.64** (strong positive)
- **Log transformation** applied to `Installs` and `Reviews` to normalize skewed distributions
- **Correlation heatmap** visualizing all numerical features

---

## Key Conclusions

- The Play Store is **user-driven** - affordability, reliability, and engagement drive success.
- **Games, Family, and Lifestyle** dominate both reach and revenue.
- **High-rated categories** tend to focus on creativity, education, and personalization.
- **Paid apps** attract fewer downloads but deliver slightly higher user satisfaction.
- No strong link between app size and rating - **performance and UX > size**.
- Niche categories (Beauty, Comics, Parenting) represent **untapped market opportunities**.

---

##  Getting Started

### Run the Notebook

```bash
jupyter notebook notebooks/EDA-google-playstore.ipynb
```

---

## Requirements

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scipy`
- `jupyter`

---

## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).

---

## Acknowledgements

Dataset sourced from [Kaggle](https://www.kaggle.com/datasets/lava18/google-play-store-apps/) - originally scraped from the Google Play Store.

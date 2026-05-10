# 🏀 Explaining NCAA Tournament Seeding

A sports analytics project studying how the NCAA selection committee assigns March Madness seeds.

The goal was to understand how much of tournament seeding can be explained with public team metrics, and where the committee seems to deviate from what the numbers predict. We used NCAA men's basketball team-season data from 2008-2024 and built models to analyze expected seed, conference tournament effects, conference bias, and whether the NET era changed committee behavior.

## 📄 Report

Full writeup:

[Final Project Report - 36460 - Group 20.pdf](Final%20Project%20Report%20-%2036460%20-%20Group%2020.pdf)

## 📦 Technologies

- R
- tidyverse
- cbbdata
- multinomial logistic regression
- Bayesian hierarchical modeling
- bootstrapping
- cross-validation
- data visualization

## 🦄 What This Project Does

### 🎯 Predicts NCAA Tournament Seeds

We built a baseline expected-seed model using public pre-tournament metrics like:

- Wins Above Bubble (WAB)
- Barthag
- Adjusted offensive efficiency
- Adjusted defensive efficiency
- Strength of schedule

The combined model predicted 86.3% of teams within two seed lines of the committee's actual seed.

### 📊 Explains What Drives Seeding

The analysis found that resume-based metrics matter more than pure efficiency metrics. WAB was the strongest predictor, suggesting the committee cares more about what a team accomplished against its schedule than how strong the team looks on paper.

### 🏆 Tests Conference Tournament Effects

We tested whether teams get a seed boost from strong conference tournament performance after controlling for regular season metrics.

The result: there was no clear evidence that conference tournament wins provide an extra seed boost once team quality is already accounted for.

### 🏛️ Measures Conference Bias

We used seed residuals to test whether certain conferences are systematically over-seeded or under-seeded.

The strongest finding was that the SEC, Big East, and Big 12 were over-seeded by roughly 0.3 to 0.6 seed lines after controlling for team quality.

### 🧪 Checks the NET Era

We also tested whether committee behavior changed after the NET ranking system was introduced in 2019.

The evidence did not support a major shift. The committee's overall weighting of metrics looked mostly stable before and after NET.

## 🚦 How to Run

### 1. Clone the repo

```bash
git clone https://github.com/Danny625/Sports-Analytics-Project.git
cd Sports-Analytics-Project
```

### 2. Install R packages

Open R or RStudio and install the main packages:

```r
install.packages(c(
  "tidyverse",
  "nnet",
  "brms",
  "loo",
  "boot",
  "ggplot2",
  "readr",
  "dplyr"
))
```

You may also need `cbbdata` depending on whether you are pulling the data directly or using the saved local data file.

### 3. Run the analysis

Open the main `.Rmd` or `.R` file in RStudio and run the sections from top to bottom.

The project uses saved/preprocessed NCAA team-season data so the report does not depend on live API calls every time it is rendered.

## 🧠 Project Structure

```text
Sports-Analytics-Project/
├── README.md
├── Final Project Report - 36460 - Group 20.pdf
├── data/              # Saved or cleaned NCAA team-season data
├── scripts/           # Modeling and analysis scripts
├── figures/           # Plots used in the report
└── outputs/           # Model summaries, tables, or generated results
```

Some folders may differ depending on the current repo version.

## 🧩 How It Works

At a high level:

1. Load NCAA men's basketball team-season data from 2008-2024.
2. Keep tournament teams only and remove 2020 because the tournament was canceled.
3. Build an expected-seed model using public team metrics.
4. Compare predicted seeds to actual committee seeds.
5. Use the residuals to study where the committee deviates from the model.
6. Analyze conference tournament effects, conference-level bias, and NET-era changes.

## 👩‍🍳 The Process

We started with a baseline question: can NCAA tournament seeding be explained using publicly available metrics?

After building the expected-seed model, we used the model's errors as the interesting part of the project. If a team was seeded better or worse than expected, that residual gave us a way to study committee behavior beyond raw team quality.

From there, the project split into a few focused analyses: which metrics matter most, whether conference tournament runs affect seed, whether conferences are treated differently, and whether the introduction of NET changed the committee's weighting of metrics.

## 📚 What I Learned

- How to turn a sports debate into a statistical modeling problem
- How to use residuals to study human decision-making
- How to compare resume-based and efficiency-based team metrics
- How to evaluate multinomial classification beyond raw accuracy
- How Bayesian hierarchical models help with noisy group-level estimates
- Why uncertainty matters when making claims about bias or committee behavior

## 💭 Main Takeaways

- NCAA seeding is mostly explainable from public metrics.
- WAB is the strongest predictor, meaning resume quality matters a lot.
- Conference tournament wins do not appear to give teams a meaningful extra boost.
- The SEC, Big East, and Big 12 show small but credible over-seeding effects.
- The NET era does not show strong evidence of a major committee behavior shift.

## 💭 How It Can Be Improved

If we were continuing this project, we would probably:

- Add injury data or late-season momentum indicators
- Model conference effects separately by seed range
- Revisit the NET-era analysis once more post-2019 tournaments are available
- Connect seeding bias to actual tournament outcomes
- Add a cleaner reproducible pipeline for downloading and preprocessing the data

# Week 27: Email Campaign Strategy

Due to the cost of delivering email, **We decides to send email to only 25% of its subscriber base for week 27**.

Given the data provided:

---

## Modeling Strategy & Results

### Model Objective

To predict the likelihood of a subscriber responding to a campaign in **Week 27**, we trained supervised learning models on data from **Weeks 1 to 26** using selected features.

---

### Features Used for Modeling

The following features were used to train the models:

- `previous_week_campaign_sent`
- `lifetime_response_rate`
- `previous_week_response`
- `WEEK_SINCE_LAST_RESPONSE_CAT`
- `attribute1`
- `Sex`

---

### Model Performance (Accuracy)

| Model               | Accuracy     |
|---------------------|--------------|
| Logistic Regression  | 0.7510       |
| Random Forest       | 0.7749       |
| XGBoost             | 0.7746       |
| Gradient Boosting   | 0.7710       |

---

### Second Modeling Experiment: Expanded Feature Set

#### Model Objective

Refined prediction by incorporating **recency-based response features** to capture subscriber behavior in recent weeks.

---

#### Features Used

- All previous features, plus:
- `Number of responses in last 2 weeks`
- `Number of responses in last 3 weeks`
- `Number of responses in last 4 weeks`

---

#### Model Performance (Accuracy)

| Model               | Accuracy     |
|---------------------|--------------|
| Logistic Regression  | 0.7724       |
| Random Forest       | 0.7742       |
| Gradient Boosting   | 0.7672       |

---

### Third Feature Set: Added Statewise Response Rate

| Model               | Accuracy     |
|---------------------|--------------|
| Logistic Regression  | 0.7715       |
| Random Forest       | 0.7595       |

---

### Observations

- Random Forest performed well with initial features but dropped slightly with state-level feature.
- Logistic Regression was stable and benefited slightly from recency features.
- Adding statewise response rate did not significantly improve predictive power.

---

## 1. Which subscribers would you send email to?

- Selected the top 25% of subscribers by predicted probability of response.
- Subscriber IDs saved in: `results/top_25_prec_receivers.csv`

---

## 2. Which campaign(s) would you deliver to them?

- For each subscriber, all 10 campaigns were scored.
- The campaign with the **highest predicted response probability** was selected.
- Campaign assignments saved in: `results/sorted_data_campaign.csv`

---

## Campaign Distribution in Top 25% Target Group

| Campaign ID | # of Campaigns | % of Campaigns |
|-------------|----------------|----------------|
| 1           | 65             | 1.97%          |
| 2           | 83             | 2.52%          |
| 3           | 30             | 0.91%          |
| 4           | 1560           | 47.27%         |
| 5           | 37             | 1.12%          |
| 6           | 474            | 14.36%         |
| 7           | 926            | 28.06%         |
| 8           | 9              | 0.27%          |
| 9           | 10             | 0.30%          |
| 10          | 106            | 3.21%          |

> **Note:** Campaigns 4 and 7 dominate, indicating they are predicted to be most effective.

---

## 3. What do you expect the response rate to be?

- Expected response rate calculated as average predicted probability across selected subscribers.
- **Estimated Response Rate:** **78.98%**

---

## Weekly Response Rate (Weeks 1–26) & Modeled Response Rate

| Week | Response Rate |
|-------|--------------|
| 1     | 0.3009       |
| 2     | 0.2887       |
| 3     | 0.3271       |
| 4     | 0.3137       |
| 5     | 0.3256       |
| 6     | 0.3271       |
| 7     | 0.3281       |
| 8     | 0.3225       |
| 9     | 0.3241       |
| 10    | 0.3259       |
| 11    | 0.3870       |
| 12    | 0.3850       |
| 13    | 0.4041       |
| 14    | 0.4858       |
| 15    | 0.4849       |
| 16    | 0.4809       |
| 17    | 0.4944       |
| 18    | 0.4894       |
| 19    | 0.4860       |
| 20    | 0.4909       |
| 21    | 0.5108       |
| 22    | 0.5163       |
| 23    | 0.5238       |
| 24    | 0.5740       |
| 25    | 0.5675       |
| 26    | 0.5713       |

> **Modeled Expected Response Rate for Week 27:** **0.79**

---

### Summary

The model predicts a **significant uplift** in response rate (~79%) compared to historical weekly averages (~30%-57%), guiding ACME's targeted campaign delivery for week 27 to maximize efficiency and ROI.


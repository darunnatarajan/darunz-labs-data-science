# Mini project: Chennai food delivery EDA

**Covers:** Modules 5, 6 and 7
**Time:** two sessions
**Deliver:** one Jupyter notebook

---

## The situation

You have joined a food delivery startup as a junior data analyst. The ops team exported 123 orders from August and wants to know one thing:

> **Why do some deliveries take so much longer than others?**

The export is raw. Nobody has checked it. That is your job first.

## The data

`chennai-food-orders.csv`

| Column | Meaning |
|---|---|
| `order_id` | Order reference |
| `order_date` | Date of the order |
| `area` | Delivery area in Chennai |
| `restaurant_type` | Cuisine |
| `distance_km` | Restaurant to customer |
| `prep_time_min` | Kitchen time |
| `delivery_time_min` | Order placed to delivered |
| `order_value` | Bill amount in rupees |
| `rating` | Customer rating, 1 to 5 |
| `payment_mode` | How they paid |

---

## What to do

### Stage 1: Meet the data
Load the CSV. Report the number of rows and columns, the data type of each column, and the first few rows. Write one sentence saying what one row represents.

### Stage 2: Check its health
Find the duplicate rows and remove them. Count the missing values in each column and the percentage. Look at the unique values of every text column and note anything strange.

### Stage 3: Describe each column on its own
For the numeric columns, report mean, median, mode, standard deviation and skewness. For each one, say which centre you would quote to the ops head and why. Plot a histogram for at least two columns.

### Stage 4: Find what does not belong
Apply the IQR rule to `delivery_time_min` and `order_value`. Report Q1, Q3, IQR, both fences, and the outliers you find. Draw box plots.

For every outlier, decide: **data error or genuine extreme?** Justify each decision in one line. Handle each one and say what you did.

### Stage 5: Find the relationships
Build a correlation matrix and plot it as a heatmap. Make at least two scatter plots. Answer the ops team's question: what actually drives delivery time?

Also answer:
- Which area has the slowest average delivery?
- Which cuisine has the longest kitchen time?
- If you pick one order at random, what is the probability that it took more than 45 minutes?

### Stage 6: Say something useful
Write a short markdown cell at the end of the notebook with:
- three findings, each with the number that supports it
- two recommendations for the ops team
- one thing this data cannot tell you, and why

---

## Rules

- pandas, matplotlib and seaborn only.
- Every section starts with a markdown heading.
- Write a one-line conclusion under every output. A number with no sentence gets no marks.
- Never overwrite the original DataFrame. Keep `orders` raw and work on `clean`.
- If you drop or change any value, say why in a comment.

## How you will be marked

| | Marks |
|---|---|
| Data health found and fixed correctly | 25 |
| Right statistics, right centre chosen | 20 |
| Outliers found, and each one judged sensibly | 20 |
| Correlation read correctly, without claiming causation | 15 |
| Conclusions backed by numbers | 15 |
| Notebook is readable and runs top to bottom | 5 |

## Plan your time

**Session 1:** stages 1 to 3
**Session 2:** stages 4 to 6, then a five-minute presentation of your findings

## Submit

Restart your kernel and run the whole notebook once, top to bottom, before you submit. If it errors, it is not finished.

---

## Hints, if you are stuck

- Percentages missing: `df.isna().mean() * 100`
- Duplicates: `df.duplicated().sum()` then `df.drop_duplicates()`
- Strange text values: `df["area"].value_counts()`. Read that output carefully
- One rating in this file is impossible. Ratings go from 1 to 5
- One order value has an extra digit. Compare it with what similar orders cost
- Two deliveries took far longer than the rest. One weather event, one long distance. Check before you delete either
- Before and after cleaning, run the correlation twice. The difference is the most interesting thing you will find today

---

**Darunz** · Darun N · Chennai

# customer-segmentation-clustering

`pandas` · `numpy` · `scikit-learn` (`KMeans`, `PCA`, `StandardScaler`, `silhouette_score`)
· `matplotlib` · `seaborn` · RFM feature engineering · unsupervised clustering ·
k selection via elbow and silhouette

Segmenting the customers of a UK online retailer by purchasing behaviour, so a marketing
team can target campaigns instead of treating the base as one group. Given a transaction
log, build a per-customer RFM profile (Recency, Frequency, Monetary), cluster it with
K-Means, and translate each cluster into a named segment a campaign can act on: reward the
high-value regulars, win back the lapsed, nurture the new. This is the unsupervised
counterpart to `london-airbnb-regression` (regression) and `telco-churn-classification`
(classification): no target variable, so the work is in feature construction, choosing the
number of clusters, and defending what each cluster means.

## Key findings

_TBC once the clustering notebook has real output._

## Data

`data/online_retail_II.xlsx` is the [UCI Online Retail II dataset](https://archive.ics.uci.edu/dataset/502/online+retail+ii):
transactions for a UK-based online gift retailer, roughly 1 million rows across two sheets
(2009-2010 and 2010-2011), fields Invoice, StockCode, Description, Quantity, InvoiceDate,
Price, Customer ID, Country. The file is committed to the repo as-is (45.6 MB, under
GitHub's 50 MB warning threshold), matching Projects 1 and 2, so there is nothing to
download. See the UCI page above for the source and licence terms.

## Approach

Per-customer RFM aggregation from the raw transaction log, then StandardScaler, then
K-Means with the number of clusters chosen from an elbow plot and silhouette scores over
k = 2 to 10. PCA to two components for a cluster scatter plot, cluster profiling by mean
R/F/M, and a named persona per segment. EDA and RFM construction live in
`notebooks/eda.ipynb`; scaling, clustering, and profiling in
`notebooks/clustering.ipynb`.

## Results

_TBC once k is chosen and clusters are profiled._

## Setup

```bash
conda create -n customer-segmentation-clustering python=3.11
conda activate customer-segmentation-clustering
pip install -r requirements.txt
```

## Run

```bash
jupyter notebook notebooks/
```

Two notebooks, run top to bottom: `eda.ipynb` (cleaning, EDA, RFM feature engineering)
then `clustering.ipynb` (re-runs the RFM build at the top since notebooks do not share
kernel state, then scaling, K-Means, PCA, profiling).

## Known limitations

_TBC._

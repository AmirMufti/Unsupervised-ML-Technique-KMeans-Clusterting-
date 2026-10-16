# World Happiness: Country Clustering with K-Means

Grouping countries by economic, social and well-being indicators using K-Means clustering, with PCA to visualise the result in two dimensions.

**Dataset:** World Happiness Report country-level data. The analysis uses the **2023** snapshot.

## Approach

1. **Filter.** Keep the 2023 rows, then drop rows with missing values. This leaves **120 countries**.
2. **Features.** Nine indicators: Life Ladder (life satisfaction), Log GDP per capita, Social support, Healthy life expectancy at birth, Freedom to make life choices, Generosity, Perceptions of corruption, Positive affect and Negative affect.
3. **Scale.** Standardise each feature with `StandardScaler`, so no single feature dominates the distance calculation.
4. **Choose k.** Fit K-Means for k = 1 to 10 and plot the within-cluster sum of squares (elbow method). The notebook settles on **k = 4**.
5. **Fit and inspect.** Fit the final model, assign each country a cluster, and compare cluster profiles with a pair plot.
6. **Visualise.** Project the standardised data onto two principal components and plot the clusters with their centroids, labelled by country.

## Findings

- The notebook assigns every country to one of four clusters and shows each feature's distribution by cluster in a pair plot.
- The choice of k = 4 comes from the elbow plot. Checking a few neighbouring values of k and reporting a silhouette score would make that choice easier to defend.
- The PCA plot is a two-dimensional view of the data, so it shows only part of the structure in the nine indicators.

The notebook contains the cluster assignments, pair plots of each feature by cluster, and the PCA plot.

## Limitations

- Only 120 countries remain after filtering, and only one year is used, so the clusters describe 2023 and may be unstable.
- K-Means assumes roughly spherical clusters of similar size, which may not hold for these indicators.
- Clusters describe similarity, not cause. They are a starting point for questions, not evidence about what drives wellbeing.

## Repository contents

| File | Purpose |
|---|---|
| `World Happiness Clustering Unsupervised ML .ipynb` | Full analysis: cleaning, scaling, elbow method, K-Means, PCA visualisation |
| `Project Brief (KMeans).docx` | Original project brief |

## Reproduce

Place the World Happiness CSV in the project folder and open the notebook. Requires `pandas`, `numpy`, `scikit-learn`, `matplotlib` and `seaborn`.

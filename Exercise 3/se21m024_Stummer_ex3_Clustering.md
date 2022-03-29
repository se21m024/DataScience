# Data Science<br/>Exercise 3<br/>Clustering

## Student:<br/>se21m024<br/>Thomas Stummer<br/>

# Big Dataset: Census Income

<br/>
Data taken from:
<br/>https://archive.ics.uci.edu/ml/datasets/Census-Income+%28KDD%29
<br/><br/>
Data Original Owner:
<br/>U.S. Census Bureau
<br/>http://www.census.gov/
<br/>United States Department of Commerce
<br/><br/>
Donor:
<br/>Terran Lane and Ronny Kohavi
<br/>Data Mining and Visualization
<br/>Silicon Graphics.
<br/>terran '@' ecn.purdue.edu, ronnyk '@' sgi.com
<br/><br/>

# Algotithms

The following three clustering algorithms were chosen because the results of the comparison overview on scikit learn seemed good:

- Partitative Clustering (K-Means Family)

"Mini-batch k-means: k-means variation using "mini batch" samples for data sets that do not fit into memory." quote

two_means = cluster.MiniBatchKMeans(n_clusters=params["n_clusters"])

- Agglomerative Clustering

  average_linkage = cluster.AgglomerativeClustering(
  linkage="average",
  affinity="cityblock",
  n_clusters=params["n_clusters"],
  connectivity=connectivity,

- density based: DBSCAN
  DBSCAN and not OPTICS because it is significatly faster

would have been nice: because looks very good on demo page

- Spectral Clustering

tbd: are they all also well applicable /efficient for high dimensional data?

#####################################

## General information

The following 14 features were extracted from the data set. Categorical columns were converted to numbers and elements with NaN values were dropped.

![Big_Feature_Head_1](./Screenshots/Big_Feature_Head_1.png)

<div style="page-break-after: always"></div>

## Dimensionality Reduction Algorithms

### PCA

A basic two dimensional principle component analysis was performed.<br/>
It can be seen that the variance along the coordinate 1 is higher than that of coordinate 2. For coordinate 2 only a few outliners are present. For coordinate 2 a relativly strict lower barrier seems to be present with very few and subtile outliners.

![Big_PCA_1](./Screenshots/Big_PCA_1.png)

The principle component 1 accounts for 75.6% of the variance in the data set, whereas principle component 2 accounts for 17.6% of the variance. This sums up to 93.2%.

<div style="page-break-after: always"></div>

To make the result more comparable to the other two selected algorithms a second PCA was performed on the same subset of 1000 data points as for the other algorithms.

![Big_PCA_2](./Screenshots/Big_PCA_2.png)

The plot suggests a similar overall structure of the data. The principle component 1 accounts for 76.9% of the variance in the data set, whereas principle component 2 accounts for 16.3% of the variance. This sums up to 93.2%. This is a light difference when compared to the full data set but not significant for the purpose of this inspection.

<div style="page-break-after: always"></div>

### MDS

For the MDS a subset of 1000 data points was taken form the original data set because otherwise the computation time would have exceeded acceptable limits.<br/>
It can be seen that the variance along the coordinate 2 is higher than that of coordinate 1 (excluding outliners). For coordinate 1 only a few outliners are present. Comparing to the results of the PCA, the MDS also produces a projection where one component accounts for most of the variance. The diagrams seem to be rotated agains each over at about 60 degrees. A noticable difference is, that the MDS creates more outliners along the <i>weaker</i> coordinate (in this case coordinate 1 to the left) compared to the PCA (hardly any outliners after the barrier at the bottom.). The PCA plot also reveals a slight <i>brushed</i> distribution along coordinate 2 which is not present in the MDS plot.

![Big_MDS_1](./Screenshots/Big_MDS_1.png)

<div style="page-break-after: always"></div>

### t-SNE

For the t-SNE a subset of 1000 data points was taken form the original data set because otherwise the computation time would have exceeded acceptable limits. This data points are the same ones as used for the MDS.<br/>
The t-SNE produces a C-shaped projection with far more space between the individual data points compared to e.g. the MDS projection (with the same amount of data points) which results in a single cohesive cluster. While the PCA and the MDS seem to result in similar projections, the t-SNE clearly produces a very distinct projection in the two dimensional space. Futhermore the t-SNE projection suggests plenty of small to medium sized clusters in comparison to the other two algorithms.

![Big_t-SNE_1](./Screenshots/Big_t-SNE_1.png)

<div style="page-break-after: always"></div>

# Small Dataset: Heart Disease

<br/>
Data taken from:
<br/>https://archive.ics.uci.edu/ml/datasets/Heart+Disease
<br/><br/>
Data Creators:<br/>
1. Hungarian Institute of Cardiology. Budapest: Andras Janosi, M.D.<br/>
2. University Hospital, Zurich, Switzerland: William Steinbrunn, M.D.<br/>
3. University Hospital, Basel, Switzerland: Matthias Pfisterer, M.D.<br/>
4. V.A. MediMcal Center, Long Beach and Cleveland Clinic Foundation: Robert Detrano, M.D., Ph.D.<br/>
<br/><br/>

## General information

The following 14 features were extracted from the data set. Categorical columns factorized and elements with NaN values were dropped.

![Small_Feature_Head_1](./Screenshots/Small_Feature_Head_1.png)

<div style="page-break-after: always"></div>

## Dimensionality Reduction Algorithms

### PCA

A basic two dimensional principle component analysis was performed.<br/>
The principle component 1 accounts for 76.7% of the variance in the data set, whereas principle component 2 accounts for 13.5% of the variance. This sums up to 90.2%. For the observer this seems quite surprising as those numbers are not that different from those of the PCA for the big data set (census income), although the plot of the small data set indicates a wider variance in both components (more of a ball-shape compared to the long-ellipse-shape of the big data set).<br/>
The data points seem to be clustered around a specific center point in the mid/low left of the diagram with more outliners along coordinate 2 compared to coordinate 1.

![Small_PCA_1](./Screenshots/Small_PCA_1.png)

<div style="page-break-after: always"></div>

### MDS

When applying MDS the data appears in a more oblong shape compared to applying PCA. But again the data points seem to be clustered in only one center point. Overall the points appear to be more cohesive compared to the projection gathered with PCA.

![Small_MDS_1](./Screenshots/Small_MDS_1.png)

<div style="page-break-after: always"></div>

### t-SNE

When applying t-SNE the data seems to be more clustered and remarkable regions without any data points (I would even describe them as <i>holes</i>). A quite isolated cluster can be observed in the top right of the plot. The overall distance between the points seems to be less condense when compared to the plots of the other algorithms. This also correlates to the interpretation of the t-SNE application on the big data set. This is not surprising, due to the intention of the algorithm to place similar data points near to each other and dissimilar data points far away from one another.

![Small_t-SNE_1](./Screenshots/Small_t-SNE_1.png)

# Comparison to analysis without dimensionality reduction

Investigating the results of the previous algorithms, I would say that, for both data sets, the benefit of the dimensionality reduction lays in the ability to estimate the overall distribution and clustering of the data. With the <i>classical</i> approach applied in the first exercise, the distribution based on single features or the correlation between two or max. three features can be spotted but it does not indicate the overall clustering of the data. On the over hand, when projecting higher dimensional data into e.g. the two dimensional space, the correlation between individual features cannot be observed but insights in the overall structure of the data can be gained. This might be benefitial to select a specific cluster algorithm and estimate a first number of clusters for these algorithms. Summing up, I find it very difficult to spot specific correlations in the data when observing more than two or three features at once, independent of the application of dimensionality reduction.

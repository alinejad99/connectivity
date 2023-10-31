# EEG Coherence Analysis for Mental Arithmetic Tasks

### Investigating Functional Connectivity During Mental Arithmetic

## Exploring Brain Connectivity

In this repository, we delve into the analysis of brain connectivity during mental arithmetic tasks, aiming to understand how different brain areas communicate when engaged in numerical processing. The human brain operates by coordinating various regions of neurons, generating electromagnetic signals. By examining the similarity and relationships between these signals, we can gain insights into brain function and even study related neurological conditions. We create a weighted graph representing these connections, which can be further analyzed to reveal patterns in brain activity. It's important to note that, given the signal-to-noise ratio (SNR) of EEG data, we opted not to employ causal methods like Granger causality or phase analysis for our initial analysis.

### Local Connectivity Effects

One challenge we encounter is the local coherence of brain regions due to electromagnetic properties. This phenomenon results in strong connectivity among nearby nodes while producing weaker connections between distant nodes. To mitigate this effect, we examined the influence of pink noise in relation to distance and normalized graph weights based on amplitude variations across the entire network.

## Statistical Testing of Graph Weights

To identify significant edges within the connectivity graph, we conducted a statistical t-test using two distinct labels: EEG signals from high-performing "good" calculator subjects and low-performing "bad" subjects. The results of this analysis are presented below:

## Unsupervised Analysis

For a more comprehensive understanding, we applied unsupervised dimensionality reduction techniques (TSNE/PCA) to the weighted graphs.

### Spectral Coherence-Based Results:

The following four plots are based on spectral coherence graphs:

### Mutual Information-Based Results:

Mutual information (MI) forms the basis for these graphs, calculated by evaluating the spectral similarities between two signals:

The MI-based plots demonstrate excellent separation between two label classes, with more than 85% accuracy for TSNE and 80% for PCA. In contrast, the spectral coherence-based graphs achieve values of 75% and 70%, respectively. While both methods are viable, MI-based results offer a superior representation of signal distribution. The disparity between TSNE and PCA highlights the non-linear pattern extraction advantages in such tasks. It's worth noting that these EEG recordings follow standard 10-20 placement, and we expect even greater accuracy and representation when applied to sEEG or ECoG with higher SNR.

### Selective Graph Weight Analysis

To enhance clustering and classification models, we selected a set of approximately 20-30 most significant electrodes based on T-Test p-values. Subsequent plots replicate the clustering (PCA/TSNE) with these electrodes, resulting in improved clustering outcomes:

## A Comparative View

Clustering results based on the MI method exhibit better separation compared to the SC method, although two data nodes within the clusters remain less distinguishable. This could be attributed to the diverse mental states of the subjects. Even if we consider these data points as clustering or classification errors, the test accuracy exceeds 84%.

### Granger Causality:

Granger causality examines whether two time series (e.g., signals) can predict each other, creating a directed graph. We reanalyzed previous findings based on Granger causality:

## Final Insights

* Important Note: FDR correction was later applied to all results. All statistical tests passed the FDR test, and the modified results are detailed in the main paper.
* Most results were obtained using EEG signals filtered within the [15-25]Hz range using a 4th-order Butterworth bandpass filter, along with spectral coherence (SC) and mutual information (MI) calculated over 3-second time windows (20 frames).
* The most significant channels were [F8, P3, O1, F7, T3, T4] based on T-Test average test, with the lowest p-values and FDR correction applied.
* The most significant edges were [F8-F7, F8-T3, F8-P3, T3-P3, O1-T3, T4-T3].
* The standard deviation of graph weights averages per subject is greater for subjects with good calculation abilities, indicating a higher variation in a good subject's graph compared to a poor one.
* Electrode distance has less impact on MI graphs than on SC.
* Subjects with higher performance exhibit greater coherence between the F8 signal and six other electrodes in the occipital and temporal regions.
* GC and MI are less influenced by electrode distance.
* Granger causality results in clustering and classification are superior to SC and slightly better than MI, potentially due to the reduced impact of electrode distance.
* The selective inclusion of specific connections (the most significant ones) in clustering improves the separation of clusters.

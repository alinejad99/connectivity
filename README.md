

# Mental Arithmetics EEG Coherence Graph

### Analysis of functional connectivity during mental arithmetics

## Connectivity

Information in connections: Activities in a brain are correlated to a specific mental task, which uses bunch of neurons for a biological computation that produces electromagnetic signal. In a system like human brain, the similarity between these recorded signals (electromagnetic, chemical, etc...) can give us a good information about functions of brain and later investigations about related diseases. The similarity criterion and variable normalizations finally form a weight matrix that can be transformed into a weighted graph, and if criterion is causal, a directional graph. Due to lower SNR than some other type of signals, we did not apply causal methods (Granger, Phase, etc...) on this dataset initially.

### Local connectivity effects

Due to electromagnetic properties of cortical matter, closer areas have more coherence; this problem causes the graph to be strongly connected in local nodes and weaker in distance nodes. In order to reduce this effect, we measured pink noise effect versus distance and normalized graph weights based on different frequency amplitude changes across the whole network. 

## Connectivity graph weight statistical test

In order to determine if some edges are important or not, we performed a statistical t-test on graph edges, based on two defined labels; high performance (good) calculator subject's EEG signal and low performance (bad) subject's EEG. Its resault are shown below:

## Unsupervised results

For better illustration, we calculated unsupervised TSNE/PCA clustering results on weighted graphs.

### Spectral coherence based:

The next 4 plots are based on spectral coherence graphs:

### Mutual information based:
Mutual information based graphs are calculated based on MI value between spectrum of two signals, the next 4 plots:


On MI (mutual information) based plots we can draw eclipses that separate two label classes with more than 85% accuracy (TSNE) and 80% (PCA). Yet on the SC (spectral coherence) based ones this value is respectively 75% and 70%. SC based values are still plausible but MI based ones are much better, showing the better representation in distribution domain of signals.

Difference between TSNE and PCA also shows the non-linear pattern extraction advantage in such task. Consider that these EEG recordings are based on standard 10-20, non invasive and we expect much more accuracy and representation when these methods are applied on sEEG or even ECoG with much higher SNR. 

### Selective graph weight results

In order to enhance clustering and classification models, set of about 20-30 most significant electrodes based on T-Test p-values got selected. Following plots are the same clusteing (PCA/TSNE) repeated with these electrodes, enhancing clustering results:

### Comparison
Clustering results based on MI method are better spearated related to SC method; although two of data nodes in the clustering are not well separated. This can be due to very different mental state of those subjects. for example, one may not focus on the tasks and still do the calculations in a flausible result. Even with assuming those data as error of our clustering and classifiers the test accuracy is more than 84%.

### Granger causality:
This method intuitively tests if two series (e.g signals) can predict eachother or not, this method is not symmetric; that means GC(X, Y) != GC(Y, X). So it gives a directed graph. We recalculated previous parts based on GC:


## Overall results

* ->Important Note: FDR correction has been applied later on results. All statistical tests have passed FDR test and their modified results are in the main paper. 
* Most results are based on EEG[15-25]Hz 4th order butterworth bandpass filtered signals, Spectral coherence (SC) and Mutual information (MI) on 3s time windows (20 frames)
* Most significant channels: [F8, P3, O1, F7, T3, T4] based on TTest average test, lowest p-values, FDR correction applied.
* Most significant edges: [F8-F7,F8-T3,F8-P3,T3-P3,O1-T3,T4-T3]

* Graph weights average std per subject is more on subjects with good calculation qualities; that means total variation of a good subject's graph is higher than a bad one 
* Electrode distance has less effect on MI graphs than SC
* Subjects with higher performance have more coherence between F8 signal and 6 other electrodes near occipital and temporal area.

* GC and MI are less affected by electrode distance 
* Granger causality results (clustering, classification) are better than SC and a bit better than MI, this could be due to lesser effect of electrode distance
* Selecting specific connections (most significant ones) for clustering enhanced the spearation and clusters.



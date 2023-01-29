## Implementing Lazy Learning k-NN on IRIS dataset and creating ggplot2 - R style visuals on Jupyter Notebook

**Points to note when using KNN:**
- k-NN classifier are model-free lazy-learners as they delay the process of modeling the training data until it is needed to classify the test instance 
- Classifying unknown records is expensive as the algorithm:
1. First, calculates the proximity or distance of the test datapoint to all the training datapoints to pick the top-k nearest datapoints
2. And then takes the majority vote of class labels by weighing the vote according to distance Eg: weight = 1/d^2
- As we are using euclidean distance here, we have to rescale features so that one feature doesn't end up dominating the distance calculation. Selecting appropriate proximity measure is required for the algorithm to work well.
- It can handle presence of interacting attributes by using proximity measures
- It has difficulty handling missing values as they are usually required for proximity calculation and redundant attributes can dominate the proximity calculation if present in large numbers 


#### Proximity between features can calculated by using several metrics:
1. For **Continous features**: the most common distance metric is the Minkowski Distance (Manhattan or L1 norm, Euclidean or L2 norm and L-infinity norm)
2. [Mahalanobis Distance](https://stats.stackexchange.com/questions/62092/bottom-to-top-explanation-of-the-mahalanobis-distance) can also be used, to consider the variance (scale) of different features and covariance among them. Using this metric is computationally expensive as it requires calculating the covariances as a scaling term.
3. For **Binary features**: Hamming Distance (which measures in how many positions are two vectors different), Simple matching coefficient[(#11 + #00)/(#01 + #10 + #11 + #00)], Jaccard[(#11)/(#01 + #10 + #11)]
4. For **Document similarity**: the most commonly used measure is cossine similarity as we use the # common words between documents to measure similarity and this metric is invariant to scaling and can handle non-binary counts.

#### [Plotnine](https://plotnine.readthedocs.io/en/stable/) package in Python can be used to create visuals which are client ready, using the sytanx used in the ggplot2 package in R

#### References: 
1. Pang-Ning Tan, Michael Steinbach, Anuj Karpatne, and Vipin Kumar. 2018. Introduction to Data Mining (2nd Edition) (2nd. ed.). Pearson.

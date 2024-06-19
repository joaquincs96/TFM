<h1 align="center"> Characterization of behaviors in neutrophils using machine learning techniques </h1>

# Abstract

Neutrophils, the most abundant leukocytes in human blood, are pivotal in the immune response to inflammation. Their dynamic behavior and functional diversity, shaped by varied stimuli, make them important agents in inflammation context. The zebrafish model, with its amenability to genetic manipulation and transgenic lines expressing fluorescent proteins, offers an exceptional model for visualizing and studying immune cells live, including neutrophils. Recent advances such as single-cell RNA sequencing and spatial transcriptomics have enriched our understanding of neutrophil biology. However, these techniques are limited as they capture only static snapshots and do not account for cellular dynamics. This project focus in a novel approach to analyze behavioral changes in neutrophils within a zebrafish model of chronic skin inflammation, used to simulate conditions like psoriasis and atopic dermatitis. By observing neutrophils in Spint1a-deficient larvae treated and untreated with a chronic inflammation inhibitor over four hours, we were able to extract a range of morphometric and kinetic parameters. Subsequent statistical and multivariate analyses distinguished significant differences between treated and untreated neutrophils. Furthermore, a Random Forest model identified key features such as sphericity, speed, and lysozyme expression that distinguish between the two neutrophil populations. Principal Component Analysis identified two distinct neutrophil populations, termed "Potentially Beneficial" and "Potentially Dangerous." To further refine this classification, a separated Random Forest model was developed, which utilized morphological parameters such as cell area, volume, and ellipsoid axis length as key features. This model effectively distinguished between the two populations, underscoring the importance of these parameters in identifying the potential impact of neutrophils on disease progression. This approach enhances our understanding of neutrophil behaviors in disease contexts and also identifies potential markers for evaluating new treatments for chronic inflammatory diseases, highlighting the potential of integrating behavioral analysis with molecular and spatial profiling technologies. 

# Repository Contents and Methodology Overview

## Extraction of New Parameters from Imaris Data
This repository contains markdown files detailing the advanced metrics developed to enhance our understanding of neutrophil dynamics and interactions within experimental settings. These metrics, derived from the original dataset through specific computational approaches, focus on both spatial and temporal interactions, offering an intricate view of cellular dynamics at play.

### Calculating Interaction Timepoints with Aggregates
We developed functions to determine the precise moments when neutrophils interact with cellular aggregates, calculating the Euclidean distance between neutrophils and aggregates based on spatial coordinates (X, Y, Z) and assumed spherical volumes. The interactions were quantified by checking if a neutrophil's position fell within an aggregate's volume at each timepoint during its track. This was implemented in R using functions that appended columns indicating the number of timepoints a neutrophil interacted with an aggregate (TimePoints.Interacting) and a cumulative count over the entire track (Track.TimePoints.Interacting).

### Duration of Interactions
Interaction timepoints were converted into seconds to provide a temporal dimension to the interaction data, making the durations of interactions interpretable both per timepoint and cumulatively across the track.

### Initiation of Contact
We refined the analysis by identifying the initiation points of contact between neutrophils and aggregates, introducing a categorical parameter (NewContact) to denote whether a neutrophil initiated contact at any given timepoint, capturing the dynamic initiation of interactions.

### Quantifying Contacts with Aggregates
Our metrics were extended to include the number of distinct contacts a neutrophil made with different aggregates, tracking transitions from non-interaction to interaction states across sequential timepoints. This provides insights into the frequency and pattern of neutrophil-aggregate interactions within the experimental timeframe.

### Continuous Interaction Tracking
We also assessed the persistence of interactions by calculating the maximum continuous time that neutrophils remained in contact with an aggregate, aiding in understanding the sustained interaction capabilities crucial for interpreting their role in immune responses.

### Proximity and Migration Analysis
By calculating distances to the nearest aggregates and analyzing migration patterns, we inferred neutrophils' movement strategies and interaction propensities. Migration types were classified based on interaction status and behavior, offering a detailed characterization of neutrophil dynamics.

### Neutrophil Aggregation
Interactions among neutrophils themselves were examined to determine the extent of their aggregation and collective behavior, crucial for understanding the social aspects of neutrophil actions in response to various stimuli.

## Statistical and Multivariate Analysis
The markdown files also detail the statistical analyses employed to compare groups based on the Condition of the zebrafish (treated with CGP3466B or untreated) and the Interaction Status of neutrophils. We used Levene’s Test for Equality of Variances, Student’s t-tests, Welch’s t-tests, and Mann-Whitney U tests for evaluating differences across groups. Multivariate analyses like Generalized Linear Models (GLMs) were performed to understand the combined effects of various factors on neutrophil behavior.

## Principal Component Analysis (PCA)
PCA was employed to reduce dimensionality and uncover patterns in the dataset of scaled neutrophil tracking parameters, with visualizations created to highlight different factorial parameters such as neutrophil conditions and interaction statuses. Confidence ellipses at the 95% level were added to plots to visually assess data clustering based on specified groups.

## Clustering and Random Forest Model Generation
Files include details on hierarchical clustering using various linkage methods and the stability assessment through bootstrap resampling techniques. Additionally, we describe the construction and prediction of Random Forest models, focusing on data preparation, model training with cross-validation, and the evaluation of model performance through confusion matrices.

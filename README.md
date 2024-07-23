# Total-Nitrogen-Levels-in-Lakes-Project
<!-- About The Project -->

<a name="readme-top"></a>

<!-- TABLE OF CONTENTS -->


<summary>Table of Contents</summary>
<ol>
  <li><a href="#introduction">Introduction</a></li>
  <li><a href="#steps-carried-out">Steps carried out</a></li>
     <li><a href="#analysis">Analysis</a></li>
    <ul>
      <li><a href="#ridge-regression">Ridge Regression</a></li>
      <li><a href="#visualize-categorical-feature-distribution">Visualize Categorical Feature Distribution</a></li>
      <li><a href="map-visualization-of-health-facilities">Map Visualization of Health Facilities</a></li>     
    </ul>
  </li>
  </li>
</ol>


# Author: Lilian Ngonadi

# Introduction

There is need to understand the nitrogen level in the lake and the covariate variables that are important in explaining total nitrogen in lakes. Thirteen (13) covariates such as baseflow, nitrate deposition (NO3Depo), total atmospheric nitrogen deposition (TotalDepo), land use metrics (urban, rowcrop, pasture, forest, and wetland percentages), lake area, maximum depth, connectivity, and LWR, were studied for the four different regressions (Ridge, Lasso, PCR and PLS) 

# Steps carried out

To carry out the exploration of the four biased regression techniques, the following steps were taken: 

- Worked with my transformed data for the previous assignment  
- Plotted different graphs for the four biased regression  
- Identified the optimal lambda value  
- extracted the best model using k-cross validation.  
- Obtained the metrics for the four biased regression (Rsquare, MSE, MAE, RMSE)  
- The ridge regression was fitted for the transformed data, and all the predictors were included in the model because ridge regression doesn't entirely shrink to zero. The lasso regression model was fitted for the transformed data and four predictors were selected (Runoff, sqrt (Rowcrop), Forest and log(Maxdepth).  
- The PCR loadings were obtained for the 7 components and the eigen values obtained  and attached in the appendix.  
- The PLS was optimal when we have only 2 components.  
- Overall, PLS seem to perform better than other regression model followed by the  ridge regression, though it is difficult interpreting result from ridge regression since all the coefficients were added.

# Analysis

## Ridge Regression

From figure (1) we can see that the tuning parameter extends from –2 to 6 and this suggest that as the log of the regularization parameter lambda increases, the coefficients of the predictors are shrunk towards zero but are never exactly zero. The plot suggests that Baseflow, NO3 and TotalDepo show a pronounced decrease than others while MaxDepth shows a decreasing trend in coefficient magnitude as the penalty increases. 
Figure 1 summarizes that as the penalty for the magnitude of coefficients increases (higher lambda), most variables tend to have a reduced influence on the model 

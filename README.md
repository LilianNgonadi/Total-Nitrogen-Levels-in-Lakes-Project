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
      <ul>
        <li><a href="#scaling-of-predictors">Scaling of Predictors</a></li>
        <li><a href="#choosing-optimal-lambda-value">Choosing Optimal Lambda Value</a></li>
  <li><a href="#extracting-the-best-model">Extracting the best model<a></li>
      </ul>
      <li><a href="#lasso-regression">Lasso Regression</a></li>
      <li><a href="#principle-component-regression">Principle Component Regression</a></li>
      <li><a href="#partial-least-square-regression">Partial Least Square Regression</a></li>
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

![Figure1](figure1.png "Figure1")

From figure 2, most of the variables show a decreasing trend in their coefficients as the L1 norm increases, but none of the variable shrink exactly to zero indicating that all the variables maintain some degree of influence in the model.
![Figure2](figure2.png "Figure2")

From figure 3, Max depth might be contributing less to the model as more variance is explained indicating it might not be as strong as others. The remaining variables' coefficients seem relatively stable across the range of the penalty, indicating that they have a consistent effect on the response variable regardless of the penalty strength.

![Figure3](figure3.png "Figure3")

## Scaling of Predictors

From table 1, the various predictors and TN has various range of scale standard deviation indicating a diverse impact these predictors may have in the study.

![Table1](table1.png "Table1")

From figure 4, the differences in the coefficients' absolute values decrease, indicating a more
uniform shrinkage effect across all predictors. Some predictors have larger absolute values of coefficients at lower lambda, indicating they have a significant impact on the outcome when there's less regularization. The coefficient of the predictors decrease in absolute value as lambda increases, but none are reduced to zero, which is typical in ridge regression.

![Figure4](figure4.png "Figure4")

From figure 5, the plot indicate14 predictors but none of the coefficient is completely reduced to zero. Also, the coefficient shows that as the betaL2 scaled regularization increases the coefficient changes

![Figure5](figure5.png "Figure5")

## Choosing Optimal Lambda Value

From figure 6 above, as the value of log(λ) increases, the MSE increases for a while before it starts to rise. The region where we have stability shows that this is where we have the optimal λ value where the model achieves the minimum of MSE. The plot depicts the mean squared prediction error MSE lambda against log lambda. The gray bar at each point show MSE lambda plus and minus one standard error. The first dashed lines shows the location of the minimum of MSE. The second dashed lines shows the largest lambda value such that the error is within 1 standard error. . The best lambda is given as 0.5346
![Figure6](figure6.png "Figure6")

## Extracting the best model 
The negative mean prediction of -34.38 suggests that, on average, the model predicts a decrease or negative outcome for the response variable under average conditions of the predictors Negative coefficients for NO3Depo, Runoff, and log(MaxDepth) suggest that increases in these predictors are associated with decreases in the response variable, indicating potentially adverse effects. Positive coefficients for TotalDepo, sqrt(Urban), sqrt(Rowcrop), sqrt(Pasture), sqrt(Wetland), log(LakeArea), and both connectivity variables indicate that these factors are associated with increases in the response variable, suggesting beneficial or enhancing effects. Small magnitude coefficients, such as for Baseflow and Forest, imply a minimal impact on the response variable

![Table2](table2.png "Table2")

From the Ridge metrics in Table 3, 65.60% of the variability in the log (TN) response variable can be explained by the Lasso regression model above. The R square difference between the predicted variable and actual variable is 0.2205. On average the model prediction are 0.3671 units away from the actual value while the standard deviation of the prediction error is 0.4696

![Table3](table3.png "Table3")


## Lasso Regression

In figure 7, the lasso regression plot suggests that while some predictors maintain their importance at different levels of regularization, others are more sensitive and become less influential in the model

![Figure7](figure7.png "Figure7")

The plot reveals that the predictor "NO3depo" has the most significant positive coefficient, which decreases rapidly as lambda increases, suggesting it is sensitive to the regularization. "Baseflow" and "Runoff" have large negative coefficients that reduce with lambda, but more gradually. Predictors like "Urban," "Rowcrop," "Pasture," "Forest," "Lakearea," "MaxDepth," "ConnectivityDR_Stream," and "LWR" tend to have smaller and more stable coefficients. The number of non-zero coefficients decreases with increasing lambda, indicating a simpler model with fewer predictors. Overall, the plot suggests that some environmental factors have a more robust influence on the response variable than others in this Lasso regression model.

![Figure8](figure8.png "Figure8")

From figure 9, plot predictor-standardized coefficients vs. L1 norm of vector scaled to OLS fit. Some predictors, such as "Runoff," "Urban," and "Pasture," have relatively stable paths, suggesting that they are consistently important across different lambda values. "NO3depo" starts with a high positive coefficient that decreases quickly, indicating initial importance that diminishes with stronger regularization. "Baseflow" has a negative coefficient that also decreases in magnitude with regularization. Predictors like "Lakearea" and "Wetland" have coefficients that approach zero more quickly, suggesting they may be less important in the presence of regularization.

![Figure9](figure9.png "Figure9")

As lambda increases, the MSE initially decreases, reaching a minimum before starting to increase again. This pattern suggests that there is an optimal value of lambda that minimizes the MSE, thus providing the best balance between bias and variance in the model. The numbers at the top indicate the number of non-zero coefficients in the model at each lambda value. With higher lambda, the model becomes more regularized, resulting in fewer non-zero coefficients,
simplifying the model at the expense of potentially increasing the MSE. The lambda value that minimizes the test MSE turns out to be 0.094. The best lambda is given as 0.094

![Figure10](figure10.png "Figure10")

In summary, the Lasso algorithm has identified NO3Depo, Runoff, Rowcrop, Forest, Wetland, MaxDepth, and LWR as significant predictors, with varying degrees of positive and negative associations with the response variable. 

![Table4](table4.png "Table4")

From the Lasso metrics in Table 5, 64.7% of the variability in the log (TN) response variable can be explained by the Lasso regression model above. The R square difference between the predicted variable and actual variable is 0.2210. On average the model prediction are 0.3648 units away from the actual value while the standard deviation of the prediction error is 0.4701

![Table5](table5.png "Table5")

From table 6, the performance of Ridge and Lasso regression is abit similar with Ridge having a negligibly higher R-squared and slightly lower MSE and RMSE, and Lasso having a marginally lower MAE.

![Table6](table6.png "Table6")

## Principle Component Regression

The error decreases as more components are added, reaching its lowest at 7 components (CV RMSEP = 0.4813, adjCV RMSEP = 0.4794), suggesting that adding up to 7 components minimizes the prediction error in this cross-validation setup.
Beyond 7 components, the RMSEP starts to increase indicating that adding more components does not significantly improve the predictive capability of the model and may instead lead to overfitting.
The percentage of variance explained in the predictors increases with each component added, reaching 84.22% with the 7 components. This is expected as more components capture more information (or variance) present in the X variables.
The variance explained in the TN response variable increases gradually with the number of components used. Starting from 36.65% with 1 component, it increases to 62.54% with 7 components. The most significant increase in explained variance in TN is observed initially, with diminishing returns as more components are added beyond the 7th component.
The optimal number of components to use for prediction, based on minimizing the cross- validated RMSEP and considering the explained variance, appears to be around 7 components.

![Table7](table7.png "Table7")
![Table7(1)](table7(1).png "Table7(1)")

From figure 11 it was noticed that with fewer components the coefficient exhibits larger variance which shows that each additional component alters the model. Also, at some certain level it was noticed that as more components were added the changes in the coefficient diminishes and the line begins to converge. Including more component beyond 7 does not substantially change the coefficients.

![Figure11](figure11.png "Figure11")

This is a plot used to determine the optimal number of component and from the plot it indicates that the optimal number of components is 7 which indicates that seven components are sufficient to achieve an acceptable balance between model complexity and prediction accuracy.

![Figure12](figure12.png "Figure12")

This PCR model indicates a complex relationship between the dependent variable and various environmental and land-use factors. Positive coefficients (e.g., for certain square root- transformed land uses like urban areas, row crops, pastures, and wetlands) suggest that these factors contribute to an increase in the dependent variable. In contrast, negative coefficients (e.g., for forest areas, baseflow, NO3 deposition, runoff, and certain log-transformed variables like lake area and max depth) indicate factors that contribute to a decrease in the dependent variable.

![Table8](table8.png "Table8")

From the PCR metrics in Table 9, 62.5% of the variability in the log (TN) response variable can be explained by the principal component regression model above. The R square difference between the predicted variable and actual variable is 0.217. On average the model prediction are 0.355 units away from the actual value while the standard deviation of the prediction error is 0.465

![Table9](table9.png "Table9")

## Partial Least Square Regression

From table 10, the RMSEP values continue to decrease slightly as more components are added, the rate of decrease in RMSEP slows down significantly after 2 components. This suggests that the first two components capture the most significant patterns in the data, and additional components only offer marginal improvements in predictive accuracy.
The optimal number of components to use for prediction, based on minimizing the cross- validated RMSEP and considering the explained variance, appears to be around 2 components.

![Table10](table10.png "Table10")
![Table10(1)](table10(1).png "Table10(1)")

The plot in figure 13 shows how each predictor influences the response variable for different numbers of components in the model. The coefficients that are close to zero suggest a weak influence on the response variable. The variability among the lines for different numbers of components indicates how stable the coefficient estimates are as complexity is added to the model.

![Figure13](figure13.png "Figure13")

This is a plot used to determine the optimal number of component and from the plot it indicates that the optimal number of components is 2 which indicates that two components are sufficient to achieve an acceptable balance between model complexity and prediction accuracy.

![Figure14](figure14.png "Figure14")

From the Pls metrics in Table 11, 68.8% of the variability in the log (TN) response variable can be explained by the Partial least square model above. The R square difference between the predicted variable and actual variable is 0.180. On average the model prediction are 0.329 units away from the actual value while the standard deviation of the prediction error is 0.425

![Table11](table11.png "Table11")

 The PLS model identifies both positive and negative relationships between various environmental and land-use factors and the logarithm of Total Nitrogen concentration. The model suggests that: (row crops, pastures) significantly increase Total Nitrogen concentrations. Urban areas also contribute positively, to a lesser extent. In contrast, natural land covers like forests and larger or deeper water bodies are associated with lower Total Nitrogen concentrations.
Atmospheric depositions have mixed effects, with nitrogen oxide depositions reducing Total Nitrogen concentrations, while total depositions increase it.

![Table12](table12.png "Table12")

PLS is the overall best model followed by that of Ridge regression.

![Table13](table13.png "Table13")


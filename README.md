# Survival Analysis - UV lamp RUL prediction model

&nbsp;

## 1. Problem Definition
- Objective
  - To predict the lifetime of a UV lamp    
  - To provide optimal process conditions to maximize the lamp's lifespan.      
- Variables    
  1) X data: Lamp process conditions (Oxygen amount, number of burner rotations, temperature, etc)    
  2) Y data: Lifetime of UV Ramp    

&nbsp;

## 2. Why Survival Analysis in this project??         
- **_Because, Y is Time-to-Event data_**
> In this project, there are two states of the lamp: "Alive" and "Gas Leak".     
> Time data for each state exists.        
>  - "Alive": The life of the lamp is **not over** yet. The Y value cannot be trusted as the minimum value of the ramp life.    
>  - "Gas Leak": The life of the lamp is **over**. Y value can be trusted with the confirmed lamp lifetime.    
>  This case is called Time-to-Event data.    

&nbsp;

## 3. What is Survival Analysis?
- **_Survival Analysis is a probabilistic approach to analyze uncertain Y._**
> #### [Concept of Survival Analysis]      
> Survival Function: The probability that the lamp will survive until the time(t).    
> Survival Regression: A methodology for estimating Survival Function using the feature of an object to know the lifespan.     
>> So, We applied Survival Analysis Algorithms that implemented through various machine learning techniques. 

&nbsp;

## 4. Development Framework     
![Framework](https://user-images.githubusercontent.com/55779934/154243790-0a7b239b-593a-4e57-b6e2-857810526c6f.jpg)    

&nbsp;

## 5. Description of Each Process (see the code above)

### [Data Preprocessing]     
  - Unnecessary Feature Removing    
  - Data Imputation     
    - Multivariate Feature Imputation(Estimation using the distribution of variables other than missing values.)    
    - using Scikit-learn IterativeImputer Function    
  - Data Scaling     
    - Robust Normalization(Outliers are less affected by normalization using quantile values instead of mean and standard deviation.)      
  > code: "1. Data Preprocessing.ipynb"     

&nbsp;

### [Feature Engineering]     
  - One-hot Encoding 
  - Feature Selection 
    - Correlation based feature selection     
    - Stepwise feature selection   
    - RFECV(Recursive Feature Elimination with Cross Validation) Feature Selection    
  - Feature Extraction     
    - AutoEncoder dimensionality reduction     
  - _Various Feature Engineering methods experimented on models, of which Autoencoder had the best performance._
  > code: "2. Feature Engineering.ipynb"        

&nbsp;

### [Modeling]    
  - _Experimented by implementing various models._
  - **Model 1: Xgboost Survival Embedding**    
    - Gradient Boosting algorithm based on the ensemble model of tree-based models   
    - XGBoost-based Survival Analysis Package     
  - **Model 2: Random Survival Forest**     
    - A model using a survival tree in RandomForest    
    - Each survival tree division criterion uses "the log-rank splitting rule".    
    - Meta-analysis using the average performed to increase accuracy and prevent overfitting.    
  - **Model 3: Deepsurv**     
    - It is a model that combines Survival Analysis and Neural Network and is Cox proportional Hazard Model based.        
    - Deep feed-forward neural network    
    - DeepSurv advances and the model expands to apply to nonlinear data and real-world problems    
  > code: "3. Modeling-Deepsurv.ipynb", "3. Modeling-RandomSurvivalForest.ipynb", "3. Modeling-XGBoost Survival Embedding.ipynb"        

&nbsp;

### [Ensemble Models]      
  - We ensembled the results of the three models to improve the model's performance.    
  > code: "4. Ensemble Models.ipynb"        


&nbsp;

### [Evaluate Models]      
  - Survival Analysis Performance Evaluation Metric 
    - Log-likelyhood   
    - AIC    
    - **_Concordance Index_** -> We choose this method.     
      - It can be interpreted as the AUC value of the sensed data.    
      - Providing objective quality indicators        
 - Final Output: Estimated lamp life time    
  - Model Output : Survival Probability    
    - The estimated value is also derived by the probability distribution.     
    - We set the final predicted value as the **Median value of the probability distribution**.    

# Survival Analysis - UV lamp RUL prediction model


## 1. Problem Definition
- Objective
  - To predict the lifetime of a UV lamp    
  - To provide optimal process conditions to maximize the lamp's lifespan.      
- Variables    
  1) X data: Lamp process conditions (Oxygen amount, number of burner rotations, temperature, etc)    
  2) Y data: Lifetime of UV Ramp    



## 2. Why Survival Analysis in this project??         
- **_Because, Y is Time-to-Event data_**
> In this project, there are two states of the lamp: "Alive" and "Gas Leak".     
> Time data for each state exists.        
>  - "Alive": The life of the lamp is **not over** yet. The Y value cannot be trusted as the minimum value of the ramp life.    
>  - "Gas Leak": The life of the lamp is **over**. Y value can be trusted with the confirmed lamp lifetime.    
>  This case is called Time-to-Event data.    



## 3. What is Survival Analysis?
- **_Survival Analysis is a probabilistic approach to analyze uncertain Y._**
> #### [Concept of Survival Analysis]      
> Survival Function: The probability that the lamp will survive until the time(t).    
> Survival Regression: A methodology for estimating Survival Function using the feature of an object to know the lifespan.     
>> So, We applied Survival Analysis Algorithms that implemented through various machine learning techniques. 



## **Process**     
**1. Data Preprocessing**     


**2. Feature Engineering**     



**3. Modeling**     


**4. Ensemble Models**     







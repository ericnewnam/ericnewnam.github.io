## Which Features Are King? An Analysis of Different House Characteristics on the Resulting Price for King County, USA.
<br><br>
Eric Newnam

**Abstract**

King County encompasses Seattle, WA. The goal of the study was to find clear correlations between certain features of the King County house sales dataset(2), and the resulting house price values. Would it be possible to fit a predictive model using regression analysis to predict, with a minimum of error, the dollar value? Were the features of **_lot area, being on the waterfront_**, and **_having a large number of rooms_** the main features driving a higher house selling price? This was a hypothesis going into the study. The study began by re-encoding certain features and performing random sampling to get 1000 observations from the total dataset. The Price feature was also log-transformed after analyzing its distribution. The model was fitted and iteratively improved. It was found that the lot area was not significant to the model, and having a large number of bedrooms was not a strong effect on the price. It turned out that having a **_high-grade rating_**, **_high condition rating_**, and **_living area_** were the strongest predictors. The model was validated with an 80/20 train to test split, examining the resulting performance and error. The model was also validated with a 5-fold cross validation, showing good performance with out-of-sample data.

<br><br>
**Introduction**

Given a dataset of 21,613 house sales transactions, would it be possible to create a robust predictive model to predict selling prices? What are the most important features that affect the resulting house price? It was postulated that the lot square footage, being located on the waterfront, and having many bedrooms were the strongest predictors. The initial exploratory analysis found that the price values were extremely right-skewed, and required a transformation. The resulting log(price) transformed distribution appeared somewhat better, but possibly not an ideal shape. Our kurtosis value of 0.841 indicated a slightly flatter shape to the distribution, and a corresponding thickening of the shoulders of the tails, according to DeCarlo.<sup>(1)</sup> This may still indicate skewness to the price data.

<br><br>
**Methodology**

The dataset contains house sale prices for King County, which includes Seattle. The home sales span the dates from May 2014 through May 2015. The methodology was:
- Get the dataset from [Kaggle.](https://www.kaggle.com/harlfoxem/housesalesprediction)
- Examine the data, features, and datatypes. Come up with a hypothesis.
- Use random sampling to create a smaller subset of 1000 observations.
- Pre-process the data: create dummy variables for categorical features and transform data as required.
- Observe scatterplot matrix to assess the linear relationships between predictors, and check for multicollinearity between predictors.
- Fit the full model with all predictors and view diagnostics, fix any data issues. Remove any influential outliers.
- Use several model-selection methods to select and fit the best model with fewer predictors.
- Examine residual plots to determine if the model assumptions are met, and if any further data transformations may be required.
- Try several interaction terms.
- Take note of the strength and weaknesses of predictors. Answer to the hypotheses put forward before the study regarding which features are the strongest on the resulting house price.
- Validate the model with an 80/20 train to test split of the dataset. Examine the differences in error between the training data and the testing data. Use a K-fold cross validation to assess the model’s performance with out-of-sample data performance.
- Compare the validation metrics of the model to other teammates’ models and choose the best performing model as the final result.

<br><br>
**Analysis, Results, and Findings:**

The regression analysis was conducted using SAS. The exploratory data analysis of the King County house price dataset began with a determination of which predictors may need recoding into dummy variables, and which predictors may have a significant effect on the resulting value of the house price. The dataset contains 21,613 observations and is in a comma-separated-value format. 

The dataset was found to contain 21 features from which to choose from in order to obtain a meaningful hypothesis: **_the ID number, Date, Price (in dollars), Number of Bedrooms (1-9), Number of Bathrooms (¾-6), Living Space Square Footage, Lot Square Footage, Number of Floors (1-3), Waterfront (y/n), Rating of the View (0-4), the Condition (1-5), the Grade (4-13), Above-ground Square Footage, Basement Square Footage, the Year Built, the Year Renovated, Zipcode, Latitude, Longitude, Average Living Space Square Footage of the Nearest 15 Neighbors, and average Lot Square Footage of the 15 nearest neighbors._** The ID number was not included in the fitting of our models, as this was a unique identifier for each observation, and we were left with 19 features that were potential predictors for our response variable **Price**. The first step was to use random sampling to select 1000 observations from the full dataset from which to perform our analysis and create our training and test data sets. We began by looking at the distribution of the **Price** with a histogram and boxplot of our randomly selected subset of 1000 observations. 

The distribution of the **Price** appeared to be right-skewed, with an upper range of house prices much higher than would normally be expected for a normal distribution. The mean ($552,003) was greater than the median ($455,000) indicating a heavily right-skewed distribution. The histogram also visually showed a distribution for the observed **Price** values to be extremely right-skewed. The inter-quartile range ($318,050) was much smaller than the total price range of $81,000 to $4,500,000. These extremely high-priced homes are valid data points, as the top observations all showed large prices in the same 7-figure level and should not be discarded, but we had to transform the **Price** to create a well fitted model.

After the normality plot was examined, we performed a log transformation to the **Price**. The resulting normality plot appeared to be much better with an almost normal distribution. However, the right-tail still had a slight curvature and may have been influenced by the extremely high-priced homes on the upper end of the range. These have shown to be valid data points however, and they were left in the model for the remaining stages of examination. The histogram was much more symmetric, with the mean (13.0567) almost equal to the median (13.0281). The kurtosis was a bit low with a value of 0.8412. 

A dummy variable was created for the **Year Renovated**, as the feature was mostly populated by zeroes, with an occasional year value, it was thought best to re-code the variable to a binary output. The existing 0 meant that the house was not renovated, and the year value re-coded to 1, signifying that the house has been renovated. We also re-coded the **Number of Bedrooms, Number of Bathrooms, Number of Floors**, the **Condition**, the **View**, and the **Grade** into a set of dummy variables. The **Year Built** was re-coded into a numeric value indicating the current **Age** of the house (in years) as of 2017. These preparatory steps brought our potential model predictors up to 43. The variables for the **Latitude, Longitude**, and the **Zipcode** were not used in the fitting of the model, as these would not be valid quantitative values as-is, but would need some re-mapping into new categorical variables, requiring a further study, which we will examine in the near future.

The model was initially fitted with the 43 predictors. Examining the Pearson correlation table, there were two potential areas of multicollinearity: the **Living Square Footage** vs **Above-ground Square Footage** (r = 0.87787), and the **Lot Square Footage** vs the **Lot Square Footage 15** (r = 0.87717). Overall, the houses in the dataset were mostly of the 1-floor type, with 477 houses, followed by 2-floors (392), 1 ½ -floors (92), 3-floors (32), and 2 ½ -floors (8). 

We began fitting the model with many predictors, then progressively reduced the number to the independent variables that accounted for the most variation in the resulting **Price** value. The results from the regression procedure showed insignificance for several of the predictors: the Lot Square Footage, On the Waterfront, View Rating 1, View Rating 3, Square Feet Above, Square Feet of the Lot of Nearest 15 Neighbors, Having 9 Bedrooms, Having 2 Bathrooms, 4 Bathrooms, 5 Bathrooms, 6 Bathrooms, Having Been Renovated, and Having 2 ½ Floors. The variance inflation values showed a large range of values, with the largest being **Grade 7** (298.39348), and **Grade 8** (252.19902), among others. Checking the Pearson correlation table, we saw that the **Grade 7** and **Grade 8** correlation values do not come close to exceeding our threshold of 0.90 in any relationship. Although initially a cause for concern, according to Murray, et. al. <sup>(3)</sup>, variance inflation may be safely ignored for dummy variables representing categorical variables with three or more categories, as variance inflation will begin to show artificially. We left these values in the model going forward, as they were significant and did not appear out of place in our correlation table, with relatively moderate values. 

Before performing variable removal through a model selection method, we examined the influential outliers. There were 5 observations that appeared as being over 3 standard deviations from the mean: obs. 44, 63, 227, 333, and 936. Two of these appeared to be a bit excessively far from the mean, the **obs. 333** was 3.526 above and **obs. 44** was 3.293 above the mean. The rest appeared to be within reason. Obs. 44 is $795,000 and obs. 333 was $2,575,000. This was excessively high compared to other 4 bedroom houses of similar characteristics in the dataset, and we elected to drop the observation, and after further analysis also dropped observation 44, as they were seen as excessively influential when fitting the model. 

Performing the backward model selection method dropped 11 predictors and left 32 predictors with an adjusted R<sup>2</sup> value of 0.6896. Running the adjusted R<sup>2</sup> selection method yielded 34 predictors and an adjusted R<sup>2</sup> value of 0.6912, although some variables were insignificant. Having fewer predictors with only a slight drop in adjusted R<sup>2</sup> while removing the insignificant variables meant that the 32-predictor model from the backward selection method would be a stronger model moving forward. 

An Interaction term between the **Living Area Square Footage** and **Having a Nice View** was postulated to be a potential significant driver for a house price increase, however the resulting significance was too low to be included as a potential term in our model.

The residual plots were examined to affirm the model assumptions. The studentized residuals vs the **Living Area Square Footage, Age, Living Area Square Footage of the 15 Nearest Neighbors**, and the **residuals** vs the **predicted** values, all did not show any linearity in the plots. The points were all scattered relatively equally above and below the zero line. The only discernable pattern would be a density change of the data points from left to right, but this is explained by the data set containing less houses with higher area values, and progressively less older homes. The variance appears to be constant with the model, and our assumption of independence appears to hold. Viewing the Normality plot, the normality appeared to be satisfied, as the distribution of the studentized residuals followed an approximately straight line from left to right. There were discernable dips and small s-shapes appearing along the plot, however. These miniature tails may need some further investigation. Overall, the points do follow a normal distribution.

**The model equation:**
```
log(Price) = 10.19393 
           + (0.00017 * Living_Area_Square_Footage) 
           + (0.31602 * Has a View Rating 4) 
           + (0.0048 * Age of the House) 
           + (0.00008 * Living_Area_Square_Footage_15) 
           - (0.3734 * Has_2_Bedrooms) 
           - (0.4570 * Has_3_Bedrooms) 
           - (0.4855 * Has_4_Bedrooms) 
           - (0.4457 * Has_5_Bedrooms) 
           - (0.4824 * Has_6_Bedrooms) 
           - (0.8871 * Has_7_Bedrooms) 
           - (0.8448 * Has_8_Bedrooms) 
           - (0.6430 * Has_9_Bedrooms) 
           + (0.0901 * Has_3_Bathrooms) 
           + (0.4546 * Condition_2) 
           + (0.6919 * Condition_3) 
           + (0.7339 * Condition_4) 
           + (0.7976 * Condition_5) 
           + (0.8782 * Grade_5) 
           + (1.2932 * Grade_6) 
           + (1.5648 * Grade_7) 
           + (1.7914 * Grade_8) 
           + (2.0014 * Grade_9) 
           + (2.1283 * Grade_10) 
           + (2.1884 * Grade_11) 
           + (2.6372 * Grade_12) 
           + (2.2623 * Grade_13) 
           + (0.1153 * Has_a_Basement) 
           + (0.0822 * Has_Been_Renovated) 
           + (0.1352 * Has_1.5_Floors) 
           + (0.1157 * Has_2_Floors) 
           + (0.2147 * Has_2.5_Floors) 
           + (0.3843 * Has_3_Floors)
```
Dummy variables are defined as:
```
Where: Has a View Rating 4 = 1 (if the view is rated as 4)
       Has a View Rating 4 = 0 (if the view is rated as 0 to 3)

       Has 2 Bedrooms = 1 (if the house has 2 bedrooms)
       Has 3 Bedrooms = 1 (if the house has 3 bedrooms)
       Has 4 Bedrooms = 1 (if the house has 4 bedrooms)
       Has 5 Bedrooms = 1 (if the house has 5 bedrooms)
       Has 6 Bedrooms = 1 (if the house has 6 bedrooms)
       Has 7 Bedrooms = 1 (if the house has 7 bedrooms)
       Has 8 Bedrooms = 1 (if the house has 8 bedrooms)
       Has 9 Bedrooms = 1 (if the house has 9 bedrooms)
	   Has 2 Bedrooms = 
         Has 3 Bedrooms = 
         Has 4 Bedrooms = 
         Has 5 Bedrooms = 
         Has 6 Bedrooms = 
         Has 7 Bedrooms = 
         Has 8 Bedrooms =
         Has 9 Bedrooms = 0 (if the house has 1 bedroom)

	   Has 3 Bathrooms = 1 (if the house has 3 bathrooms)
	   Has 3 Bathrooms = 0 (if the house has 1 to 5 bathrooms)

	   Condition 2 = 1 (if the condition is rated as 2)
	   Condition 3 = 1 (if the condition is rated as 3)
	   Condition 4 = 1 (if the condition is rated as 4)
	   Condition 5 = 1 (if the condition is rated as 5)
	   Condition 2 = 
         Condition 3 = 
         Condition 4 = 
         Condition 5 = 0 (if the condition is rated as 1)

	   Grade 5 = 1 (if the grade of the house is rated as 5)
	   Grade 6 = 1 (if the grade of the house is rated as 6)
	   Grade 7 = 1 (if the grade of the house is rated as 7)
	   Grade 8 = 1 (if the grade of the house is rated as 8)
	   Grade 9 = 1 (if the grade of the house is rated as 9)
	   Grade 10 = 1 (if the grade of the house is rated as 10)
	   Grade 11 = 1 (if the grade of the house is rated as 11)
	   Grade 12 = 1 (if the grade of the house is rated as 12)
	   Grade 13 = 1 (if the grade of the house is rated as 13)
	   Grade 5 = 
         Grade 6 = 
         Grade 7 = 
         Grade 8 = 
         Grade 9 = 
         Grade 10 = 
	     Grade 11 = 
         Grade 12 = 
         Grade 13 = 0 (if the grade of the house is 4)

	   Has a Basement = 1 (if the house has a basement)
	   Has a Basement = 0 (if the house doesn’t have a basement)

	   Has Been Renovated = 1 (if the house has been renovated)
	   Has Been Renovated = 0 (if the house hasn’t been renovated)

	   Has 1.5 Floors = 1 (if the house has 1 ½ floors)
	   Has 2 Floors =   1 (if the house has 2 floors)
	   Has 2.5 Floors = 1 (if the house has 2 ½ floors)
	   Has 3 Floors =   1 (if the house has 3 floors)
	   Has 1.5 Floors = 
         Has 2 Floors = 
         Has 2.5 Floors = 
         Has 3 Floors = 0 (if the house has 1 floor)
```

The model equation contains a relatively large number of dummy variables, as the features of this particular dataset contained several qualitative ordinal value types. This may be a potential area for model improvement, as the model expression seems to be excessively long, and may not express the clarity of the relationships between the predictors that we would prefer. 

Examining the relationships between the independent variables of our model equation and the resulting house Price, we can determine the strongest affecting predictors. Listing them from strongest effect to weakest on Price, they are: **Grade 8, Grade 7, Grade 9, Grade 10, Grade 6, Condition 3, Condition 4, Grade 11, Having 4 Bedrooms, 3 Bedrooms, Grade 12, Condition 5, Living Area Square Footage, Age of the House, 2 Bedrooms, 5 Bedrooms, Grade 5, Grade 13, 3 Floors, Living Area of the Nearest 15 Neighbors, Having a Basement, 2 Floors, 6 Bedrooms, Condition 2, Having a Top Rated View of 4, 1 ½ Floors, 8 Bedrooms, 3 Bathrooms, 7 Bedrooms, 9 Bedrooms, 2 ½ Floors, and Having Been Renovated**. 

Computing a prediction for the house price of a house in King County with 2,500 sq ft of living area, a poor view level below 4, built in 2002, with 15 nearest neighbors having an average of 2,500 sq ft of living area, with 4 bedrooms, 2 bathrooms, 2 floors high, condition rating of 5, grade of 7, with a basement, has been renovated:

log(**Price**) = 13.1079 with a 95% confidence interval of 12.9606 to 13.2553.

**_Price_** = $492,820 with a 95% confidence interval of $425,321 to $571,088.


Computing a prediction for the house price of a house in King County with 3,150 sq ft of living area, with a view rating of 4, built in 1995, with the nearest 15 neighbors having an average area of 3,000 sq ft of living area, with 5 bedrooms, 5 bathrooms, 2 ½ floors high, condition rating of 4, grade of 8, with a basement, and has not been renovated:

log(**Price**) = 13.8333 with a 95% confidence interval of 13.5253 to 14.1414.

**_Price_** = $1,017,948 with a 95% confidence interval of $748,106 to $1,385,262.

Overall, with our independent variables, the pattern of strength appears to be strongest with having a relatively **high-grade rating**, as these are the top 5 strongest affecting predictors. This is followed by having a relatively high condition rating, the living area, a moderate number of bedrooms; the Age of the house has a moderate effect. However, having a basement, having been renovated, and having a very high number of bedrooms and bathrooms are at the weakest end of the scale. 

Speaking to our initial hypothesis, we noticed that the initial thinking that the house price would be strongly driven by the lot area, being on the waterfront has been disproven. However, having a large number of rooms may have an overall positive effect. First, the lot size and the waterfront actually turned out to be *insignificant* to the model, and the standardized estimates show that simply having a high number of rooms is not directly a strong driver of the resulting house price, although having a large number of bedrooms does show a progressively smaller negative effect on the resulting Price. The strongest variables turned out to be having a **high-grade rating, high condition rating**, and **living area**. As the number of bedrooms increases, the overall negative effect on the house price is decreased, showing that a large number of rooms may in fact have a positive, yet indirect effect on the price. It was also very surprising to see that having a **top-rated view** only had a relatively weak positive effect on the resulting house price. 

If the house is rated as **grade 8**, the resulting house price increases by 499.8% over being a grade 4 house. Also, we see that if the house is rated as **grade 7**, the resulting price increases by 378.2% over being a grade 4 house. Interpreting the condition effects, we see that if the house has a **condition rating of 4**, the resulting house price increases by 108.3% over a base condition rating of 1. Similarly, if the **condition is rated as 3**, the resulting house price increases by 99.8% over the base rating of 1. Also surprisingly, if the house has a **top-rated view of 4**, the resulting house price only increases by 37.2% over having the lower view ratings.

The validation of the model began by splitting the dataset into an 80/20 split. 799 observations were randomly selected as the training set, and the remaining 199 observations were the test set. The resulting RMSE for the training set of 799 randomly selected observations was: 0.30659 and the R<sup>2</sup> value was: 0.7042. The test set counterpart RMSE was: 0.29344 and the R<sup>2</sup> value was: 0.67584. The training and testing sets both show a similar RMSE values, and the CV-R<sup>2</sup> value is relatively low with a value of 0.0283, indicating that the model may predict out-of-sample data well. The adjusted R<sup>2</sup> value of the test set showed a relatively large difference however, with a value of 0.61335 as opposed to the training: 0.6919. 

Train:  
- **RMSE**: 0.30659 
- **R<sup>2</sup>**: 0.7042 
- **AdjR<sup>2</sup>**: 0.6919 
- **GOF**: Ok 
- **Residuals**: Ok

Test: 
- **RMSE**: 0.29344 
- **MAE**: 0.23718 
- **AdjR<sup>2</sup>**: 0.61335 
- **CV-R<sup>2</sup>**: 0.0283

We then performed a K-fold cross validation (K = 5) in order to further validate the out-of-sample performance of the model. The results of the cross-validation showed a relatively consistent performance, as the ASE (Train) 0.08327 and the ASE (Test) 0.13426 were both similar in value, with a difference of 0.051, indicating good performance with out-of-sample data. Approximately 70% of the variability of the resulting house price value is accounted for by the variables we have in this model. 

<br><br>
**Future Work**

During the examination of our model assumptions, the normality plot of the studentized residuals showed several miniature S-shapes along several points along the relatively straight line of the plot. Although, we had determined that normality had been satisfied overall, the S-shapes may be a source for future investigation, and correction. 

Although the categorical variables have been re-coded into each discreet numerical step using dummy variables, there may be an opportunity to re-code the steps into larger categories, encompassing several steps into one. The overall number of predictors would be brought down, with an added potential of bringing errors down and increasing the adjusted R<sup>2</sup>.

The features corresponding to the Latitude, Longitude, and Zipcode have been dropped from the analysis, needing further re-coding and classification into area variables, requiring further study. Future analysis may include these new predictors, and may find new correlations between them and the resulting Price.

Although, we had used random sampling to create a smaller subset of 1000 observations from which to perform the analysis, there is an opportunity to use the entire population to perform the fitting of the model, as we do have access to the full population of 21,613 observations. 

<br><br>
**References**

1. DeCarlo, Lawrence T. 1997. On the Meaning and Use of Kurtosis. Psychological Methods Vol. 2, No. 3: 292-307.
2. Kaggle. (2017). House Sales in King County, USA [Data file]. Retrieved from Kaggle Web site: https://www.kaggle.com/harlfoxem/housesalesprediction
3. Murray, Leigh; Nguyen, Hien; Lee, Yu-Feng; Remmenga, Marta D.; and Smith, David W. (2012). Variance Inflation Factors in Regression Models With Dummy Variables, Annual Conference on Applied Statistics in Agriculture.

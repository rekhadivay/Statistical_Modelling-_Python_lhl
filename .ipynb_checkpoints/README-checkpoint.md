# Final-Project-Statistical-Modelling-with-Python

## Project/Goals

(1) We're using Python to build a statistical model. First, we gather data from different sources using  different APIs.

(2) we organize this data into a SQLite database.
(3) After creating tables in the database, we get a final dataset for further analysis.

(3) Performing EDA--In the analysis phase, we visually explore the data to find any unusual patterns or outliers. We also clean, group, and filter the data to make it ready for analysis. Additionally, we perform hypothesis testing to check if there are meaningful relationships between different features.
(4) we create a statistical model to study connections and make predictions between the dependent variable and other factor, the independent variables).

## Process
### 1) Connecting to CityBikes API: CityBikes
Citybikes is an API that provides bike sharing data for apps, research and projects.
CityBikes supports more than 400 cities and the Citybikes API is an interesting dataset for building bike-sharing transportation projects.

1. Explore the structure of the API, query the API and understand returned Data.
2. Choose a city covered by the CityBikes API and retrieve all available bike stations in that city.
3. For each bike station, use the API to call the latitude, longitude and number of bikes.
4. Parse the JSON object into a Pandas dataframe and created csv files.

# 2) Connecting to the Foursquare API and yelp API
(1) Connect to the Yelp API. This API offers similar services as Foursquare.
(2) For each of the bike stations in Part 1, query both APIs to retrieve information for the indian restaurants and Bars of Toronto location.
(3) Created a DataFrame for the Yelp results and Foursquare results.

(4) Compared the quality of the Yelp and Foursquare API data. Yelp API provided more complete data as mentioned in above steps, There are no null and duplicated value in yelp results compared to foursquare Api. Yelp provides a greater number of field attributes in its results compared to Foursquare

### 3) Joining the Data
(1) Join the data from CityBikes(part 1) with the Foursquare API and yelp API data (part 2) to create a new dataframe.
(2) Use data visualization to explore the data.
(3) Created own SQLite database and store the collected data from the Apis.
## 4) Building a Model
(1) Build a regression model using Python’s statsmodels module that demonstrates a relationship between the number of bikes in Toronto location and the characteristics of the restaurants in that location.
Interpreted results. Expand on the model output, and derive insights from your model.



## Results
-- Created a Linear Regression Model between 'Bikes Available' (dependent variable) and ['Distance', 'Rating'] (independent variables)

   OLS Regression Results                            
==============================================================================
Dep. Variable:        Bikes Available   R-squared:                       0.009
Model:                            OLS   Adj. R-squared:                  0.009
Method:                 Least Squares   F-statistic:                     118.0
Date:                Fri, 01 Dec 2023   Prob (F-statistic):           9.63e-52
Time:                        16:33:10   Log-Likelihood:                -83249.
No. Observations:               24829   AIC:                         1.665e+05
Df Residuals:                   24826   BIC:                         1.665e+05
Df Model:                           2                                         
Covariance Type:            nonrobust                                         
==============================================================================
                 coef    std err          t      P>|t|      [0.025      0.975]
------------------------------------------------------------------------------
const         15.5226      0.475     32.703      0.000      14.592      16.453
distance       0.0007      0.000      3.890      0.000       0.000       0.001
rating        -1.0057      0.066    -15.237      0.000      -1.135      -0.876
==============================================================================
Omnibus:                     6339.075   Durbin-Watson:                   0.040
Prob(Omnibus):                  0.000   Jarque-Bera (JB):            17532.458
Skew:                           1.357   Prob(JB):                         0.00
Kurtosis:                       6.096   Cond. No.                     7.49e+03
==============================================================================
# Interpretation of the model
(1) For "const," and "distance"with a p-value of 0.000, we reject the null hypothesis, suggesting that the intercept is statistically different from zero and suggesting that the distance variable is statistically significant.

(2) With R-squared around 0.009, the model explains a very small proportion of the variance in "Bikes Available".
   
(4) The R-squared and adjusted R-squared values in this regression output suggest that the model explains a very small   percentage (less than 1%) of the variance in the number of available bikes. The low values indicate that the chosen independent variables ("distance" and "rating") are not effective in explaining the variability in the dependent variable.
# Removing Rating and recreating model with 'Bikes Available'(dependent variable) and 'Distance' Independent variable

                            OLS Regression Results                            
==============================================================================
Dep. Variable:        Bikes Available   R-squared:                       0.000
Model:                            OLS   Adj. R-squared:                  0.000
Method:                 Least Squares   F-statistic:                     3.858
Date:                Fri, 01 Dec 2023   Prob (F-statistic):             0.0495
Time:                        19:45:11   Log-Likelihood:                -83365.
No. Observations:               24829   AIC:                         1.667e+05
Df Residuals:                   24827   BIC:                         1.667e+05
Df Model:                           1                                         
Covariance Type:            nonrobust                                         
==============================================================================
                 coef    std err          t      P>|t|      [0.025      0.975]
------------------------------------------------------------------------------
const          8.5079      0.116     73.283      0.000       8.280       8.735
distance       0.0003      0.000      1.964      0.050    6.96e-07       0.001
==============================================================================
Omnibus:                     6402.927   Durbin-Watson:                   0.031
Prob(Omnibus):                  0.000   Jarque-Bera (JB):            17671.455
Skew:                           1.372   Prob(JB):                         0.00
Kurtosis:                       6.091   Cond. No.                     1.81e+03
==============================================================================

## Challenges 
(--> Gathering Data from differenet APIs: Different APIs option available to gather data from: (1) Foursquare: (1) Need to provide precise parameters for POI(points of interest) (2) Data mixed with null values (3) Can make multiple requests (2)Yelp: (1) Detailed response with just including interested point in query (2) More precise data with no nulls or duplicated values (3) Very Limited API requests (Have to write complete code as to not run out of request)

---> It is Difficult to choose from available data from different sources.

We Worked with Data Available from Foursquare API, as Yelp has Limited API Requests available and it is time consuming to wait for requests to reset and use it

## Future Goals

 if i have extra time, I'd gather more data from the API.
 The current model lacks depth as it has low accuracy in fitting, and I believe incorporating more variables would enhance its performance. This way, we can extract more meaningful insights.
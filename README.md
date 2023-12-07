# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
The project goals include using Python to build a statistical model. This involves gathering data from various sources through APIs, organizing it into a SQLite database, and conducting Exploratory Data Analysis (EDA).
The analysis phase includes visually exploring the data, cleaning and preparing it, and performing hypothesis testing. 
Ultimately, the project aims to create a statistical model to study connections and make predictions, particularly focusing on understanding the impact of independent variables on the dependent variable.

## Process
### 1) Connecting to CityBikes API: CityBikes
Citybikes is an API that provides bike sharing data for apps, research and projects.
CityBikes supports more than 400 cities and the Citybikes.

 1. Explore the structure of the API, query the API and understand returned Data.
 2. Choose Toronto city covered by the CityBikes API and retrieve all available bike stations in that city.
 3. For each bike station, use the API to call the latitude, longitude and number of bikes.
 4. Parse the JSON object into a Pandas dataframe and created csv files.

Reference link: https://github.com/rekhadivay/Statistical_Modelling-_Python_lhl/blob/main/notebooks/city_bikes.ipynb

### 2) Connecting to the Foursquare API and yelp API

 1. Connect to Foursquare API and yelp API to extract Data.

 2. For each of the bike stations in Part 1, query both APIs to retrieve information for the indian restaurants of Toronto  location.

 3. Created a DataFrame for the Yelp results and Foursquare results. Created csv files.

 4. Compared the quality of the Yelp and Foursquare API data. Yelp API provided more complete data as mentioned in above steps.

 5. There are no null and duplicated value in yelp results compared to foursquare Api. Yelp provides a greater number of field  attributes in its results compared to Foursquare

Reference link: https://github.com/rekhadivay/Statistical_Modelling-_Python_lhl/blob/main/notebooks/yelp_foursquare_EDA.ipynb

### 3) Joining the Data
 1. Join the data from CityBikes(part 1) with the Foursquare API and yelp API data (part 2) to create a new dataframe.
 2. Created own SQLite database, established connection and store the collected data from the Apis..
 3. Use data visualization to explore the data, conducted Hypothesis testing.

Reference link: https://github.com/rekhadivay/Statistical_Modelling-_Python_lhl/blob/main/notebooks/joining_data.ipynb

### 4) Building a Model
 1. Build a regression model using Python’s statsmodels module that demonstrates a relationship between the number of bikes in Toronto location and the characteristics of the restaurants in that location.
 2. Provided an Interpreted results.
 3. Elaborating on the model output and extracting insights.

Reference link: https://github.com/rekhadivay/Statistical_Modelling-_Python_lhl/blob/main/notebooks/model_building.ipynb

## Results & Interpretation of the model
 Created a Linear Regression Model between 'Bikes Available' (dependent variable) and ['Distance', 'Rating'] (independent variables)
 
1. For "const," and "distance"with a p-value of 0.000, we reject the null hypothesis, suggesting that the intercept is statistically different from zero and suggesting that the distance variable is statistically significant.

2. With R-squared around 0.009, the model explains a very small proportion of the variance in "Bikes Available".
   
3. The R-squared and adjusted R-squared values in this regression output suggest that the model explains a very small   percentage (less than 1%) of the variance in the number of available bikes. The low values indicate that the chosen independent variables ("distance" and "rating") are not effective in explaining the variability in the dependent variable.
 4. Removing Rating and recreating model with 'Bikes Available'(dependent variable) and 'Distance' Independent variable
 5. removing the 'rating' variable results in a significant drop in the model's explanatory power, as reflected in the decrease in R-squared value.
 6. The overall model fit is notably weaker.
 
## Challenges 
 We Gathered Data from differenet APIs. in this process we faced many Challenges: 
 1. Foursquare's Details Demands: Required precise parameters for Points of Interest (POI), leading to potential  data limitations.
 2. Messy Foursquare Data:  Foursquare data had mixed null values, making data cleaning a critical step.
 3. Yelp's Request Restrictions: Yelp gave good info but limited how much we could ask, so we had to be careful.
 4. Choosing the Right Data: Picking between Foursquare and Yelp was tricky because of these challenges.
 5. Favoring Foursquare: Even though Yelp was more precise, we mainly used Foursquare due to its practicality and fewer restrictions.

## Future Goals

 if i have extra time, I'd gather more data from the API.
 The current model lacks depth as it has low accuracy in fitting, and I believe incorporating more variables would enhance its performance. This way, we can extract more meaningful insights.
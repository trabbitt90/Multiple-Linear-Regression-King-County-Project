![image.png](attachment:image.png)


# King County Housing Sale Price Analysis
By: Tim Rabbitt

 ## Overview

The housing market is booming and the demand to create more housing is higher than ever. I have been tasked by Kraken Construction, a new housing developer in King County, WA to assess the local housing market and identify the features that most influence home sale price.

**Stakeholder:**  Kraken Construction
    
**Business Problem:** Housing developers would like to build homes including features that will contribute to a higher sale price of the home.

**Business Question:** What features should you consider when building a new home that would ultimately lead to a higher sale price?

Performing multiple linear regression on past home sales can show how strong of a relationship there is between the sale price of a home and a particular feature. Knowing to what extent these features influence sale price can provide insight and confidence that your new construction will not only be a desirable build but one that will sell at a price you feel comfortable with.

## Data Understanding   

The project utilizes data from the King County House Sales dataset. This dataset was provided to us at the onset of analysis and contains home sale information from 2014 to 2015 in King County, WA.  This dataset contains 21,597 homes and 21 features, including:

* `id` - Unique identifier for a house
* `date` - Date house was sold
* `price` - Sale price (prediction target)
* `bedrooms` - Number of bedrooms
* `bathrooms` - Number of bathrooms
* `sqft_living` - Square footage of living space in the home
* `sqft_lot` - Square footage of the lot
* `floors` - Number of floors (levels) in house
* `waterfront` - Whether the house is on a waterfront
  * Includes Duwamish, Elliott Bay, Puget Sound, Lake Union, Ship Canal, Lake Washington, Lake Sammamish, other lake, and river/slough waterfronts
* `view` - Quality of view from house
  * Includes views of Mt. Rainier, Olympics, Cascades, Territorial, Seattle Skyline, Puget Sound, Lake Washington, Lake Sammamish, small lake / river / creek, and other
* `condition` - How good the overall condition of the house is. Related to maintenance of house.
* `grade` - Overall grade of the house. Related to the construction and design of the house.
* `sqft_above` - Square footage of house apart from basement
* `sqft_basement` - Square footage of the basement
* `yr_built` - Year when house was built
* `yr_renovated` - Year when house was renovated
* `zipcode` - ZIP Code used by the United States Postal Service
* `lat` - Latitude coordinate
* `long` - Longitude coordinate
* `sqft_living15` - The square footage of interior housing living space for the nearest 15 neighbors
* `sqft_lot15` - The square footage of the land lots of the nearest 15 neighbors

Further information on this dataset can be found at the [King County Assessor Website](https://info.kingcounty.gov/assessor/esales/Glossary.aspx?type=r) 

## Methods 
sWe imported the King County housing dataset that was provided to us for this project. We focused on features that can be included in a new construction, and removed those that applied to previously existing homes (ie. `condition`, `yr_built`, `yr_renovated`). We processed the data by removing outliers, filling/dropping Nan values, and converting object data types when necessary. We used visualizations to explore relationships within the dataset, eventually deciding to use the following features for use in our models:

* `bedrooms`
* `bathrooms`
* `sqft_living`
* `sqft_living15`
* `floors`
* `waterfront`
* `view` 
* `grade`
* `sqft_basement`
 
Using an iterative approach to our model building we created multiple linear regression models. We revisited the data on several occasions, creating dummy variables, performing log transformations, and dropping features in an attempt to improve model performance. 

## Results
In our final regression model using all of our selected features except `sqft_living` and `grade_8`, we saw an increase in model performance based on our R-squared value from 46.1 percent (baseline) to 57.4 percent (final). All model features had a p-value < 0.05 (our alpha/significance level), which tells us that all features have a statistically significant linear relationship with price. While we did not pass our normality assumption in our final model we did pass our independence, linearity, and homoscedasticity assumptions, which is good. Here are some observations from our chosen model:
 
* With each additional bathroom added you can increase the home sale price by 8,500 dollars.
* With each additional bedroom added you can increase the home sale price by 10,700 dollars.
* Homes on a waterfront see an increase in property value of 267,800 dollars.
* Homes that are considered to have a 'fair' view sell for 125,900 dollars more than those with no view.
* Homes that are considered to have an 'excellent' view sell for 221,900 dollars more than those with no view.
* With each additional floor added you can increase the home sale price by 32,000.
* Building grade and sqft_living had the strongest positive correlations with home sale price.

## Recommendations
1. Find an area to develop that has at least what is considered a 'fair' view. Homes built on these lots will see an increase in sale price of around 126,000 dollars.
2. Homes on a waterfront see a bigger increase in value than most other features. Building a house on a waterfront sees an increase in sale price of around 268,000 dollars. 
3. Do not cut costs on building materials, building grade is highly correlated to house sale price. Most houses are built with an "average" grade. Start building with at least a "better" grade to increase sale price.

## Limitations and Futher Analysis

Our model accurately fits only 57.4 percent of the data. While this is sufficient enough to make observations and insights, conclusions should be approached with caution. Additionally, a test for normality failed in our final model, which is one of the assumptions for linear regression. Further exploration into the normalization and scaling of features might help pass that assumption. Future analysis and modeling might want to consider a couple of items:

1. Find more recent home sales data to get a more accurate picture of today's market. Finding home sale information before 2014 would also help to create a more in-depth analysis.
2. Include additional features in future models. Particularly zipcode, sqft_living, and condition.

## For More Information
Please check out my Jupyter Notebook: https://github.com/trabbitt90/Multiple-Linear-Regression-King-County-Project/blob/main/Home%20Sale%20Regression%20Analysis.ipynb and Presentation: https://github.com/trabbitt90/Multiple-Linear-Regression-King-County-Project/blob/main/Presentation.pdf

## Navigating the Repository

README.md ---> Document for reviewers of the project

King-County-Housing-Sale-Price-Analysis.ipynb ---> Modeling and methods explaination in Jupyter Notebook

Presentation.pdf ---> PDF of presentation slides

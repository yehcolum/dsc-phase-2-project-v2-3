# Phase 2 Project 

## Overview

How can home-flippers and developers most effectively add value to their projects? This analysis seeks to find the variables with the most positive impact on sale price. The inferential regression model identifies adding bathrooms, increasing construction grade, and adding floors as the best ways to maximize sale price.

### Business Problem

Home flipping describes buying houses, adding value through remodels or other features, and selling for profit. To this end, this analysis seeks to give home flippers the best way to add value (maximize sale price) to their projects.

Statistically significant variables with the largest coefficients will be considered for our business recommendations.

### The Data

The Data:
* King County Housing data
* Includes 20 housing variables ranging from construction grade to zip code

Omitted irrelevant variables:
* `date`
* `view`
* `sqft_above`
* `sqft_basement`
* `yr_renovated`
* `zipcode`
* `lat`
* `long`
* `sqft_living15`
* `sqft_lot15`

Final continuous variables include:
Bedrooms, bathrooms, sqft_living, sqft_lot, yr_built 

Final categorical variables include:
condition, construction grade, waterfront, and number of floors

## Modeling and Results

Our model took on 3 iterations.

The first baseline model used sqft_living and price:


<img width="461" alt="Screen Shot 2022-01-19 at 1 51 07 PM" src="https://user-images.githubusercontent.com/87211473/150203582-9d433e40-5f50-4686-93dc-3889094fd612.png">

However, the model did not meet the assumptions of regression. The residuals were not normally distributed, and did not meet the Homoscedasticity requirement. More manipulation is needed.

The second iteration included our other variables. First, categorical variables were changed to dummy variables in order to properly model them. 
The second model ran as follows:

<img width="418" alt="Screen Shot 2022-01-19 at 1 55 14 PM" src="https://user-images.githubusercontent.com/87211473/150204225-d4fc20d0-39f3-41ea-b181-81fc563515cd.png">

This model achieved a higher r_squared, but continued to fail the assumptions of normal residuals and homoscedasticity. Transformation is needed.


### Model Refinement

Due to the larger errors for higher priced homes, removing outliers from the baseline model may improve model performance. Data points greater than 3 standard deviations away were removed from the model. 
Next, all the continuous variables including price were log transformed in an effort to meet the assumptions of normal residuals and homoscedasticity.

The refined model ran as follows:

<img width="427" alt="Screen Shot 2022-01-19 at 1 59 47 PM" src="https://user-images.githubusercontent.com/87211473/150204817-0b539ec8-713c-49d6-80e4-f8d028a669b6.png">

R_squared decreased, but the assumptions of normal residuals and homoscedasticity were met. 

## Final Model

While log transforming our continuous variables allowed our model to meet the assumptions of normality and homoscedasticity, transforming ALL continuous variables may not be necesary. In fact, stakeholders will better understand the interpretation of coefficients that have not been log transformed. To this end, I will undo the transformations of bedrooms, bathrooms, sqft_living, and yr_built. However price will maintain its log transformation.

The final iteration of our model ran as follows:

<img width="419" alt="Screen Shot 2022-01-19 at 2 03 25 PM" src="https://user-images.githubusercontent.com/87211473/150205304-e38070dd-eb5e-4bbe-9bee-c3dccb9823ae.png">

The model meets the assumptions of normal residuals and homoscedasticity. R_squared did not change, but our coefficients are now more easily interpretable.


## Recommendations

Circling back to how home-flippers can add value to their projects (maximize sale price), the model has identified the variables that provide the most positive impact on price. In accordance with the model's findings I recommend:

Add Bathrooms

According to the model, an increase in one bathroom results in 7.96% increase in sale price. Adding a bathroom is a practical, less capital-intensive strategy that produces a significant increase in sale price.

Increase construction grade to Excellent or Luxury. Do not decrease construction grade or risk losing significant value.

From a baseline of 10, achieving a construction grade of 11 'Excellent' increases sale price by 5.72%
Achieving a construction grade of 12 'Luxury' increases sale price by 11.76%.

In contrast decreasing construction grade consistently decreases sale price. In fact, a lowering of construction grade to 6 'Below Average' results in a 88.52% decrease in sale price. Overall, developers and home-flippers should build/remodel in accordance with high construction grade qualifications to increase value. They should also avoid downgrading their project's construction grade to prevent price decreases. High construction grade qualifications include (King Country Assessor):


-Custom design
-High quality finish
-Excellent builders
-Added amenities of solid woods, bathroom fixtures and more luxurious options.
-Materials of highest quality

Adding floors

From a baseline of 1 floor, adding 0.5 floors (1.5 floors total) results in a 4.64% increase in sale price.

Adding 1 floor (2.0 floors total) results in a 4.46% increase in sale price.

Adding 1.5 floors (2.5 floors total) results in a 8.64% increase in sale price.

Adding 2 floors (3 floors total) results in a 24.83% increase in sale price

Finally, adding 2.5 floors (3.5 floors total) results in 27.16% increase in sale price.

Overall, developers and home-flippers should add floors to raise the value of their projects. However, this strategy can be cost intensive, especially when adding more than one floor. That being said, achieving a height of 3 or 3.5 floors significantly increases sale price (24.83% and 27.16% increase respectively). If a flipper opts for a more intensive remodel, adding floors is a good strategy. For less intensive remodels, adding floors may not be as cost efficient as the flipper desires.


## Other Considerations

This inferential model eliminated outliers above 3 standard deviations of price. The model's errors, or "noise," were especially large for these higher priced homes. This may indicate that for the highest priced homes, different variables than the ones used in the model better explain price. Further analysis is recommended for pricing these homes.

Furthermore, the model identified the presence of a waterfront as the variable with the largest positive impact on price. However, home-flippers and developers are unable to create a waterfront, as being on the water is an innate feature that cannot be built in. Therefore the waterfront variable was omitted from our recommendations.


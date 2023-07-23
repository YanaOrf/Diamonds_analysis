# Analysis of the diamond dataset

## Introduction 
The goal of this analysis was to understand what  determines the price of a diamond and to build a model to predict a possible price based on the diamond's features.

## Data set overview
Dataset contains prices and other attributes of roughly 54,000 diamonds. Variables in the dataset are: 



|         |  Variable Explanation                                                                             |
|---------|---------------------------------------------------------------------------------------------------|
| price   | price in US dollars ($326–$18,823)                                                                |
| carat   | weight of the diamond (0.2–5.01)                                                                  |
| cut     | quality of the cut (Fair, Good, Very Good, Premium, Ideal)                                        |
| color   | diamond colour, from J (worst) to D (best)                                                        |
| clarity | a measurement of how clear the diamond is (I1 (worst), SI2, SI1, VS2, VS1, VVS2, VVS1, IF (best)) |
| x       | length in mm (0–10.74)                                                                            |
| y       | width in mm (0–58.9)                                                                              |
| z       | depth in mm (0–31.8)                                                                              |
| depth   | total depth percentage = z / mean(x, y) = 2 * z / (x + y) (43–79)                                 |
| table   | width of top of diamond relative to widest point (43–95)                                          |


## Data Preprocessing

During data cleaning were deleted 146 duplicates. 

The analysis of statistical indicators showed a high standard deviation relative to the mean value in the columns price and price per carat. 
The IQR was used to detect  Outlires. But further analysis showed that the high price variance was caused by a strong difference in diamond characteristics.  Therefore, I decided not to delete these values ​​so as not to lose the highest quality diamonds.


## EDA

[](blob:vscode-webview%3A//03sce1co20h8fdm8tbpq3i17kkuiulosetl5qq30j12gg3k63gon/df198e48-7725-4ce8-9cb0-ccc1eacccdc8)


When writing the grades of a diamond using the AGS Scale, diamond Cut grade is first, then diamond Color, Clarity, then Carat Weight—in that order.

## Predictive Modelling 

image.png


## Conclusions

a larger carat diamond will have a higher price than smaller carat diamonds of similar quality. But carat weight is not the only factor that influences a diamond’s price. In addition to its measurements along the diamond size chart, its carat weight and other features among the 4Cs will impact its price

Diamond prices per carat increase as you jump up to higher weight categories. In short, the higher the diamond’s carat weight, the higher the total amount you’ll need to pay per carat to purchase the diamond.



diamonds are treated to improve their appearance. Treated diamonds can be beautiful and come with a lower price tag than untreated diamonds of similar color and clarity. 

https://4cs.gia.edu/en-us/diamond-treatment/


### Ways to improve model
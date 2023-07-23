# Analysis of the diamond dataset

## Introduction 
The goal of this analysis was to understand what  determines the price of a diamond.

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
### Data Cleaning
During data cleaning were deleted 146 duplicates. 

The analysis of statistical indicators showed a high standard deviation relative to the mean value in the columns price and price per carat. 
The IQR was used to detect  Outlires. But further analysis showed that the high price variance was caused by a strong difference in diamond characteristics.  Therefore, I decided not to delete these values ​​so as not to lose the highest quality diamonds.

### Feature engineering
The following features were added to the dataset for further analysis:
* "Price per carat"   
* "Cut score" - from 0 to 3 (best to worst)
* "Color score" - from 0 to 3 (best to worst)
* "Clarity score" - from 0 to 3 (best to worst)
* "Diamond score" - was added to give a quantitative evaluation of the qualitative characteristics (cut,color,clarity) of diamonds. Based on [AGS Diamond Grading System](https://www.americangemsociety.org/buying-diamonds-with-confidence/ags-diamond-grading-system/#:~:text=When%20writing%20the%20grades%20of,0%2F0–1.000%20carat.)  

* "Carat label" - to group diamonds by number of carats  from small to large 
* "Price label" - to group diamonds by price per carat from low to extra high


## EDA

This dataset contains mostly low and very low mass diamonds (moda - 0.3 carats), high quality diamond cutting,  and  average color and clarity. 
![dist_ch](https://github.com/YanaOrf/Diamonds_analysis/blob/main/dist_characteristics.png)

Average prices per carat (3,000 to 10,000) also tend to prevail. 
Mode diamond_score 0.65
Median diamond_score 0.97
![dist_lables](https://github.com/YanaOrf/Diamonds_analysis/blob/main/dist.png)


Due to the predominant number of diamonds of low mass, the price mode of diamond is quite low - 605 usd.
The median price is 2401 usd. 
![price_dist](https://github.com/YanaOrf/Diamonds_analysis/blob/main/price_distribution.png)

Median price per carat is 3496 usd.
Mode preis per carat is 2250 usd.
![price_dist_carat](https://github.com/YanaOrf/Diamonds_analysis/blob/main/Price_per_carat_dis.png)



The biggest impact on the price of a diamond and the price per carat is the number of carats. The more carats, the more the diamond is worth. 
![corr_matrix](https://github.com/YanaOrf/Diamonds_analysis/blob/main/corr_matrix.png)

The carat weight of diamonds is also strongly positively correlated with the cost per carat.  In short, the higher the diamond’s carat weight, the higher the total price  need to be paied per carat to purchase the diamond. 
But the graph clearly shows that some of the diamonds with small carat weight have a higher price per carat than diamonds with large carat weight.
![price_effect](https://github.com/YanaOrf/Diamonds_analysis/blob/main/carat_price.png)


Сarat weight is not the only factor that influences a diamond’s price. The chart shows that large diamonds are cheaper per carat than small diamonds because their characteristics are significantly lower (The lower the Diamonds score, the better the quality)
![price_score](https://github.com/YanaOrf/Diamonds_analysis/blob/main/score_price.png)


If we take a closer look at the characteristics and prices per carat within the carat quantity groups XS - XL we can see that in the groups XS-M there are diamonds of all characteristics (from the lowest to the highest).

While in the high carat groups (4 carats and above) only diamonds with low color, cut and clarity are represented.
Therefore, the lack of data on high quality large diamonds skews the price per carat in favor of even high quality, but low carat weight diamonds.
![xs](https://github.com/YanaOrf/Diamonds_analysis/blob/main/price_features_carat.png)
![s](https://github.com/YanaOrf/Diamonds_analysis/blob/main/s.png)
![m](https://github.com/YanaOrf/Diamonds_analysis/blob/main/m.png)
![l](https://github.com/YanaOrf/Diamonds_analysis/blob/main/l.png)
![xl](https://github.com/YanaOrf/Diamonds_analysis/blob/main/XL.png)

## Conclusions

A larger carat diamond will have a higher price than smaller carat diamonds of similar quality. But carat weight is not the only factor that influences a diamond’s price. In addition, cut, color and clarity affect the price. 

Following information would help to improve the analysis: 
* on diamond [treatment](https://4cs.gia.edu/en-us/diamond-treatment/). Treated diamonds can be beautiful and come with a lower price tag than untreated diamonds of similar color and clarity. 
* on large, high-quality diamonds

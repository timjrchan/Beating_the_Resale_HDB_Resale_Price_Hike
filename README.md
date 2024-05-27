#  ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 2 - Singapore Housing Data and Kaggle Challenge

# Background

Anchoring bias affects home prices by setting a psychological benchmark that influences buyers’ and sellers’ expectations. Recent news articles such as [Straits Times](https://www.straitstimes.com/singapore/housing/hdb-resale-prices-rise-15-in-january-record-74-units-sold-for-at-least-1-million-each) affect people’s perceptions on prices of resale flats, causing overvaluation of subsequent future resale prices. With [13.4% of BTO Flats being sold within a year of MOP](https://stackedhomes.com/editorial/13-4-of-bto-flats-were-sold-within-a-year-of-mop/#gs.5s7x2y), most resale flat buyers will be looking to buy with little to no transaction history, and such benchmarks leads buyers into overpaying for their flat without substancial evidence backing the valuation. This results in penalties by HDB in the form of Cash over Valuation [(COV)](https://www.propertyguru.com.sg/property-guides/what-is-cov-and-how-it-affects-your-hdbs-appreciation-10332) which further impacts buyer financials and grows the possible housing bubble in Singapore.
[Source](https://www.channelnewsasia.com/singapore/record-high-hdb-resale-price-q3-2021-2215726)

---

# Problem Statement

How can we effectively assess a property’s value with factors other than flat transaction history?

---

# Data Dictionary of Engineered Features

|Feature|Type|Description|
|---|---|---|
|nearby_top_sch|int64|indicates if the resale unit is near a top primary school with a value of 1 else 0|
|prop_one_room|float64|proportion of one room flats in a block|
|prop_two_room|float64|proportion of two room flats in a block|
|prop_three_room|float64|proportion of three room flats in a block|
|prop_four_room|float64|proportion of four room flats in a block|
|prop_exec|float64|proportion of executive flats in a block|
|prop_multigen|float64|proportion of multi-generation flats in a block|
|prop_studio_apt|float64|proportion of studio apartments in a block|
|North South Line|int64|indicates if the resale unit has a mrt on the North-South line in the vicnity with a value of 1 else 0|
|North East Line|int64|indicates if the resale unit has a mrt on the North-East line in the vicnity with a value of 1 else 0|
|East West Line|int64|indicates if the resale unit has a mrt on the East-West line in the vicnity with a value of 1 else 0|
|Circle Line|int64|indicates if the resale unit has a mrt on the Circle line in the vicnity with a value of 1 else 0|
|Down Town Line|int64|indicates if the resale unit has a mrt on the Down Town line in the vicnity with a value of 1 else 0|
|Thomson East Coast Line|int64|indicates if the resale unit has a mrt on the Thomson East Coast Line in the vicnity with a value of 1 else 0|
|floor_density|int64|the number of flats in each floor|
|floor_category|int64|a value of 1 if situated on the lower floors, 2 for middle floors, 3 for upper floors|

Source: [nearby_top_sch](https://schlah.com/primary-schools)
---

# Summary of Analysis

### Exploratory Visualizations & Pre-processing

The following were observed:
Elaboration on findings

# Modeling

### Table Summary

| Baseline           | Baseline	    | Baseline	     | Base (LinearReg)      | Base (LinearReg)      | Ridge (L2)    | Ridge (L2)     | Lasso (L1)     | Lasso (L1)      | LinReg (SS)	|LinReg (SS)	|
|--------------------|-------------|-------------|--------------|-------------|--------------|-------------|--------------|-------------|--------------|-------------|
|                    |             |             |              |             |              |             |              |             |              |             |
| Parameters         | Train       | Test        | Train        | Test        | Train        | Test        | Train        | Test        | Train        | Test        |
| MSE                | 4931625665.83578 | 5019741304.30099 | 3120455883.87812 | 3131016127.04941 | 3120567243.97344 | 3131239005.84914 | 3114806570.06442 | 3130445674.84443 | 4931625665.83576 | 3131016127.04941 |
| RMSE               | 70225.534286581 | 70850.132704893 | 55861.040841342 | 55955.483440405 | 55862.037592389 | 55957.474977425 | 55810.452157857 | 55950.385832847 | 70225.534286581 | 55955.483440405 |
| R2                 | 0.759201595 | 0.758235677 | 0.847636287 | 0.849201792 | 0.847630849 | 0.849191058 | 0.847912128 | 0.849229267 | 1.0 | 0.849201792 |
| Adj R2             | 0.759181611 | 0.758155400 | 0.847573042 | 0.848951097 | 0.847567603 | 0.848940345 | 0.847840156 | 0.848943460 | 1.0 | 0.848951097 |
| CV score           | 0.759123859 | 0.758037392 | 0.847373907 | 0.848892172 | 0.847377330 | 0.848871297 | 0.847654178 | 0.848921731 | 1.0 | 0.848892658 |
| Intercept          | None |9650488.14971169 | None | 11544983.7985385 | None | 11594311.3395181 | None | 11593134.17892 | None  |449015.838599118 |

---

### Conclusions and Recommendations
The main drivers of resale prices are:
1. Flat Attributes;
2. Surrounding amenities;
3. Geographical Regions; and
4. Connectivity. 

## 1. Flat Attributes 
      Certain Flat models such as DBSS & Masionettes command higher prices due to their amenities such as swimming pools, sky gardens and security. However, it was noted that the number of resale transactions were highest for 4 room flats across all regions except central. In the central region, 3 room flats had the highest number of transactions. This could be due to the affordabilty as these flats were as expensive as 4 room flats in other regions.

      
## 2. Surrounding amenities
      The main amenities that we will focus on are Hawker Centre within 2km radiusm, Malls within 2km radius and top primary schools. 

      For Hawker Centres, we observed that there is a positive correlation and more hawker centres generally lead to a higher resale price.

      For Malls, we observed an upward trend for resale prices but this stopped at 15 malls. Prices were generally fluctuating around the same resale price for >15 Malls

      For Primary schools, we observed that Resale HDB units near top primary schools commanded higher prices consistently over 10 years.

## 3. Geographical Regions
      Flats located in certain towns are able to command a higher selling price due to their maturity and location within Singapore. As such, HDB units in East and Central regions tend to be higher due to their closer proximity to the central business district and key commercial areas.

      Central Region:
      Most number of top primary schools
      Central Business District
      Main Shopping District
      National attractions e.g. Sentosa, Marina Bay, National Stadium
      Highest train station/line density

      North-East Region:
      Some top primary schools
      Robust amenities and accessible to expressways
      Relatively close proximity to Airport
      High density of schools
      Outdoor activities e.g. Coney Island

      East Region:
      Some top primary schools
      Changi Business Park
      Water sports and activities
      Close proximity to Airport and Jewel

      West Region:
      One top primary schools
      Industrial Areas (Tuas Island and Mainland)
      2 Universities
      Army Training grounds

      North Region:
      Main Water Catchment area
      Mandai Wildlife Reserve
      Near to Causeway for a getaway


## 4. Connectivity
      MRT Stations have a large impact and areas that have more than 1 line or certain preferred lines tend to have higher valuation.

## 5. Recommendations
      For couples, it is recommended to prioritise connectiveity and region of stay. If planning for children, surrounding amenities and flat models could be more important.

      For Investors, it is recommended to prioritise Affordability and Region. Surrounding Industries and Rent could also be paid attention to.


---

### Files

-code  
      &emsp;01_EDA_and_Cleaning.ipynb   
      &emsp;02_Preprocessing_and_Feature_Engineering.ipynb   
      &emsp;03_Data_Visualizations.ipynb  
      &emsp;04_Model_Building_and_Tuning.ipynb  
      &emsp;05_Kaggle_Submission.ipynb  
-data
      &emsp;hdb_cleaned.csv  
      &emsp;hdb_cleaned2.csv  
      &emsp;hdb_no_dummy.csv  
      &emsp;kaggle_CRT.csv  
      &emsp;train.csv  
      &emsp;test.csv  
-images  
      &emsp;Linear_Regression_Coefficients.png  
      &emsp;images/Linear_Regression_Predicted_True_Values.png    
-Presentation.pdf  
-README.md  


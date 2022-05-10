![Header](https://github.com/cmhollman/Phase-3-Project/blob/main/Images/water_image.jpeg)



# Tanzania Waterpoint Classification

**Author**: [Chris Hollman](mailto:chollman91@gmail.com)

## Overview

The goal of this project is to build a machine learning model capable of classifying the functionality of water sources in Tanzania. The Ministry of Water is looking for insight as to where to focus resources in order to ensure that the populace has access to clean water. This model could help narrow down which areas need the most urgent help.
## Business Problem

The country of Tanzania is largely dependent on outside sources to maintain an adequate supply of drinking water. Due the the high variability in management, design, funding, and installation, it can be very difficult to keep track of which sources are in working order. It is imperative that the Tanzanian Ministry of Water maximizes it's available resources so ensure that as many people as possible don't lose access to this basic need.

## Data

The data for this project comes from one dataset which is included in this repository:
- data/training_set_labels.csv
- data/training_set_values.csv
This data contains information from over 59,000 waterpoints geographical data, pump type, water quality, funding and management information and construction. Many of these columns are redundant. The scale of the issue is apparent when looking at these two vizualizations: A map plotting "failed" waterpoints, and a bar chart depicting what percentage of the total water sources in a given region are categorized as non functional or in need of repair.
![Tanz_map](https://github.com/cmhollman/Phase-3-Project/blob/main/Images/Tanz_map.png)
![Fail_bar](https://github.com/cmhollman/Phase-3-Project/blob/main/Images/Failure_Bar.png)

## Methods

For this project we will apply three different classifications models in order to find which performs best when classifying our data. The key metrics will be overall accuracy as well as precision and recall for our target group (1).
## Results

We were able to build a Random Forest model which, when tuned can predict whether a water source is functional or not with 82% accuracy. Notably, the precision score for our target (accuracy when predicting that a well is non functioning) is 84% and the model is able to identify 75% of the total sources that are in need of repair. The precision and recall scores for functional sources are .80 and .88 respectively, which is also useful. Out model did produce 2058 'false positives' and 1197 'false negatives. The most useful predictors are a source being classified as dry, the GPS altitude of the site, the year it was constructed, the nearby population, and the waterpoint type being classified as 'other'

![Conf_mat](https://github.com/cmhollman/Phase-3-Project/blob/main/Images/conf_mat.png)
![Feat_imp](https://github.com/cmhollman/Phase-3-Project/blob/main/Images/feature_importance.png)



## Conclusions

This analysis leads to the following recommendations for the Ministry of Water

- **Accurate Record Keeping of Key Data.** This dataset was very messy and incomplete. Moving forward, focusing on accurate records of key predictors will increase model performance and reduce resource waste. 
- **Waterpoint Types.** Waterpoints categorized as "other" are the third most common classification group and that designation was among the 5 most important predictors for our final model. Identifying and properly categorizing these points will lead to a greater understanding of why that is, possibly highlighting some flawed design concepts. 

### Next Steps

Further analyses could provide more value to the Ministry of Water:

- **Cross Check GPS Height.** A large percentage of the GPS heights (our second most valuable predictor) were 0 values, which does not match up to the topography of Tanzania. Further model performance could be gained by using the lattitude and longitude data to obtain the correct values for these points.
- **Better Categorization of Funder/Installer Data.** While this will be time consuming, classifying these categories into cleaner, more meaningful groups could increase model performance and lead to insight as to which installers may tend to fail more than others. This can help inform future projects. 
- **Ranking Importance** A metric could be created to determine which of the flagged waterpoints should be addressed first. This is likely some combination of total static head, population nearby, and proximity to an alternative water source. 
## For More Information

See the full analysis in the [Jupyter Notebook](https://github.com/cmhollman/Phase-3-Project/blob/main/tanz_notebook.ipynb) 

or review this [presentation](https://github.com/cmhollman/Phase-3-Project/main/tanz_slides.pdf).

For additional info, contact Chris Hollman at [chollman91@gmail.com](mailto:chollman91@gmail.com)


## Repository Structure

```
├── Data
├── images
├── tanz_notebook.ipynb
├── tanz_slides.pdf
└── README.md

# NYC 2015 Street Tree Census
### Lisa Hwang
### February 3, 2020


### Repo Contents
- README.md
- Tree_Census.ipynb - Jupyter Notebook for modeling


### Objective
"Pick a dataset and do something with it."


### Background
This project was part of a one-day hackathon. We were instructed to "Pick a dataset and do something with it." Ideally, build a predictive model.

One of the recommended data sources was [Data is Plural](https://docs.google.com/spreadsheets/d/1wZhPLMCHKJvwOkP4juclhjFgqIY8fQFMemwKL2c64vk/edit#gid=0). Honestly, the biggest problem I had was simply figuring out which dataset to use! Many of them were really intriguing. However, after closer inspection, some of the datasets were not really ideal for modeling. For example, not having more than one variable.

I finally settled on working with the New York City 2015-2016 Street Tree Census dataset. The census recorded a total of 666,134 street trees on 131,488 blocks in New York City, with the help of city staffers and many volunteers.
- https://www.nycgovparks.org/trees/treescount
- https://data.cityofnewyork.us/Environment/2015-Street-Tree-Census-Tree-Data/uvpi-gqnh (download the dataset here)


### Problem Statement
Given the data in the street tree census, can we predict tree health?


### EDA
The census data originally consisted of 683,788 rows. For ```status```, I decided to focus on ```Alive``` trees due to limited data collected on ```Stump``` and ```Dead``` trees.

| Status of Trees | Number |
|--|--|
| Alive | 652,173 |
| Stump | 17,654 |
| Dead | 13,961 |

| Health of Alive Trees | Number |
|--|--|
| Good | 528,850 |
| Fair | 96,504 |
| Poor | 26,818 |

I created dummies for the types of trees and changed some column variables from string values to categorical values. Also, I removed all null rows from the datatset, leaving a total of 642,961 trees.


### Data Dictionary
The data dictionary can be found here: https://data.cityofnewyork.us/Environment/2015-Street-Tree-Census-Tree-Data/uvpi-gqnh


### Predictor Variables
In addition to the types of trees, the following variables were included in model building:

| Variable | Description from Dictionary |
|--|--|
|tree_dbh | Diameter of the tree, measured at approximately 54" / 137cm above the ground |
| curb_loc | Location of tree bed in relationship to the curb |
| steward | Indicates the number of unique signs of stewardship observed for this tree |
| guards | Indicates whether a guard is present, and if the user felt it was a helpful or harmful guard |
| sidewalk | Indicates whether one of the sidewalk flags immediately adjacent to the tree was damaged, cracked, or lifted |
| root_stone | Indicates the presence of a root problem caused by paving stones in tree bed |
| root_grate | Indicates the presence of a root problem caused by metal grates in tree bed |
| root_other | Indicates the presence of other root problems |
| trunk_wire | Indicates the presence of a trunk problem caused by wires or rope wrapped around the trunk |
| trnk_light | Indicates the presence of a trunk problem caused by lighting installed on the tree |
| trnk_other | Indicates the presence of other trunk problems |
| brch_light | Indicates the presence of a branch problem caused by lights (usually string lights) or wires in the branches |  
| brch_shoe | Indicates the presence of a branch problem caused by sneakers in the branches |
| brch_other | Indicates the presence of other branch problems |  
| postcode | Five-digit zipcode in which tree is located |
| community board | Community board in which tree point is located |  
| borocode | Code for borough in which tree point is located: 1 (Manhattan), 2 (Bronx), 3 (Brooklyn), 4 (Queens), 5 (Staten Island) |
| cncldist | Council district in which tree point is located |
| st_assem | State Assembly District in which tree point is located |
| st_senate | State Senate District in which tree point is located |
| boro_ct | This is the boro_ct identifyer for the census tract that the tree point falls into |
| latitude | Latitude of point, in decimal degrees |
| longitude | Longitude of point, in decimal degrees |
| x_sp | X coordinate, in state plane, in feet |
| y_sp | Y coordinate, in state plane, in feet |


### Modeling
The baseline accuracy is the majority class percentage, here good health. If I were to predict that all of the trees were in good health, I'd be correct **81.13%** of the time.

#### Logistic Regression
With logistic regression, I was not able to improve upon baseline accuracy.

Best testing accuracy: ```0.8114```

#### Random Forest
Since I had a tree dataset, of course random forests had to be considered as an option! There was overfitting in the first model but it was eliminated with the second after I adjusted a few hyperparameters. However, the accuracy did not significantly improve.

Best testing accuracy: ```0.8208```

#### Decision Tree
Like with the random forest, I was able to eliminate overfitting by modifying the hyperparameters, though the accuracy did not significantly improve.

Best testing accuracy: ```0.8122```


### Conclusions
For this hackathon-style project, unfortunately I wasn't able to noticeably improve upon baseline with my logistic regression, random forest, and decision tree models for predicting tree health in NYC. An imbalanced dataset certainly didn't help matters. Perhaps given more time, I could experiment with adding or removing certain variables to improve accuracy. This could be a future direction.

At any rate. it was still a great dataset to explore! And who wouldn't love using random forests and decision trees on a tree dataset?

# Mushrooms

I have this data set from Kaggle. For this reason, and for a better understanding of the data, I will also take over the rest of the description of [Kaggle](https://www.kaggle.com/uciml/mushroom-classification).

<img width="350" alt="portfolio_view" src="/images/Britannica_Mushroom_Pasture_Mushroom.jpg">

## Context
Although this dataset was originally contributed to the UCI Machine Learning repository nearly 30 years ago, mushroom hunting (otherwise known as "shrooming") is enjoying new peaks in popularity. Learn which features spell certain death and which are most palatable in this dataset of mushroom characteristics. And how certain can your model be?

## Content
This dataset includes descriptions of hypothetical samples corresponding to 23 species of gilled mushrooms in the Agaricus and Lepiota Family Mushroom drawn from The Audubon Society Field Guide to North American Mushrooms (1981). Each species is identified as definitely edible, definitely poisonous, or of unknown edibility and not recommended. This latter class was combined with the poisonous one. The Guide clearly states that there is no simple rule for determining the edibility of a mushroom; no rule like "leaflets three, let it be'' for Poisonous Oak and Ivy.

Time period: Donated to UCI ML 27 April 1987

## Inspiration
What types of machine learning models perform best on this dataset?

Which features are most indicative of a poisonous mushroom?

## Acknowledgements
This dataset was originally donated to the UCI Machine Learning repository. You can learn more about past research using the data [here](https://archive.ics.uci.edu/ml/datasets/Mushroom).

# The Project

After loading and a few simple edits of the data came the following steps:
* Exploratory Data Analysis
* Modelling
* Model comparison
* Conclusions
* References

## Exploratory Data Analysis
At the beginning of the

 ```
 plot_list <- list()

for(i in colNames){
plt <- ggplot(all, aes_string(x=i, fill = "class")) +
  geom_bar(stat="count",position=position_dodge()) +
   labs(
      title= i) +
   scale_x_discrete(name="")+
  theme(legend.position="none")

plot_list[[i]] <- plt
}
 ```
 
 With this loop and arrangeGrob function I was able to plot the following plots.
 
 <img width="750" alt="portfolio_view" src="/images/count.png">
 
Dueto the fact that not all variabels are good distrubuted for a train and test split I had to remove "gillattachment" and "veiltype". After I saw that none of the variables is able to split mushrooms clearly into edible and poisonous I started to model. 

## Modelling

Since the focus of this project is not on the optimization of the classification, I will implement it quickly and easily (it also saves a lot of time).

### Comparing the models
 It is possible to predict the poisonous and edible mushrooms with a high accuracy with each model. 

We were able to predict with very high accuracy the poisonous and edible mushrooms based on the three models used, Random Forest, Gradient Boosting Machine (GBM) and XGBoost. For the GBM and XGBoost models we were also using cross validation. The best prediction was obtained using Random Forest model.

<img width="750" alt="portfolio_view" src="/images/mushrooms.png">

Actually I thought that the gb and XGBoost model perform better than the RF but under the simple settings of the algorytmen, the Random Forest gives the best results. But once you adjust the settings of the Gradient Boosting models they should be just as good as the Random Forest (but they take longer).
A very interesting fact is that the different algorithms consider other variables as important. In this case, it was only a comparison of the ranking and not a direct comparison that mattered, so that the saklieren of the x axis plays a subordinate role.

For the boosters I also used crossvalidation, but with the struckture of the data this is relatively difficult. 

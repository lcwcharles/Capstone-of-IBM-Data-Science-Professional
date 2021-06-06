# Capstone-of-IBM-Data-Science-Professional
The capstone project of IBM Data Science Professional on the Coursera.
## Table of contents
* [1. Introduction](#Introduction)
 * [1.1 Description & Disscusion of the Background](#Description)
 * [1.2 Data Description](#Data)
* [2. Methodology](#Methodology)
* [3. Results](#Results)
* [4. Discussion](#Discussion) 
* [5. Conclusion](#Conclusion)
* [6. References](#References)

## 1. Introduction <a name="Introduction"></a>
### 1.1 Description & Discussion of the Background<a name="Description"></a>
  Singapore is a developed country, known as one of the "four little dragons of Asia". At the same time, with its geographical advantages, Singapore has become one of the important financial, service and shipping centers in Asia, and the fourth largest international financial center after London, New York and Hong Kong. Chinese make up about three-quarters of its population. With the rapid development of economy and the accelerated pace of life, more and more people are unwilling to spend their time cooking at home. Going out to a restaurant has become a choice, and Chinese restaurants attract these people's stomach with their rich and colorful cuisine and attractive taste. Opening a Chinese restaurant in Singapore is a good investment option.

  In this project, we try to find the best location to open a Chinese restaurant. Specifically, we will try to find areas with high population density and few Chinese restaurants. We will use data science to analyze and process the data we get, generate several subzones that deserve our attention most, and analyze and compare to get our best location.

  ### 1.2 Data Description <a name="Data"></a>
  According to the description of our problem, we need to know the population density of the subzones in Singapore and the distribution of Chinese restaurants.

  We can find out the population density of each subzone from <a href="https://www.citypopulation.de/en/singapore/admin/">here</a>.
  
  Use Foursquare API to get the number and location of Chinese restaurants around each subzone.
  
  <img src='image\data_example.png'>

  We will use K-means and supervised learning to solve the problem.

  ## 2. Methodology<a name="Methodology"></a>
  First, we get the name of each subzone and its population density.

Then use <code>geocode</code> to get the longitude and latitude of each subzone.

<img src='image\subzone_location.png'>

According to the longitude and latitude of each subzone, we use <code>Foursquare API</code> to get the information of Chinese restaurants that around each subzone. Use <code>Folium</code> to draw subzones and restaurants on the map.

<img src='image\venues_map.png'>

There are many areas that are not within Singapore's borders. We will delete these areas and rebuild map.

<img src='image\venues_map_new.png'>

Refine the data, because it's unwise to open a Chinese restaurant if the population nearby is too small. Here we screen out subzones with population density greater than 10000/km2.

Through k-means method, we cluster these data and create a scatter plot to show the relationship between population density and the number of Chinese restaurants.

Because the data sets are too few, the population density and the number of restaurants are too scattered, we divide these data equally in order to generate samples using machine learning. We choose the subzone with about 0 restaurants as our investment target area, and predict the number of restaurants through supervised learning.

Create a scatter diagram to show the relationship between the population density and the number of Chinese restaurants.

<img src='image\scatter.png'>

From the scatter above, we can see that the number of restaurants has no obvious relationship with population density.

<img src='image\bar_population_density.png'>
 
<img src='image\bar_restaurant_number.png'>

From the bars above, We found that there are a few subzones with a large number of restaurants, and a few subzones are just famous tourist destinations. We will exclude these subzones when modeling.

Use machine learning to predict subzones with very few restaurants.

## 3. Results<a name="Results"></a>
From the data we analyzed, the accuracy is about 0.4, which is not an ideal value. Compared with several machine learning methods, the data obtained by decision tree method shows that the number of restaurants in several areas is more.

<img src='image\predNumber.png'>

The results predicted by KNN, SVN, LR

<img src='image\others_predNumber.png'>

Four subzone most worthy of investment (marked in cyan)

<img src='image\pred_venues_map_new.png'>

## 4. Discussion<a name="Discussion"></a>
Our model is very simple and single. There are many uncertain factors, such as:

1. The distribution of subzones is uneven, and the search radius is limited, which make the number of restaurants controversial.

2. The number of people in each age group, the number of ethnic groups, and their eating habits. These need a source with enormous data to support us to explore.

3. Consumers' evaluation of each restaurant. To get the informations, we need a higher authority of <code>Foursquare API</code>.

## 5. Conclusion<a name="Methodology"></a>
As a result, Chinese restaurants abound in Singapore. It is a feasible investment plan to open a Chinese restaurant in Singapore. Through these data, investors can decide better their investment strategy and get profits as soon as possible.

##  6. References<a name="References"></a>
* <a href="https://www.citypopulation.de/en/singapore/admin/">Population Density Data of Singapore</a>
* <a href="https://developer.foursquare.com/">Foursquare API</a>
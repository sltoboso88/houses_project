README
================
Sandra Tobon
2020-06-19

<center>

# MEDIAN HOUSES VALUE WEST COAST USA

![](https://www.cockettgroup.com/PortsMapAssets/images/regions/countries/na-usaw.jpg)

</center>

## What is the data set about?

This data set is a fictional and is about the median house value in
diferrent areas around the West Coast in USA. This data set came from a
csv file and had 20640 rows and 10 columns. Those columns are:

  - Latitude  
  - Longitude  
  - Households age  
  - Total rooms  
  - Total bedrooms  
  - Population  
  - Households  
  - Median house income  
  - Median house value  
  - Ocean proximity

## Tools used in this project

  - **Language**: Python  
  - **Libraries**:
      - dfply  
      - pandas  
      - numpy  
      - pandas\_profiling  
      - seaborn  
      - plotnine  
      - statsmodel  
      - matplotlib  
      - sklearn  
      - scipy

## Clean Process

  - **Values Validation**: Some columns had some invalid values, for
    instance longitude had -1.000000e+18 as value, so we drop all the
    not valid values. Also other columns had valid values but followed
    by special characters as *?*, so we had removed those specials
    characters.

  - **Outliers**: The columns total\_rooms, total\_bedrooms, population,
    households, median\_house\_income and median\_house\_value had
    outliers, in this case because we had enough data, we just drop
    them.

  - **Missing Values**: The column total\_bedroom had 180 missing
    values, for filling them we found the mean of population per
    bedrooms (3), and the mean of population per rooms (5). For filling
    each missing value we made a ration between population per bedroom
    and rooms in each row.

  - **Cross validation**: In this case we only did one cross validation
    around the number of people per bedroom. In the west coast of USA
    the maximum number of people allow to live in a rent bedroom are 2,
    the mean of population per bedroom was 3, so we decide to drop all
    the rows with more than 6 persons per bedroom.

## Some useful plots from the data set:

  - The median\_house\_value, change a lot according to
    ocean\_proximity. The median\_house\_value in land is the lowest and
    the median\_house\_value is the highest in the islands.

<img src="images/ocean_proximity_house_value.png" width="408" />

  - The median\_house\_income change a lot between the house inland and
    the houses closer to the ocean or beach. But here is particulary
    interesting see how the median income in the houses located in the
    islands are very low even when they have the most expensive houses.
    The reason for this could be that in the island most of the
    population are retired and probably the normal income that they have
    isn’t very high.

<img src="images/ocean_proximity_median_income.png" width="387" />

## Model

In this case we decided to do a linear model, for this we standardize
all the variables so the comparation was easier. In the first moment we
only used the features than looked more relative with the
median\_houses\_value, as:

  - median\_income  
  - ocean\_proximity  
  - households\_median\_age  
  - total\_rooms

In the end we couldn’t find a very good model with only those features,
so we decided to do a model with all the features, but even with this we
couldn’t find a very good model with a good fit and spred residuals.

For the future we should try other model with the purpose of find a way
to predict the median house value.

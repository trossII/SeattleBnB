# SeattleBnB

## Business Problem

Since 2008, guests and hosts have used Airbnb to expand on traveling possibilities and present more unique, personalized way of experiencing the world. Ever thought about renting out your own home to put a little extra cash in your pocket but don't really know how much your home would be worth.



## Project Goal

This project is for the purpose of making it simple to get a prediction of what a new property in the Seattle area is worth. Returning a rental price that would allow the property to be successfull in the the competative Seattle rental market.

## Data Collection & Processing 

Data for this notebook was downloaded from Airbnb.

AirBnb Data: http://insideairbnb.com/get-the-data.html

The Data files I used were to big to be placed on Github. So to use the notebooks in this Repo you will need to create a Data Folder. Inside my Data folder I have folders that that specify which year the data pertains to and place the listings file in that folder. Furthermore when you download the files they will all download as listings.csv so I recommend renaming the files as listingsmmddyysum.csv or listingsmmddyylong.csv where mmddyy refers to the month, day and year the data is from, sum refering to if it is the summary version of the data and long refering to the detailed version.

The initial Data used was "Summary information and metrics for listings in Seattle (good for visualisations)" from the listings.csv file. But as I needed to dig deeper into the data to find correlations I moved onto using the full dataset provided under "Detailed Review Data for listings in Seattle", which is the listings.csv.gz file. I then began organizing these columns into features that the machine learning could use, by employing Natuaral Language Processing, Vectorizers and Scaling. In my current model the features I am using are:

'name': Allows the user to give a brief descripion of their home.
'host_is_superhost': An AirBnB Program that increases the visibility of your listing.
'neighbourhood_cleansed': The neighborhood where your property resides.
'neighbourhood_group_cleansed': The macro grouping that your neighborhood belongs to.
'latitude': Used to give the user a price more precise to their property.
'longitude': Same as above.
'room_type': Lets the user specify what exactly they are renting out.
'accommodates': How many people the user would like to limit using their property.
'bathrooms': How many bathrooms are available to guests.
'bedrooms': How many bedrooms are available to guests.
'beds': How many beds are available to guests. 
'cleaning_fee'?: An added fee to cover cleaning after guest leaves. *May remove or set to average for app due to model currently overfitting this feature*.
'minimum_nights': Set the minimum amount to nights the users will allow the guests to stay.
'number_of_reviews': Allows the user to determine a change in price if they have prior experience on their property.



## Building the Model

### FSM

The initial First Simple Model was build using linear regression, this model had a very small R2 score on the training data and a negative R2 score on the testing data. From there I moved onto more advanced models and ended up using a Random Forest Regressor. This first Random Forest performed much better than the FSM and had a positive R2 score around .3 on the testing data giving me hope and sending me back to reviewing my data that my model was learning from. 

### Clean up

Upon review of the data that I was using I realized some of my features needed a little cleaning. For starters some of the prices for the properties were 0 dollars and other properties had very bad overall review scores. So after removing some of these extreme outliers and unsuccessfull properties I returned to optimizing my model.

### Current Models

The final models I chose to optimize were the Random Forest Regressor that I had run at the beginning and a Neural Network. To optimize the Random Forest Regressor I used GridSearchCV to find the best hyperparameters, testing over 14 hyperparameters in 5 different categories. For the Neural Network I tried a variety of different techniques such and lengthening or widening the layers as well as limiting the learning with techniques such as Dropout.  


## Evaluation

The best scores I have attained so far come from the Random Forest Regressor model. I have reached an R2 of .89 on my training data which is showing me that the model is finding a pretty good correlation between my the features and the price, but shows that there is still information out there that my model is missing to better estimate the pricing. On the testing data my R2 drops down to around .65, meaning that while my model is finding a great correlation on the training data it might be overfitting on some of the features. Though compared to similar projects using AirBnb data such as New York Airbnb Open Data on Kaggle (https://www.kaggle.com/dgomonov/new-york-city-airbnb-open-data/kernels), it seems that this R2 score is where people max out using the supplied data. 

The Mean Absolute Error I am currently recieving on my model is 35 dollars which would be a huge deal to someone that is renting their house for a small amount but not for someone who is renting their house for hundreds of dollars. As I looked closer at this varience I have noticed that percentage wise I was off by about 30 percent and by graphing this I could see that this error was very right skewed and that most of the points were only off by less than 10 percent.

## Further Steps 

I need to further evaluate the predictions that my model is getting totally wrong and try to find a correlation between these properties to hopefully find what my model is missing in predicting the cost of these properties. I would also like to add additional features from outside sources and see if my model can find any correlation. These features would include things such as distance from attraction, image processing, greater neighborhood details.


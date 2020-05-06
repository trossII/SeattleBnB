# Business Understanding
This repository is to provide a daily price prediction for a BnB property that is quick and easy for the user to access. To provide this service I am trying to limit the amount of information the user would need to input to provide a prediction, then have the computer generate additional data and even offer some feedback to increase value based on there advertisement. 

# Modeling
To complete a successful model I am focusing on minimizing the percent difference between my predictions and the actual cost of successfull properties. I chose this metric instead of just minimizing difference in general, since the prices of properties vary so much that a 20 dollar difference would be totally different against a rental price of 75 dollars compared to a rental price of 300 dollar.

At first glance with the model predicting an average percent difference of .27 I did not want to claim that my model was ready to be deployed, but with a closer look at my data I see that it is skewed pretty far to the right, which shows me that most of my prices are actually predicting better than that 27 percent difference. Therefore I think this model is very useful for giving the user an idea of where to price their home to be sucessful.

# Conclusion
Currently the apllication of this model will be useful to the user to get a better understanding to base their final price off of if they are posting but ultimately the price of the property is up to the user since this project does not currently take in super detailed information such as aesthetics, age of appliances or other hosted benefits.

I will be continuing my goal to find a correlation between the properties that my model is missing to hopefully lower the average difference. As well as puting some final touches on my app that lets a user input their own data.
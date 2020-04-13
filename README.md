## A Look Into Touchdown Regression
Analysis article, Code Samples, and Data from [airyards](https://airyards.com/). This exercises investigates NFL receiving data to determine touchdown regression rate to equip fantasy football players with a simple, yet powerful, tool in making executive roster decsisions.


### Exploratory Data Analysis
First portion of this investigation was to explore the [airyads](https://airyards.com/) data and clean any null values. This step allows for accurate analysis and modeling. I combined years of data into a single dataframe and created a function to determine certain summary statistics. [airyards](https://airyards.com/) already has readily usable data and very few NaN specific variables. After using `fillna()`, the concatenated dataframe was ready for analysis.


### Receiving Yards to Touchdowns Correlation
Our datasets from airyards contains tight end and wide receiver specific data. We want to independtly explore each to determine positional dependent correlation.
+ Wide Receviver: the tight end data was excised. I grouped by each wide receiver to summate receiving yards and touchdowns to plot a correlation. I used [Seaborn](https://seaborn.pydata.org/generated/seaborn.lmplot.html) library for out visualization. From [Scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html), I ran a linear regression model that determined a strong R^2 value (**0.927**) between wide receiver receiving yards and receiving touchdown. I then determined the average amount of wide receiver receiving yards leads to one touchdown - **159 receving yards/touchdwon**.
+ Tight End: the wide recevier data was excised from the concatenated dataset. Repeated the above process to determine positional specific correlation; this was visualized, modeled and scored (R^2 = **0.881**), and the average tight end receiving yards to touchdown was calculated to be **129 receiving yards/touchdown**.


### Determining Touchdown Regression Rate

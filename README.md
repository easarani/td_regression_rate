## A Look Into Touchdown Regression
Analysis article, Code Samples, and [airyards](https://airyards.com/) Data. This exercise investigates 8 years worth of NFL receiving data to determine touchdown regression rate to equip fantasy football players with a simple, yet powerful, tool in making executive roster decsisions.


### Exploratory Data Analysis
Initially, I set to explore [airyads](https://airyards.com/) data and clean any null values. This step allows for accurate analysis and modeling. I combined years of data into a single dataframe and created a function to determine certain summary statistics. [airyards](https://airyards.com/) already has readily usable data and very few ***NaN*** specific variables. After using `fillna()`, the concatenated dataframe was ready for analysis.


### Receiving Yards-to-Touchdowns Correlation
Our dataframes contain tight end and wide receiver specific data. We want to independtly explore each to determine positional independent correlation.
+ Wide Receviver: the tight end data was excised. I grouped by each wide receiver to summate receiving yards and touchdowns to plot a correlation. I used [Seaborn's lmplot](https://seaborn.pydata.org/generated/seaborn.lmplot.html) for our visualization. From [Scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html), I ran a linear regression model that determined a strong R^2 value (**0.927**) between wide receiver receiving yards and receiving touchdowns. I then determined the average amount of wide receiver receiving yards that leads to one touchdown - **159 receving yards/touchdwon**.
+ Tight End: the wide recevier data was excised from the concatenated dataframe. Repeat the above process to determine positional specific correlation; this was visualized, modeled and scored (R^2 = **0.881**), and the average tight end receiving yards-to-touchdown was calculated to be **129 receiving yards/touchdown**.


### Determining Touchdown Regression Rate
Now that we know that receiving yards and tochdowns correlate, strongly, we can make a function to determine a player's touchdown regression rate. The average wide receiver scores a touchdown on approximately every 159 receiving yards. The average tight end scores a touchdown on approximately every 129 receiving yards. Let us build two functions:
+ The first function will take in two variables (a dataframe and a string) and return the correct postional sorted dataframe. The alloted string corresponds to the position we wish to investigate (WR or TE).
+ The second function will take in two variables (a dataframe and the corresponding positional ratio of receiving yards/TD). This function creates a column and calculates the touchdown regression rate for each player for a given year.
Negative and positive touchdown regression candidates can we visualized using [Seaborn's diverging pallette] (https://seaborn.pydata.org/generated/seaborn.diverging_palette.html). Understanding regression and that receiving yards correlate with touchdowns will equip fantasy football players with beneficial knowledge when making lineup moves and trades.

### Conclusion
Creating a regression function can help determine how many more touchdowns a wide receiver/tight end should have based off the averages of 8 years worth of receiving data used in this analysis. We can determine positive and negative regression candidates through this calculation. Having found a strong correlation between receiving yards and receiving touchdowns, we know that, on average, a receiver scores one touchdown on every 159 receiving yards and a tight end scores one touchdown on every 129 receiving yards. If a receiver is likely to get a similar amount of usage/work, it is fair to think that the positive touchdown candidates, for lack of a bettwe word, are "due" and should eventually score touchdowns, which aids in fantasy point accumulation. An important thing to keep in mind - a touchdown regression rate is ***NOT*** an overcorrection.

++ An example for future use: let us say that after week 4 of the 2020 season, JuJu Smith-Schuster has a touchdown regression rate of approx. -3. He would be considered a positive touchdown regression candidate. This value tells us that, based off his receiving yards, he is underperforming (as it relates to an average wide receiver) by 3 touchdowns. If he continues to get similar usage and produces similar yardage, he should begin to score touchdowns. It does not mean we should expect a 3 touchdown game in week 5 from JuJu. But that he should eventually regress to the mean and begin to start scoring touchdowns more to the average of 159 receiving yards per one touchdown.

Of course there are many factors that can drive touchdown success rate but, knowing the correlation of receiving yards to receiving touchdowns and knowing that touchdowns regress aids fantasy football owners in making executive decisions about their lineup.

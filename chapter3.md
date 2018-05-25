--- 
title       : "Confounders, Counterfactuals, and p-Hacking"
description : "This chapter will introduce you the important issues of confounders, counterfactuals, and the problem of p-hacking, and will let you learn and practice through R"
 

--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:5c37f21710
## Confounders
*** =video_link
//player.vimeo.com/video/230623543


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:ac9bc35c31
## Understanding Confounders
Why are confounding variables a potential problem?
*** =instructions
- Because treatment is not randomly assigned
- Because the control groups and treatment groups are not identical
- Because the treatment variable is correlated with an unobserved variable that might affect outcomes
- Because confounders are not observed
*** =sct
```{r}
msg1 = "The main reason we worry about confounders has to do with outcomes, not treatment assignment. Try again."
msg2 = "The main reason we worry about confounders has to do with outcomes, not our sampling technique. Try again."
msg3 = "Correct! Confounders are called *confounders* for a reason---because when they are present, we cannot distinguish the effect of treatment from the effect of the confounder. To learn causal effects, we want to compare people with treatment and people without treatment. If those two groups of people differ in their values of some potential confounding variable, then we can't tell if differences in outcomes are due to differences in treatment, or differences in the confounder."
msg4 = "Unobserved variables are not always a problem in causal inference, because they may not have any effect on outomes. Try again"
test_mc(correct = 3, feedback_msgs = c(msg1,msg2,msg3,msg4))
```

--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:6e830d0422
## Counterfactuals
*** =video_link
//player.vimeo.com/video/230623577


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:97e0c3c1ec
## Counterfactuals and You 
Suppose you hadn't watched this video just now, and weren't reading this question. Instead, you went outside and enjoyed the day with a stroll and ate an ice cream cone from a mysterious store. The ice cream cone was affected by a terrible curse, and you would have terrible luck for the rest of your life. But by taking this DataCamp course instead of eating that ice cream has literally saved you from this terrible curse. Right?
*** =instructions
- Yes
- I can't tell you either way
- No

*** =sct
```{r}
msg1 = "Oops! Think about the data you have about your world, and the data about the counterfactual that you don't have. Try again."
msg2 = "Correct! The question proposed a counterfactual world where not watching these modules ends in disaster for you, and thus the unit level causal effect of taking the course is to avoid this disaster. Well, you did watch this video and so we will never know what happened if you didn't. It's possible that such a disaster may have happened, but we just don't know. So while you may think this sounds a bit implausible, it can't be refuted with the data you directly observe."
msg3 = "Oops! Think about the data you have about your world, and the data about the counterfactual that you don't have. Try again."
test_mc(correct = 2, feedback_msgs = c(msg1,msg2,msg3))
```

--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:ddb24adc92
## Statistical Inference vs. Causal Inference
*** =video_link
//player.vimeo.com/video/230623833


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:11e02ba59d
## Big Data and Causal Inference 
If I have an enormous amount of data, do I still have to worry about causal inference?
*** =instructions
- It depends
- Yes
- No
*** =sct
```{r}
msg1 = "Correct. In some cases, we don't care about causality. For example, if we are trying to make predictions *in a stable environment* where we are *not* intervening to change policy, then often we don't have to worry about causal inference. A good example of this is weather forecasting. If you want to know what the weather in your town will be like next summer, your best prediction is probably going to just depend on the weather in the previous summers. But if you want to predict the weather next summer after implementing a nationwide cloud-seeding policy to increase the number of clouds on Earth in an effort to cool global temperatures, then you would want to understand the causal effects of treatments on the weather system than just relying on past data. For that difficult question, all the data on weather that exists might not be sufficient to answer your causal question."
msg2 = "If this were the case, education would confound the relationship between having and not having the death penalty. We would expect that states with the death penalty have higher underlying homicide rates of homicide, so whatever deterrent effect of the death penalty that we estimated would be smaller than the true deterrent effect. Try again."
msg3 = "Big Data does not solve all problems by magic! Depending on your data and your questions, you may need to worry about causal inference. Try again."
test_mc(correct = 1, feedback_msgs = c(msg1,msg2,msg3))
```


--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:a13b7c2ffd
## p Hacking and Talking to Ghosts
*** =video_link
//player.vimeo.com/video/230618095

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:b1da122e43
## Creating a Simple Counterfactual
Last year, a small town baseball team called The Hammers was hoping to attract bigger audiences to their home games, so halfway through their season they started a social media advertising campaign. Let’s see what we can find out if it worked through the data they collected.  

We will explore the data by tracking the behavior of just a single individual in the dataset. Let’s start with a table showing games attended and social media ads served for this individual for the 1st half of the season: 
|                            | April |  May  | June  | 
|----------------------------|------:|------:|------:|
|       Games Attended/Month |   0   |   1   |   2   |     
| Number of Ads Served/Month |   0   |   0   |   0   |  

Now let’s make a counterfactual: what do you think would happen if the ads had no affect at all on attendance? Based on the average number of games attended in the first 3 months, what would you use as a conservative counterfactual for average number of games attended in each month of the second half?

*** =instructions
- 0
- 1
- 2
- 3

*** =sct
```{r}
msg1 = "This person has already shown that they go to some games without ads, so it’s probably safe to assume they’ll go to at least one. Try again.”
msg2 = “Correct. This person has gone to 3 games in 3 months, so on average this person goes to 1 game per month. If you are optimistic, you could read this as a rising trend leading to either +1 game per month, or even 2x games per month, but let’s just stick with the average of 1 game per month for now”
msg3 = “This could be a safe guess if you think they’ll continue at their last count. But they’ve shown variability before, so it’s probably wise to back off this. Try again.”
msg4 = “This could be a safe guess if you think their attendance rate will keep increasing. But they’ve shown variability before, so it’s probably wise to back off this. Try again.”
test_mc(correct = 2, feedback_msgs = c(msg1,msg2,msg3,msg4))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:0ecec920ef
## Is Our Initial Data Enough?
Okay, let’s take a look at how many games this particular individual actually attended in July, the first month of the advertising campaign.

|                            | April |  May  | June  | July  |  Aug  | Sept  |
|----------------------------|------:|------:|------:|------:|------:|------:|
|       Games Attended/Month |   0   |   1   |   2   |   5   |       |       |  
| Number of Ads Served/Month |   0   |   0   |   0   |  72   |       |       |  

You compare the July results to your counterfactual of 1 game per month. Would you say the social media ads (our treatment variable) caused people to go to more games?

*** =instructions
- Yes, treatment had a positive effect on the outcome variable
- No, treatment had no effect.
- It's too soon to tell.

*** =sct
```{r}
msg1 = "Not yet! This is a form of p-hacking: stopping the experiment as soon as you get the result you were looking for. Try again!”
msg2 = “Not yet! This is a form of p-hacking: stopping the experiment as soon as you get any result. Try again!”
msg3 = “Correct! We want to let this experiment run throughout the rest of the advertising campaign, which will avoid the temptpation of stopping as soon as we get an answer that we like. That would be hacking our results!”
test_mc(correct = 3, feedback_msgs = c(msg1,msg2,msg3))
```



--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:2d4f173966
## Checking our Counterfactual
Since we know we need to look at the entire season to get the real causal answer, let’s take a look at how many games this individual actually attended during the entire advertising campaign.

|                            | April |  May  | June  | July  |  Aug  | Sept  |
|----------------------------|------:|------:|------:|------:|------:|------:|
|       Games Attended/Month |   0   |   1   |   2   |   5   |   4   |   0   |
| Number of Ads Served/Month |   0   |   0   |   0   |  72   |  157  |  71   |

You compare these numbers to your counterfactual of 1 game per month. Would you say the social media ads (our treatment variable) caused people to go to more games?

*** =instructions
- Yes, treatment had a positive effect on the outcome variable
- No, treatment had no effect.

*** =sct
```{r}
msg1 = "Yes, for now. On average, they attended 3 games per month during treatment, which is significantly more than before treatment. Now let’s look at the other available data to see if the situation is actually more complex than we thought.”
msg2 = “This may look like unconvincing and like it might be statistical noise, but we’re keeping it simple for now, so count up the average number of games attended per month during treatment and try again.”
test_mc(correct = 1, feedback_msgs = c(msg1,msg2))
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:4a0d3cf7b9
## Looking for Confounders with Positive Correlations
Now you look at the other variables that you have in the data that might affect this individual’s baseball game attendance. They are: Mean Daily High Temperature (in F and C), Quality of Stadium Food Consumed (scale 0-10), and National Ranking of Team (from 1-30).
Here is a table of all available data for this individual, with the months of the season along the top and variables down the side:


|                            | April |  May  | June  | July  |  Aug  | Sept  |
|----------------------------|------:|------:|------:|------:|------:|------:|
|       Games Attended/Month |   0   |   1   |   2   |   5   |   4   |   0   |
| Number of Ads Served/Month |   0   |   0   |   0   |  72   |  157  |  71   |
|   Mean Daily High Temp (F) |  56   |   66  |  77   |  86   |  75   |  65   |
|   Mean Daily High Temp (C) |  13   |   19  |  25   |  30   |  24   |  18   |
|    Quality of Stadium Food |   4   |   6   |   6   |   4   |   5   |   5   |
|      Nat’l Ranking of Team |  21   |  15   |  11   |   4   |   7   |  13   |


What variable looks like it is **positively** correlated with attendance?

*** =instructions
- Mean Daily High Temperature
- Quality of Stadium Food
- National Ranking of Team


*** =sct
```{r}
msg1 = "Correct! As attendance goes up, the temperature does too, so these are likely to be positively correlated”
msg2 = “The quality of stadium food seems hover around 5, so it doesn’t seem to vary significantly throughout the season. Try again.”
msg3 = “The team’s performance varies pretty significantly through the season, but that number goes down as the attendance goes up, so it’s not a positive correlation. Try again.”
test_mc(correct = 1, feedback_msgs = c(msg1,msg2,msg3))
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:c379b36151
## Looking for Confounders with Negative Correlations
Now that we’ve seen what other variables are positively correlated with attendance, what about the opposite?  Here’s the table again:

|                            | April |  May  | June  | July  |  Aug  | Sept  |
|----------------------------|------:|------:|------:|------:|------:|------:|
|       Games Attended/Month |   0   |   1   |   2   |   5   |   4   |   0   |
| Number of Ads Served/Month |   0   |   0   |   0   |  72   |  157  |  71   |
|   Mean Daily High Temp (F) |  56   |   66  |  77   |  86   |  75   |  65   |
|   Mean Daily High Temp (C) |  13   |   19  |  25   |  30   |  24   |  18   |
|    Quality of Stadium Food |   4   |   6   |   6   |   4   |   5   |   5   |
|      Nat’l Ranking of Team |  21   |  15   |  11   |   4   |   7   |  13   |


What variable looks like it is **negatively** correlated with attendance?

*** =instructions
- Mean Daily High Temperature
- Quality of Stadium Food
- National Ranking of Team


*** =sct
```{r}
msg1 = "As attendance goes up, the temperature does too, so these are likely to be positively correlated, not negatively correlated, so try again.”
msg2 = “The quality of stadium food seems hover around 5, so it doesn’t seem to vary significantly throughout the season. Try again.”
msg3 = “Correct! At first glance, the National Ranking of the team goes down as the attendance goes up, so it’s likely a negative correlation.”
test_mc(correct = 1, feedback_msgs = c(msg1,msg2,msg3))
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:23e5c17fe0
## Looking for Variables with No Correlations
Now that we’ve seen what other variables are positively and negatively correlated with attendance, are there any variables that are totally uncorrelated with attendance, and hence are not confounders?  Here’s the table again:

|                            | April |  May  | June  | July  |  Aug  | Sept  |
|----------------------------|------:|------:|------:|------:|------:|------:|
|       Games Attended/Month |   0   |   1   |   2   |   5   |   4   |   0   |
| Number of Ads Served/Month |   0   |   0   |   0   |  72   |  157  |  71   |
|   Mean Daily High Temp (F) |  56   |   66  |  77   |  86   |  75   |  65   |
|   Mean Daily High Temp (C) |  13   |   19  |  25   |  30   |  24   |  18   |
|    Quality of Stadium Food |   4   |   6   |   6   |   4   |   5   |   5   |
|      Nat’l Ranking of Team |  21   |  15   |  11   |   4   |   7   |  13   |


What variable looks like it is **uncorrelated** with attendance?

*** =instructions
- Mean Daily High Temperature
- Quality of Stadium Food
- National Ranking of Team


*** =sct
```{r}
msg1 = "As attendance goes up, the temperature does too, so these are likely to be positively correlated, not negatively correlated, so try again.”
msg2 = “Correct! The stadium food seems to be consistently mediocre, so it doesn’t seem to be connected to any of our other variables.”
msg3 = “The National Ranking of the team seems goes down as the attendance goes up, so it’s likely a negative correlation. Try again.”
test_mc(correct = 2, feedback_msgs = c(msg1,msg2,msg3))
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:d5098c9a23
## Do We Have Confounder Problems?
Let’s look again at the variables in our data that seem to be either positively or negatively correlated. Here’s the table again:

|                            | April |  May  | June  | July  |  Aug  | Sept  |
|----------------------------|------:|------:|------:|------:|------:|------:|
|       Games Attended/Month |   0   |   1   |   2   |   5   |   4   |   0   |
| Number of Ads Served/Month |   0   |   0   |   0   |  72   |  157  |  71   |
|   Mean Daily High Temp (F) |  56   |   66  |  77   |  86   |  75   |  65   |
|   Mean Daily High Temp (C) |  13   |   19  |  25   |  30   |  24   |  18   |
|      Nat’l Ranking of Team |  21   |  15   |  11   |   4   |   7   |  13   |

Would you say that the relationship between your treatment variable, Number of Ads Served per Month, and your outcome variable, Number of Games Attended per Month, is **confounded** by the other variables?

*** =instructions
- Yes
- No
- Maybe

*** =sct
```{r}
msg1 = "Yes, we seem to have confounder problems, which means that our attempts to find any causal effects of our treatment might be confused by other factors. That means we have to work a bit harder, and our answer might not be as clear as we’d like.”
msg2 = “”
msg3 = “”
test_mc(correct = 1, feedback_msgs = c(msg1,msg2,msg3))
```


#In case these become coding questions, some data generation!

***=pre_exercise_code
```{r}
#generate basic data
Month<-c("April", "May", "June", "July", "Aug", "Sept")
GamesAttendedPerMonth<-c(0,1,2,5,4,0)
NumberOfAdsServedPerMonth<-c(0,0,0,72,157,71)
MeanDailyHighTemp<-c(56,66,77,86,75,65)
QualityOfStadiumFoodConsumed<-c(4,6,6,4,5,5)
NationalRankingOfTeam<-c(21,15,11,3,7,73)

#generate dataframe of basic data called ‘Variables’
Variables<-data.frame(GamesAttendedPerMonth, NumberOfAdsServedPerMonth, MeanDailyHighTemp, QualityOfStadiumFoodConsumed, NationalRankingOfTeam)
Variables<-t(Variables)
colnames(Variables)<-c("April", "May", "June", "July", "Aug", "Sept")
row.names(Variables)<-c("GamesAttendedPerMonth","NumberOfAdsServedPerMonth","MeanDailyHighTemp", “QualityOfStadiumFoodConsumed","NationalRankingOfTeam")
Variables

#generate a table of the Variables with Month listed
AdvertisingResults<-data.frame(Variables, Month)
AdvertisingResults



|                            | April |  May  | June  | July  |  Aug  | Sept  |
|----------------------------|------:|------:|------:|------:|------:|------:|
|       Games Attended/Month |   0   |   1   |   2   |   5   |   4   |   0   |
| Number of Ads Served/Month |   0   |   0   |   0   |  72   |  157  |  71   |
|   Mean Daily High Temp (F) |  56   |   66  |  77   |  86   |  75   |  65   |
|   Mean Daily High Temp (C) |  13   |   19  |  25   |  30   |  24   |  18   |
|    Quality of Stadium Food |   4   |   6   |   6   |   4   |   5   |   5   |
|      Nat’l Ranking of Team |  21   |  15   |  11   |   4   |   7   |  13   |



#generate random daily high temperatures (in F)
MeanDailyHighTempApril<-sapply((rnorm(30,56,8)),as.integer)
MeanDailyHighTempMay<-sapply((rnorm(31,66,8)),as.integer)
MeanDailyHighTempJune<-sapply((rnorm(30,77,8)),as.integer)
MeanDailyHighTempJuly-sapply((rnorm(31,86,8)),as.integer)
MeanDailyHighTempAug<-sapply((rnorm(30,75,8)),as.integer)
MeanDailyHighTempSept<-sapply((rnorm(31,65,8)),as.integer)


#generate random count of games attended that match basic table
GamesAttendedAPerDayApril<-rbinom(14,1,0)
GamesAttendedMPerDayMay<-rbinom(13,1,0.07692307692)
GamesAttendedPerDayJune<-rbinom(14,1,0.14285714285)
GamesAttendedPerDayJuly<-rbinom(13,1, 0.38461538461)
GamesAttendedPerDayAug<-rbinom(14,1, 0.28571428571)
GamesAttendedPerDaySept<-rbinom(13,1,0)

#create function to generate random numbers that sum up to another number

rand_vect <- function(N, M, sd = 1, pos.only = TRUE) {
  vec <- rnorm(N, M/N, sd)
  if (abs(sum(vec)) < 0.01) vec <- vec + 1
  vec <- round(vec / sum(vec) * M)
  deviation <- M - sum(vec)
  for (. in seq_len(abs(deviation))) {
    vec[i] <- vec[i <- sample(N, 1)] + sign(deviation)
  }
  if (pos.only) while (any(vec < 0)) {
    negs <- vec < 0
    pos  <- vec > 0
    vec[negs][i] <- vec[negs][i <- sample(sum(negs), 1)] + 1
    vec[pos][i]  <- vec[pos ][i <- sample(sum(pos ), 1)] - 1
  }
  vec
}


#generate random daily team ranking 
NationalRankingOfTeamDailyApril<-sapply((rnorm(30,21,2)),as.integer)
NationalRankingOfTeamDailyMay<-sapply((rnorm(31,15,2)),as.integer)
NationalRankingOfTeamDailyJune<-sapply((rnorm(30,11,2)),as.integer)
NationalRankingOfTeamDailyJuly<-abs(sapply((rnorm(31,4)),as.integer))
NationalRankingOfTeamDailyAug<-sapply((rnorm(30,7,2)),as.integer)
NationalRankingOfTeamDailySept<-sapply((rnorm(31,13,2)),as.integer)

#new attendance figures with Men and Women 
|                            | April |  May  | June  | July  |  Aug  | Sept  |
|----------------------------|------:|------:|------:|------:|------:|------:|
|   Average Attendance/Month | 4378  | 6099  | 7744  | 9343  | 9569  | 8785  |
| Avg Count Ads Served/Month |   0   |   0   |   0   |  72   |  157  |  71   |
|    Avg Attendance(M)/Month | 2188  | 3064  | 3881  | 4675  | 4791  | 4384  |
|    Avg Attendance(W)/Month | 2190  | 3035  | 3863  | 4676  | 4788  | 4399  |

#average monthly attendance of treatment + control for women
MeanAttendanceMonthlyWomenApril<-1106+1084
MeanAttendanceMonthlyWomenMay<-1523+1512
MeanAttendanceMonthlyWomenJune<-1920+1943
MeanAttendanceMonthlyWomenJuly<-2366+2311
MeanAttendanceMonthlyWomenAug<-2399+2342
MeanAttendanceMonthlyWomenSept<-2229+2170

#average monthly attendance of treatment + control for men
MeanAttendanceMonthlyMenApril<-1098+1090
MeanAttendanceMonthlyMenMay<-1528+1536
MeanAttendanceMonthlyMenJune<-1941+1940
MeanAttendanceMonthlyMenJuly<-2374+2301
MeanAttendanceMonthlyMenAug<-2438+2353
MeanAttendanceMonthlyMenSept<-2241+2149


#average attendance per game of treatment group for women
AttendancePerGameTreatmentWomenApril<-sapply((rnorm(14,1106,20)),as.integer)
AttendancePerGameTreatmentWomenMay<-sapply((rnorm(13,1523,20)),as.integer)
AttendancePerGameTreatmentWomenJune<-sapply((rnorm(14,1920,20)),as.integer)
AttendancePerGameTreatmentWomenJuly<-sapply((rnorm(13,2366,20)),as.integer)
AttendancePerGameTreatmentWomenAug<-sapply((rnorm(14,2399,20)),as.integer)
AttendancePerGameTreatmentWomenSept<-sapply((rnorm(13,2229,20)),as.integer)

#average attendance per game of control group for women
AttendancePerGameControlWomenApril<-sapply((rnorm(14,1084,20)),as.integer)
AttendancePerGameControlWomenMay<-sapply((rnorm(13,1512,20)),as.integer)
AttendancePerGameControlWomenJune<-sapply((rnorm(14,1943,20)),as.integer)
AttendancePerGameControlWomenJuly<-sapply((rnorm(13,2311,20)),as.integer)
AttendancePerGameControlWomenAug<-sapply((rnorm(14,2342,20)),as.integer)
AttendancePerGameControlWomenSept<-sapply((rnorm(13,2170,20)),as.integer)

#average attendance per game of treatment group for men
AttendancePerGameTreatmentMenApril<-sapply((rnorm(14,1098,20)),as.integer)
AttendancePerGameTreatmentMenMay<-sapply((rnorm(13,1528,20)),as.integer)
AttendancePerGameTreatmentMenJune<-sapply((rnorm(14,1941,20)),as.integer)
AttendancePerGameTreatmentMenJuly<-sapply((rnorm(13,2374,20)),as.integer)
AttendancePerGameTreatmentMenAug<-sapply((rnorm(14,2438,20)),as.integer)
AttendancePerGameTreatmentMenJuly<-sapply((rnorm(13,2241,20)),as.integer)

#average attendance per game of control group for men
AttendancePerGameControlMenApril<-sapply((rnorm(14,1090,20)),as.integer)
AttendancePerGameControlMenMay<-sapply((rnorm(13,1536,20)),as.integer)
AttendancePerGameMenJune<-sapply((rnorm(14,1090,20)),as.integer)
AttendancePerGameControlMenJuly<-sapply((rnorm(13,2301,20)),as.integer)
AttendancePerGameControlMenAug<-sapply((rnorm(14,2353,20)),as.integer)
AttendancePerGameControlMenJuly<-sapply((rnorm(13,2149,20)),as.integer)

#generate random number of ads served daily each month
MeanNumberDailyAdsServedPerPersonJuly<-rand_vect(30,70)
MeanNumberDailyAdsServedPerPersonAug<-rand_vect(31,160)
MeanNumberDailyAdsServedPerPersonSept<-rand_vect(rnorm(30,70)



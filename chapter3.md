--- 
title       : "Confounders, Counterfactuals, and p-Hacking"
description : "This chapter will introduce you the important issues of confounders, counterfactuals, and the problem of p-hacking, and will let you learn and practice through R"
 

--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:5c37f21710
## Confounders
*** =video_link
//player.vimeo.com/video/230623543


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:ac9bc35c31
## Understanding Confounders
Why are confounding variables a potential problem for causal inference?
*** =instructions
- Because confounding variables prevent the treatment from being randomly assigned
- Because the treatment variable is correlated with an unobserved variable that might affect outcomes
- Because confounders are not observed
*** =sct
```{r}
msg1 = "Almost, but remember, the main reason we worry about confounders has to do with effects on the outcome, not on treatment assignment. Try again."
msg2 = "Correct! Confounders are called *confounders* for a reason---because when they are present, we cannot distinguish the effect of treatment from the effect of the confounder. To learn causal effects, we want to compare people with treatment and people without treatment. If those two groups of people differ in their values of some potential confounding variable, then we can't tell if differences in outcomes are due to differences in treatment, or differences in the confounder."
msg3 = "Unobserved variables are not always a problem in causal inference, because they may not have any effect on outomes. Try again"
test_mc(correct = 3, feedback_msgs = c(msg1,msg2,msg3))
```

--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:6e830d0422
## Counterfactuals
*** =video_link
//player.vimeo.com/video/230623577


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:97e0c3c1ec
## Counterfactuals and You 
Suppose this was the best DataCamp course ever, and over the course of the past hour, we delivered a cup of ice cream to every DataCamp user's front door. We surveyed our participants, and found out that half of them decided to eat our free ice cream. Can we be certain that providing this free ice cream increased the amount of ice cream that each user would have eaten today if we hadn't provided any free ice cream? 

*** =instructions
- Yes
- No

*** =sct
```{r}
msg1 = "Oops! Think about the data we provided you. Is this really enough to make that conclusion? Try again."
msg2 = "Correct! The question proposed an experiment and an outcome, but we do not know the counterfactual. While it seems likely that having access to free ice cream would increase our users ice cream consumption, there is no way to know for certain that they would not have eaten ice cream otherwise. For example, maybe some of our user's would have eaten ice cream anyway, or decided to eat more ice cream than what we provided to them. Maybe some users were going to eat ice cream, but changed their mind after seeing a melted scoop of ice cream on their door steps. In sum, the null hypothesis cannot be refuted without knowing the counterfactual."
test_mc(correct = 2, feedback_msgs = c(msg1,msg2))
```

--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:ddb24adc92
## Statistical Inference vs. Causal Inference
*** =video_link
//player.vimeo.com/video/230623833


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:11e02ba59d
## Big Data and Statistical Inference 
If I have an enormous amount of data, do I still have to worry about causal inference?
*** =instructions
- Yes
- No
*** =sct
```{r}
msg1 = "Correct. Big data might give you more power to make statistical inferences with your data, but all statistics still need to be interpreted carefully in order to make any causal inferences about the patterns you see."
msg2 = "Big Data does not solve all problems by magic! No matter the size of your data, you will always need to think about how to interpret your results. Try again."
test_mc(correct = 1, feedback_msgs = c(msg1,msg2))
```


--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:a13b7c2ffd
## p Hacking and Talking to Ghosts
*** =video_link
//player.vimeo.com/video/230618095

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:b1da122e43
## Determining a Reasonable Counterfactual
Last year, a small town baseball team called The Hammers was hoping to attract bigger audiences to their home games, so halfway through their season they started a social media advertising campaign. Let’s see how well it worked.

Below is a table tracking the games attended per month of just a single individual who was exposed to the advertising campaign: 
|                            | April |  May  | June  | July  |  Aug  | Sept  |
|----------------------------|------:|------:|------:|------:|------:|------:|
|       Games Attended/Month |   0   |   1   |   2   |   5   |   4   |   5   |  
| Number of Ads Served/Month |   0   |   0   |   0   |   7   |   8   |   6   |  

It appears that being exposed to ads was associated with going to baseball games for this individual. If we assumed that the individual went to more baseball games in the latter months only because of the ad campaign, how many games per month do you think the individual would have gone to if he were not exposed to ads in the second three months? In other words, based on the average number of games attended in the first 3 months, what would you use as a conservative counterfactual for average number of games attended in each month of the second half?

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
## Interpreting our Data
Let’s take another look at how many games this particular individual attended during the baseball season.

|                            | April |  May  | June  | July  |  Aug  | Sept  |
|----------------------------|------:|------:|------:|------:|------:|------:|
|       Games Attended/Month |   0   |   1   |   2   |   5   |   4   |   5   |  
| Number of Ads Served/Month |   0   |   0   |   0   |   7   |   8   |   6   |  

Since the number of baseball games that this individual went to appears to be associated with how many ads he was served, can we conclude that the advertising campaign caused the individual to go to more games?

*** =instructions
- Yes, the treatment had a positive effect on the outcome variable
- No, the treatment had no effect.
- It's too soon to tell.

*** =sct
```{r}
msg1 = 'Not yet! We do not know whether the difference in games attended after being exposed to the ad-campaign was statistically significant, nor do we have a sense for what the counterfactual would be (i.e. maybe he would have gone to more games anyway)'
msg2 = 'Not yet! We do not know whether the difference in games attended after being exposed to the ad-campaign was statistically significant, nor do we have a sense for what the counterfactual would be (i.e. maybe he would have gone to more games anyway)'
msg3 = “Correct! We want to let this experiment run throughout the rest of the advertising campaign, which will avoid the temptation of stopping as soon as we get an answer that we like. That would be hacking our results!”
test_mc(correct = 3, feedback_msgs = c(msg1,msg2,msg3))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:4a0d3cf7b9
## Looking for Confounders with Positive Correlations
Let's look at some other variables that might affect this individual’s baseball game attendance. We gather information on the Mean Daily High Temperature, and National Ranking of Team (from 1-30). Here is our updated table:

|                            | April |  May  | June  | July  |  Aug  | Sept  |
|----------------------------|------:|------:|------:|------:|------:|------:|
|       Games Attended/Month |   0   |   1   |   2   |   5   |   4   |   5   |
| Number of Ads Served/Month |   0   |   0   |   0   |   7   |   8   |   6   |
|   Mean Daily High Temp (F) |  56   |   66  |  77   |  86   |  75   |  65   |
|    Nat’l Ranking of Team   |  21   |   15  |  11   |   4   |   7   |  13   |


We inserted this table into the R workspace What variable looks like it is **positively** correlated with attendance?

*** =instructions
- Mean Daily High Temperature
- Quality of Stadium Food
- National Ranking of Team


*** =sct
```{r}
msg1 = 'Correct! As attendance goes up, the temperature does too, so these are likely to be positively correlated”'
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
#there are home games about half of the days each month, so that count is either 13 and 14
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


#ad company creates campaign for second haf of season. The MC is just looking at one person. But do they work overall. Here's a more statistically valid way. Explore the data a bit. Then compare means/CATEs. Did the ads work. Are they confounded.

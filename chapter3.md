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
- Because confounding variables might alter the association between the treatment and dependent variable
- Because confounders are not observed
*** =sct
```{r}
msg1 = "Almost, but remember, the main reason we worry about confounders has to do with effects on the outcome, not on treatment assignment. Try again."
msg2 = "Correct! Confounders are called *confounders* for a reason---because when they are present, we cannot distinguish the effect of treatment from the effect of the confounder. To learn causal effects, we want to compare people with treatment and people without treatment. If those two groups of people differ in their values of some potential confounding variable, then we can't tell if differences in outcomes are due to differences in treatment, or differences in the confounder."
msg3 = "Unobserved variables are not always a problem in causal inference, because they may not have any effect on outomes. Try again"
test_mc(correct = 2, feedback_msgs = c(msg1,msg2,msg3))
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
Last year, a small town baseball team called The Hammers was hoping to attract bigger audiences to their home games, so halfway through their season they started a social media advertising campaign. Let’s see how well it worked and explore the data by looking at the behaviour of just one individual.

To find a causal effect, we need to develop a counterfactual. So let's see if our subject went to any baseball games before they saw the ads. Below is a table tracking the games attended per month and the number of ads served per month for our initial subject: 

| Month    |Attended|Ads Served|
|----------|-------:|---------:|
| April    |   0    |    0     |
| May      |   1    |    0     |
| June     |   2    |    0     |
| July     |   -    |    -     |
| August   |   -    |    -     |
| September|   -    |    -     |

Based on the average number of games attended per month in the first 3 months, what would you use as a conservative counterfactual for average number of games attended per month in the second 3 months?

*** =instructions
- 0
- 1
- 2
- 3

*** =sct
```{r}
msg1 = "This person has already shown that they go to some games without ads, so it’s probably safe to assume they’ll go to at least one. Try again."
msg2 = "Correct. This person has gone to 3 games in 3 months, so on average this person goes to 1 game per month. If you are optimistic, you could read this as a rising trend leading to either +1 game per month, or even 2x games per month, but let’s just stick with the average of 1 game per month for now"
msg3 = "This could be a safe guess if you think they’ll continue at their last count. But they’ve shown variability before, so it’s probably wise to back off this. Try again."
msg4 = "This could be a safe guess if you think their attendance rate will keep increasing. But they’ve shown variability before, so it’s probably wise to back off this. Try again."
test_mc(correct = 2, feedback_msgs = c(msg1,msg2,msg3,msg4))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:0ecec920ef
## Looking at the results of the first month
Let’s see what happened in the first month of the ad campaign for our individual fan. Take a look at the following table:

| Month    |Attended|Ads Served|
|----------|-------:|---------:|
| April    |   0    |    0     |
| May      |   1    |    0     |
| June     |   2    |    0     |
| July     |   7    |    5     |
| August   |   -    |    -     |
| September|   -    |    -     |

Since the number of baseball games that this individual went to appears to increase after viewing 5 ads, can we conclude that the advertising campaign caused the individual to go to more games?

*** =instructions
- Yes, the treatment had a positive effect on the outcome variable.
- No, the treatment had no effect.
- It's too early to tell.

*** =sct
```{r}
msg1 = "Not yet! We do not know whether the difference in games attended after being exposed to the ad-campaign was statistically significant, nor do we have a sense for any potential confounding variables"
msg2 = "Not yet! We do not know whether the difference in games attended after being exposed to the ad-campaign was statistically significant, nor do we have a sense for any potential confounding variables"
msg3 = "Correct! Stopping this analysis just because we like the results in the first month would be hacking our results. This month could just be due to confounders. We should let the ad campaign run for the whole season to get a better conclusion"
test_mc(correct = 3, feedback_msgs = c(msg1,msg2,msg3))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:4a0d3cf7b9
## Looking for Confounders with Positive Correlations
Let's look at the full season's attendance figures for our sample individual, as well as some other variables that might affect this individual’s baseball game attendance. As you'll see, their attendance does seem to be positively correlated with the ad campaign:

| Month    |Attended|Ads Served|
|----------|-------:|---------:|
| April    |   0    |    0     |
| May      |   1    |    0     |
| June     |   2    |    0     |
| July     |   7    |    5     |
| August   |   8    |    4     |
| September|   6    |    5     |

But we think there could be confounders at work, so let's add information on the Mean Daily High Temperature, and National Ranking of Team (from 1-30). Here is our updated table:

| Month    |Attended|Ads Served|Temp(F)|Ranking|
|----------|-------:|---------:|------:|------:|
| April    |   0    |    0     |   56  |  21   |
| May      |   1    |    0     |   66  |  15   |
| June     |   2    |    0     |   77  |  11   |
| July     |   7    |    5     |   86  |   4   |
| August   |   8    |    4     |   81  |   7   |
| September|   6    |    5     |   70  |  13   |

Which of the following variables look **positively** correlated with attendance?

*** =instructions
- Mean Daily High Temperature
- National Ranking of Team

*** =sct
```{r}
msg1 = "Correct! As attendance goes up, the temperature does too, so these are likely to be positively correlated"
msg2 = "The team’s performance varies pretty significantly through the season, but that number goes down as the attendance goes up, so it’s not a positive correlation. Try again."
test_mc(correct = 1, feedback_msgs = c(msg1,msg2))
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:c379b36151
## Looking for Confounders with Negative Correlations
Now that we’ve seen what other variables are positively correlated with attendance, what about the opposite?  Here’s the table again:

| Month    |Attended|Ads Served|Temp(F)|Ranking|
|----------|-------:|---------:|------:|------:|
| April    |   0    |   0      |   56  |  21   |
| May      |   1    |   0      |   66  |  15   |
| June     |   2    |   0      |   77  |  11   |
| July     |   7    |   5      |   86  |   4   |
| August   |   8    |   4      |   81  |   7   |
| September|   6    |   5      |   70  |  13   |

What variable looks like it is **negatively** correlated with attendance?

*** =instructions
- Mean Daily High Temperature
- National Ranking of Team

*** =sct
```{r}
msg1 = "As attendance goes up, the temperature does too, so these are likely to be positively correlated, not negatively correlated, so try again."
msg2 = "Correct! At first glance, the National Ranking of the team goes down as the attendance goes up, so it’s likely a negative correlation. Note that this wording is sort of tricky because a `lower` ranking implies that a team is performing `better`, whereas `negative` is often used colloquially to mean something is `worse`."
test_mc(correct = 2, feedback_msgs = c(msg1,msg2))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:d5098c9a23
## Do We Have Confounder Problems?
We found that temperature and team ranking are also associated with how frequently this individual attends baseball games. Is it likely that the the relationship between your treatment variable, Number of Ads Served per Month, and your outcome variable, Number of Games Attended per Month, are **confounded** by these two other variables?

*** =instructions
- Yes
- No

*** =sct
```{r}
msg1 = "Yes, we seem to have confounder problems, which means that our attempts to find any causal effects of our treatment might be confused by other factors. That means we have to work a bit harder, and our answer might not be as clear as we’d like."
msg2 = "Try Again"
test_mc(correct = 1, feedback_msgs = c(msg1,msg2))
```

--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:384a8c2308
## Let’s Code: A Bigger Sample Size for the Ad Campaign
*** =video_link
//player.vimeo.com/video/276320373


--- type:NormalExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:1b191b5c59
## Homerun Ad Campaign I - Exploring Data
This series of question will test your knowledge on what we have learned so far, and will introduce some new functions.

The Hammers decided to expand their sample to examine how effective their social media campaign was. They collected more information on how many games each individual attended per month, as well as how many ads they were served to each individual per month. In the following questions, let's find out whether these correlations still hold. To begin, let's first get acquainted with the provided dataframe, `Baseball`:

*** =instructions
- 1) Look at the first few rows of dataframe, `Baseball` with function `head`.
- 2) Identify how many observations (`rows`) are in dataframe, `Baseball` with function `nrow`.
- 3) Identify how many unique individuals (`id`) were sampled in dataframe, `Baseball` with functions `length` and `unique`.

*** =pre_exercise_code
```{r}
library(dplyr)
n=62
set.seed(1)
#Create rnorm function that allows for min and max
  rtnorm <- function(n, mean, sd, min = -Inf, max = Inf){
      qnorm(runif(n, pnorm(min, mean, sd), pnorm(max, mean, sd)), mean, sd)
  }
#Create rounding function that allows to round to numbers above 1
  mround <- function(x,base){
          base*round(x/base)
  }
#Create scaling function that puts number between 0 and 1
  scale <- function(x){
    (x - min(x))/(max(x)-min(x))
  }
#Dataframe
  Baseball<-data.frame(id=rep(1:n,each=6))
  Baseball$month=rep(1:6,n)
  Baseball$ads.served=ifelse(Baseball$month<4,round(rtnorm(n=n,mean=1,sd=.5,min=0,max=3)),round(rtnorm(n=n,mean=5,sd=3,min=1,max=12)))
  Baseball$temp<-rep(c(56,66,77,86,81,70),n)
  Baseball$ranking<-rep(c(21,15,11,4,7,13),n)
  Baseball$attended<-round(
                    rtnorm(n=n,mean=3,sd=1.5,min=0,max=6)+
                    .3*Baseball$ads.served+
                    .0006*Baseball$temp^2+
                    -.2*Baseball$ranking
                    )
  Baseball$attended[Baseball$attended<0]<-0
  Baseball$month=rep(c("April","May","June","July","August","September"),n)
  Baseball<-Baseball[,c("id","month","attended","ads.served","temp","ranking")]
#Adjustments for this problem
  Baseball<-Baseball[,c("id","month","attended","ads.served")]
```
*** =sample_code
```{r}
# 1) Look at the first few rows of dataframe, `Baseball` with function `head`.


# Note: Notice that the first rows all have the same respondent id, but different months. In this case, the unit of analysis is not individuals or months, but what we could refer to as "person-months". Let's now determine our sample size of "person-months" and number of unique individuals.


# 2) Identify how many observations (`rows`) are in dataframe, `Baseball` with function `nrow`. Assign this result to object "Solution1"
    Solution1<-

# 3) Identify how many unique individuals (`id`) were sampled in dataframe, `Baseball` with functions `length` and `unique`. To help, we provide sample code for how to determine how long the vector, Baseball$month is, and code for printing the unique months in our sample.
    length(Baseball$month)
    unique(Baseball$month)
    
    Solution2<-
      
```
*** =solution
```{r}
    head(Baseball)
    Solution1<-nrow(Baseball)
    Solution2<-length(unique(Baseball$id))
```
*** =sct
```{r}
test_function("head", incorrect_msg = "Did you use the `head` function?")
test_function("nrow", incorrect_msg = "Did you use the `nrow` function?")
test_object("Solution1")
test_object("Solution2")
test_error()
success_msg("Good work! You should always explore your data before running analyses. These are very typical steps that one might take")
```



--- type:NormalExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:3c1d77fe1a
## Homerun Ad Campaign II - Correlating Variables
Let's now determine if the Hammer's ad-campaign appears effective by assessing whether our treatment variable is positively correlated with our outcome variable. In analysis, you may see the treatment variable is called the **independent** variable (because we have the freedom to manipulate its value in an experiment), and the outcome variable is called the **dependent** variable (because its value **depends** on the treatment variable), so let’s use those terms. 

Use the `cor` function to discover whether our independent variable (a.k.a. treatment variable), `ads.served`, is correlated with our dependent variable (a.k.a. outcome variable), `attended`.

*** =instructions
- 1) Find the correlation between `attended` and `ads.served` in dataframe, `Baseball` with the `cor` function.

*** =pre_exercise_code
```{r}
library(dplyr)
n=62
set.seed(1)
#Create rnorm function that allows for min and max
  rtnorm <- function(n, mean, sd, min = -Inf, max = Inf){
      qnorm(runif(n, pnorm(min, mean, sd), pnorm(max, mean, sd)), mean, sd)
  }
#Create rounding function that allows to round to numbers above 1
  mround <- function(x,base){
          base*round(x/base)
  }
#Create scaling function that puts number between 0 and 1
  scale <- function(x){
    (x - min(x))/(max(x)-min(x))
  }
#Dataframe
  Baseball<-data.frame(id=rep(1:n,each=6))
  Baseball$month=rep(1:6,n)
  Baseball$ads.served=ifelse(Baseball$month<4,round(rtnorm(n=n,mean=1,sd=.5,min=0,max=3)),round(rtnorm(n=n,mean=5,sd=3,min=1,max=12)))
  Baseball$temp<-rep(c(56,66,77,86,81,70),n)
  Baseball$ranking<-rep(c(21,15,11,4,7,13),n)
  Baseball$attended<-round(
                    rtnorm(n=n,mean=3,sd=1.5,min=0,max=6)+
                    .3*Baseball$ads.served+
                    .0006*Baseball$temp^2+
                    -.2*Baseball$ranking
                    )
  Baseball$attended[Baseball$attended<0]<-0
  Baseball$month=rep(c("April","May","June","July","August","September"),n)
  Baseball<-Baseball[,c("id","month","attended","ads.served","temp","ranking")]
#Adjustments for this problem
  Baseball<-Baseball[,c("id","month","attended","ads.served")]
```
*** =sample_code
```{r}
# 1) Find the correlation between `attended` and `ads.served` in dataframe, `Baseball` with the `cor` function. Assign this correlation to the object, Solution1. As an example of how this might be done, we provide the correlation between early summer months and ads served
    Baseball$earlysummer<-Baseball$month=="April" | Baseball$month=="May" | Baseball$month=="June"
    cor(Baseball$earlysummer,Baseball$ads.served)
    
    Solution1<-
      
```
*** =solution
```{r}
    Solution1<-cor(Baseball$attended,Baseball$ads.served)
```
*** =sct
```{r}
    test_object("Solution1")
    test_error()
    success_msg("Good work! Baseball attendance is positively correlated with number of ads served. Let's see if this relationship could be confounded.")
```



--- type:NormalExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:85efc26bc3
## Homerun Ad Campaign III - Merging in New Variables
Let's now determine if the treatment effect of the Hammer's ad campaign could be confounded by the temperature or rank of the team. To do this, we will need to merge in this data with dataframe `Baseball`:

*** =instructions
- 1) Print dataframe `dfMonth` to the console.
- 2) Merge `dfMonth` with dataframe `Baseball` by `month` with the `merge` function.

*** =pre_exercise_code
```{r}
library(dplyr)
n=62
set.seed(1)
#Create rnorm function that allows for min and max
  rtnorm <- function(n, mean, sd, min = -Inf, max = Inf){
      qnorm(runif(n, pnorm(min, mean, sd), pnorm(max, mean, sd)), mean, sd)
  }
#Create rounding function that allows to round to numbers above 1
  mround <- function(x,base){
          base*round(x/base)
  }
#Create scaling function that puts number between 0 and 1
  scale <- function(x){
    (x - min(x))/(max(x)-min(x))
  }
#Dataframe
  Baseball<-data.frame(id=rep(1:n,each=6))
  Baseball$month=rep(1:6,n)
  Baseball$ads.served=ifelse(Baseball$month<4,round(rtnorm(n=n,mean=1,sd=.5,min=0,max=3)),round(rtnorm(n=n,mean=5,sd=3,min=1,max=12)))
  Baseball$temp<-rep(c(56,66,77,86,81,70),n)
  Baseball$ranking<-rep(c(21,15,11,4,7,13),n)
  Baseball$attended<-round(
                    rtnorm(n=n,mean=3,sd=1.5,min=0,max=6)+
                    .3*Baseball$ads.served+
                    .0006*Baseball$temp^2+
                    -.2*Baseball$ranking
                    )
  Baseball$attended[Baseball$attended<0]<-0
  Baseball$month=rep(c("April","May","June","July","August","September"),n)
  Baseball<-Baseball[,c("id","month","attended","ads.served","temp","ranking")]
#Adjustments for this problem
  Baseball<-Baseball[,c("id","month","attended","ads.served")]
  dfMonth<-data.frame(month=c("April","May","June","July","August","September"),
                      temp=c(56,66,77,86,81,70),
                      ranking=c(21,15,11,4,7,13))
```
*** =sample_code
```{r}
# 1) Print dataframe `dfMonth` to the console. This can be done by either simply typing dfMonth below, or by using the `print` function with `dfMonth`.


# 2) Merge `dfMonth` with dataframe `Baseball` by `month` with the `merge` function. The merge function requires three arguments, your first dataframe, your second dataframe, and the name of the column that you want to merge by. To accomplish this, replace 'x, y, and "variable"' in the code below with 'Baseball, dfMonth, and "month"'.
    Baseball<-merge(x,y,by="variable")


```
*** =solution
```{r}
    dfMonth
    Baseball<-merge(Baseball,dfMonth,by="month")
```
*** =sct
```{r}
    test_object("Baseball")
    test_error()
    success_msg("Good work! This is a common way to merge data from different sized dataframes together. Now we can see whether these other variables are associated with attending baseball games and whether they may be confounding the relationship between baseball attendance and  number of ads served.")
```

--- type:NormalExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:796f46ec84
## Homerun Ad Campaign IV - Assessing confounders
Now that we have the data merged, let's see if the treatment effect of the Hammer's ad campaign could have been confounded by the temperature or rank of the team:

*** =instructions
- 1) Find the correlation between `attended` and `temp` in dataframe `Baseball`
- 2) Find the correlation between `attended` and `ranking` in dataframe `Baseball`

*** =pre_exercise_code
```{r}
library(dplyr)
n=62
set.seed(1)
#Create rnorm function that allows for min and max
  rtnorm <- function(n, mean, sd, min = -Inf, max = Inf){
      qnorm(runif(n, pnorm(min, mean, sd), pnorm(max, mean, sd)), mean, sd)
  }
#Create rounding function that allows to round to numbers above 1
  mround <- function(x,base){
          base*round(x/base)
  }
#Create scaling function that puts number between 0 and 1
  scale <- function(x){
    (x - min(x))/(max(x)-min(x))
  }
#Dataframe
  Baseball<-data.frame(id=rep(1:n,each=6))
  Baseball$month=rep(1:6,n)
  Baseball$ads.served=ifelse(Baseball$month<4,round(rtnorm(n=n,mean=1,sd=.5,min=0,max=3)),round(rtnorm(n=n,mean=5,sd=3,min=1,max=12)))
  Baseball$temp<-rep(c(56,66,77,86,81,70),n)
  Baseball$ranking<-rep(c(21,15,11,4,7,13),n)
  Baseball$attended<-round(
                    rtnorm(n=n,mean=3,sd=1.5,min=0,max=6)+
                    .3*Baseball$ads.served+
                    .0006*Baseball$temp^2+
                    -.2*Baseball$ranking
                    )
  Baseball$attended[Baseball$attended<0]<-0
  Baseball$month=rep(c("April","May","June","July","August","September"),n)
  Baseball<-Baseball[,c("id","month","attended","ads.served","temp","ranking")]
```
*** =sample_code
```{r}
# Note, we have sorted the merged dataframe `Baseball` by id and month for you. Although this is not necessary for this problem, it is often preferable to have longitudinal data sorted this way for conducting future analyses.
    head(Baseball)

# 1) Find the correlation between `attended` and `temp` in dataframe `Baseball`. Assign this correlation to Solution1.
    Solution1<-

# 2) Find the correlation between `attended` and `ranking` in dataframe `Baseball`. Assign this correlation to Solution2.
    Solution2<-

```
*** =solution
```{r}
    Solution1<-cor(Baseball$attended,Baseball$temp)
    Solution2<-cor(Baseball$attended,Baseball$ranking)
```
*** =sct
```{r}
    test_object("Solution1")
    test_object("Solution2")
    test_error()
    success_msg("Good work! Both temperature and ranking are highly correlated with attending Baseball games. Since these factors are likely associated with when the campaign was launched (during the summer), these factors likely confound the relationship between Baseball attendance and ads served.

Congratulations! You have now finished the Causal Inference with R - Introduction course. To continue your exploration into causal inference and learn slightly more advanced techniques for statistical inference, we highly recommend you try our next course, 'Causal Inference with R - Experiments")
```

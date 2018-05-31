--- 
title       : "Introduction to Treatment Effects"
description : "This chapter will introduce you to individual, group, and average treatment effects, and will let you learn and practice through R"
 

--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:df9b958a75
## The Average Treatment Effect
*** =video_link
//player.vimeo.com/video/230622767

--- type:NormalExercise lang:r aspect_ratio:62.5 xp:50 skills:1 
## Soggy Cereal III

Since there were no significant errors in their dataset, Puritan Wheat Inc. now wants you to determine whether their cereal, TechnoCrunch lasts a longer amount of `time` before it gets soggy than NeoPuffs. They also want to know whether `milk` absorption or `fiber` content are correlated with `time` before sogginess. That is, conduct the  the following steps:

*** =instructions
- Use the `mean` function to estimate the mean `time` in dataframe `Soggy` just for flakes that were in TechnoCrunch `cereal`
- Use the `mean` function to estimate the mean `time` in dataframe `Soggy` just for flakes that were in NeoPuffs `cereal`
- In dataframe `Soggy`, subtract the mean `time` for flakes in NeoPuffs `cereal` from the mean `time` for flakes in TechnoCrunch `cereal` to determine which cereal lasts longer before it gets soggy.
- Use the `cor` function to estimate the correlation between `milk` and `time`
- Use the `cor` function to estimate the correlation between `fiber` and `time`


*** =pre_exercise_code
```{r}
n=731
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
  x=rtnorm(n=n,mean=1,sd=.3,min=.5,max=1.5)
  x2=rtnorm(n=n,mean=.8,sd=.1,min=.1,max=1.5)
    
  Soggy<-data.frame(
    ID=1:n,
    cereal=rbinom(n,1,.4*x*x2),
    milk=mround(rtnorm(n=n,mean=3,sd=2,min=0,max=8)*x,.1),
    time=mround(rtnorm(n=n,mean=212,sd=20,min=99,max=399)*x2,1),
    fiber=mround(rtnorm(n=n,mean=30,sd=5,min=15,max=66)*x2^(1/2),1)
    )
  Soggy$time<-Soggy$time+Soggy$cereal*rtnorm(n=n,mean=10,sd=3,min=0,max=20)
  Soggy$cereal<-ifelse(Soggy$cereal==1,"TechnoCrunch","NeoPuffs")

```
*** =sample_code
```{r}
#Use the `mean` function to estimate the mean `time` in dataframe `Soggy` just for flakes that were in TechnoCrunch `cereal`. Remember that we had entered max(Soggy$time[Soggy$cereal=="TechnoCrunch"]) to get the maximum `time` in dataframe `Soggy`

#Use the `mean` function to estimate the mean `time` in dataframe `Soggy` just for flakes that were in NeoPuffs `cereal`

#In dataframe `Soggy`, subtract the mean `time` for flakes in NeoPuffs `cereal` from the mean `time` for flakes in TechnoCrunch `cereal` to determine which cereal lasts longer before it gets soggy.

#As an example for how to use the cor function for the following questions, we produce the correlation between milk and fiber below
    cor(Soggy$milk,Soggy$fiber)

#Use the `cor` function to estimate the correlation between `milk` and `time`

#Use the `cor` function to estimate the correlation between `fiber` and `time`




```
*** =solution
```{r}
    mean(Soggy$time[Soggy$cereal=="TechnoCrunch"])
    mean(Soggy$time[Soggy$cereal=="NeoPuffs"])
    mean(Soggy$time[Soggy$cereal=="TechnoCrunch"])-mean(Soggy$time[Soggy$cereal=="NeoPuffs"])
    cor(Soggy$milk,Soggy$time)
    cor(Soggy$fiber,Soggy$time)
    
```
*** =sct
```{r}
test_function("mean", incorrect_msg = "Did you use the `mean` function?")
test_function("cor", incorrect_msg = "Did you use the `cor` function?")
test_error()
success_msg("Good work! It appears that TechnoCrunch's crunchiness lasts longer than does NeoPuffs. However, you may have noticed that there is a positive correlation between fiber and time. We may eventually want to explore whether this correlation confounds the relationship between time and cereal brand.")
```


--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:5ebfd9aaa0
## The Unit Level Effect
*** =video_link
//player.vimeo.com/video/230623038


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:6238dbab2d
## Understanding Your Unit Level Causal Effect 
Multiple choice question: Suppose you want to learn your own unit level causal effect of eating breakfast on how hungry you are at dinner time. Monday you eat breakfast and write down how hungry you are later on. Tuesday you don't eat breakfast and write down how hungry you are later on. Then your unit level causal effect is the difference between these two numbers.
*** =instructions
- True
- False
*** =sct
```{r}
msg1 = "Unit level causal effects require all over variables to be held constant. In this example, the day of the week is not held constant, and hence is a potential confounder. Try again."
msg2 = "Correct. Unit level causal effects require all over variables to be held constant. In this example, the day of the week is not held constant, and hence is a potential confounder. In order to learn this causal effect directly from data, you would have to eat breakfast on Monday, and write down how hungry you are later on. Then, you would also have to not eat breakfast on that very same Monday, and write down how hungry you are later on. This is impossible, and so you cannot learn the unit level causal effect from the data. Instead, you will have to make assumptions, such as: the day of the week does not affect my hunger. We will talk ideas like this throughout the rest of the videos."
test_mc(correct = 2, feedback_msgs = c(msg1,msg2))
```TotalAttendancePerGameAprilTreatment<-sapply((rnorm(14,21,2)),as.integer)


--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:6fc38f8905
## The Conditional Average Treatment Effect
*** =video_link
//player.vimeo.com/video/230623221

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:2bbbcc3971
## Calculating Ice Cream Recipe Changes 
Suppose Edy's wants to know the effect of changing to a new recipe for chocolate ice cream on how many cartons of ice cream someone buys next month. Consider the following population. There are three people who are regular customers (buy Edy's at least once a month), with unit level causal effects of -10, -6, -5. For example, the first person will buy 10 fewer cartons if Edy's uses the new receipe. There are three people who are not regular customers, with unit level causal effects of -1, 0, 2. What is the difference between CATE(regular customers) and CATE(not regular customers)?
*** =instructions
- -3.33
- -7.33
- 0
- 20
*** =sct
```{r}
msg1 = "Correct! CATE(regular) = [(-10) + (-6) + (-5)]/3 = -7. CATE(not regular) = (-1 + 0 + 2)/3 = 1/3. So the difference is -7 - 1/3 = -7.33. We see that the average effect on regular customers is much different than on non-regulars: the regular customers will buy a lot less ice cream on average."
msg2 = "Try again: CATE(regular) = [(-10) + (-6) + (-5)]/3 = -7. CATE(not regular) = (-1 + 0 + 2)/3 = 1/3."
msg3 = "Try again: CATE(regular) = [(-10) + (-6) + (-5)]/3 = -7. CATE(not regular) = (-1 + 0 + 2)/3 = 1/3."
msg4 = "Try again: CATE(regular) = [(-10) + (-6) + (-5)]/3 = -7. CATE(not regular) = (-1 + 0 + 2)/3 = 1/3."
test_mc(correct = 1, feedback_msgs = c(msg1,msg2,msg3,msg4))
```

--- type:NormalExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:
## Practice identifying heterogeneous outcomes (Part 1)
The transportation network company, Unter Technologies, is interested in improving their employee morale and reducing employee turnover rate by downsizing their Human Resources (HR) Department.

To make sure this would not antagonize their workforce, Unter conducts an experiment: With a balanced sample of employees, Unter tells a treatment group that the HR Department will be downsized in the following year, and a control group that the HR Department will remain the same size in the following year (and magically, they don't end up discussing this with each other). Unter then surveys the employees to find out whether employees plan to look for new jobs, with response options 0="No" and 1="Yes."

With the dataframe, `UnterHR`, determine whether there is a negative or positive average treatment effect of reducing the size of Unter's HR department on employee turnover:

*** =instructions
- Determine the average effect of reducing the size of HR (`treatment`) on whether employees plan to leave their job in the following year (`LeaveJob`) by subtracting the mean rate of people's intention to leave their job in the control condition from the mean rate of people's intention to leave their job in the treatment condition.
*** =hint
- You will need to use the `mean` and `subset` commands.
- Try breaking the task into pieces. First find the mean rate of `LeaveJob`in the control condition (`Treatment=0`) then find the mean rate of `LeaveJob`in the treatment condition (`Treatment=1`).
*** =pre_exercise_code
```{r}
set.seed(1)
n=382
#Dataframe
  UnterHR<-data.frame(Treatment=rbinom(n,1,.4),Female=rbinom(n,1,.1),LeaveJob=0)
#LeaveJob
  #treatment makes men less likely to leave
    UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0]),1,.3)
    UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0]),1,.2)
  #treatment makes wommen more likely to leave
    UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1]),1,.3)
    UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1]),1,.6)
```
*** =sample_code
```{r}
# The average treatment effect is simply the mean outcome of the treatment group minus the mean outcome of the control group.

#---- Question 1-------------------------------------#
    Solution1<- 
#----------------------------------------------------#
```
*** =solution
```{r}
Solution1<- mean(UnterHR$LeaveJob[UnterHR$Treatment==1])-mean(UnterHR$LeaveJob[UnterHR$Treatment==0])
```

*** =sct
```{r}
test_object("Solution1")
success_msg("Good work! It seems that reducing the size of HR reduced Unter employees' intentions to leave their jobs")
```

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:
## Practice identifying heterogeneous outcomes (Part 2)
Since reducing the size of HR seems to reduce the rate of employee turnover, the CEO of Unter Technologies is now heavily considering this option.

However, his chief operating officer (COO) warns him that reducing the size of HR might be unpopular among certain minority groups within the company, particularly among women. The COO sends the CEO a figure (illustrated in the R workspace) showing the results of his experiment among men and women. Which of the following does the figure suggest?

*** =instructions
- While the pooled average treatment effect is slightly negative, and the average treatment effect for men is negative, the average treatment effect for women is positive.
- While the pooled average treatment effect is slightly positive, and the average treatment effect for men is positive, the average treatment effect for women is negative.
- While the pooled average treatment effect is slightly negative, and the average treatment effect for men is positive, the average treatment effect for women is negative.
- While the pooled average treatment effect is slightly positive, and the average treatment effect for men is negative, the average treatment effect for women is positive.
*** =pre_exercise_code
```{r}
set.seed(1)
n=382
#Dataframe
  UnterHR<-data.frame(Treatment=rbinom(n,1,.4),Female=rbinom(n,1,.1),LeaveJob=0)
#LeaveJob
  #treatment makes men less likely to leave
    UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0]),1,.3)
    UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0]),1,.2)
  #treatment makes wommen more likely to leave
    UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1]),1,.3)
    UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1]),1,.6)
    library(ggplot2)
    library(scales)
    df<-data.frame(Treatment=c("Control","Control","Treatment","Treatment"),Gender=c("Male","Female","Male","Female"),Value=c(mean(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0]),mean(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1]),mean(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0]),mean(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1])))
    df<-data.frame(Treatment=c("Control","Control","Control","Treatment","Treatment","Treatment"),Gender=c("Male","Female","Pooled","Male","Female","Pooled"),Value=c(mean(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0]),mean(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1]),mean(UnterHR$LeaveJob[UnterHR$Treatment==0]),mean(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0]),mean(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1]),mean(UnterHR$LeaveJob[UnterHR$Treatment==1])))
    df$Gender<-factor(df$Gender, levels = c("Male","Pooled","Female"))
    df$`Percent Intending to Quit`<-df$Value
    df$`Control and Treatment Groups`<-df$Treatment
    p<-ggplot(df, aes(x=`Control and Treatment Groups`,y=`Percent Intending to Quit`,group=Gender,color=Gender))
    p+geom_point(size=3)+geom_line(size=2)+scale_y_continuous(label = percent,limits = c(0,1))
```

*** =sample_code
```{r}
p<-ggplot(df, aes(x=`Control and Treatment Groups`,y=`Percent Intending to Quit`,group=Gender,color=Gender))
    p+geom_point(size=3)+geom_line(size=2)+scale_y_continuous(label = percent,limits = c(0,1))
```
*** =sct
```{r}
msg1 = "Good job! This is an example of a heterogeneous average treatment effect - the treatment has different effects on men and women. However, when men and women are pooled, this heterogeneity is masked."
msg2 = "Whoa! While you're right that there are different effects for men and for women, it looks like you're confused about which effects are negative and which are positive.  Try again."
msg3 = "While you're right that the pooled effects are negative and there are different effects for men and for women, it looks like you're confused about which gender-specific effects are negative and which are positive. Look again."
msg4 = "You're right about the gender-specific effects, but not the pooled effects. Check your results again."
test_mc(correct = 1, feedback_msgs = c(msg1,msg2,msg3,msg4))
```


--- type:NormalExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:
## Practice identifying heterogeneous outcomes (Part 3)
Let's further analyze the heterogeneous effect of the treatment on men vs. women in Unter Technologies. With the dataframe, `UnterHR`, determine the average treatment effect of reducing the size of Unter's HR department on employee turnover by gender (`Female`).

*** =instructions
- Determine the average effect of reducing the size of HR (`treatment`) on whether male employees (`Female = 0`) plan to leave the job in the following year (`LeaveJob`).
- Determine the average effect of reducing the size of HR (`treatment`) on whether female employees (`Female = 1`) plan to leave the job in the following year (`LeaveJob`).
*** =hint
- Remember, you can determine the ATE by subtracting the mean rate of the outcome in the control condition by the mean rate of the outcome in the treatment condition.
- You will need to use the `mean` and `subset` commands.
- Try breaking the task into pieces. First find the mean rate of `LeaveJob`in the control condition (`Treatment=0`) then find the mean rate of `LeaveJob`in the treatment condition (`Treatment=1`).
*** =pre_exercise_code
```{r}
set.seed(1)
n=382
#Dataframe
  UnterHR<-data.frame(Treatment=rbinom(n,1,.4),Female=rbinom(n,1,.1),LeaveJob=0)
#LeaveJob
  #treatment makes men less likely to leave
    UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0]),1,.3)
    UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0]),1,.2)
  #treatment makes wommen more likely to leave
    UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1]),1,.3)
    UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1]<-rbinom(length(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1]),1,.6)
```
*** =sample_code
```{r}
# Since we are interested in understanding the rates of intention to leave by treatment and gender, we might want to examine a three way table of this relationship first. The following syntax prints the numbers of men and women who intend to leave work by treatment group and gender.
    xtabs(~LeaveJob+Treatment+Female, data=UnterHR)

# Since the treatment and control groups among women are of relatively similar sizes, it is fairly easy to get a sense of how treatment affects women's intention to leave Unter; the majority of women in the treatment group appear to want to leave, whereas the majority of women in the control group do not. But to be sure, let's actually calculate the differences in the average treatment effects among men and women.

# Question 1: Determine the average treatment effect among men.
#---- Question 1-------------------------------------#
    Solution1<- 
#----------------------------------------------------#

# Question 2: Determine the average treatment effect among women.
#---- Question 2-------------------------------------#
    Solution2<- 
#----------------------------------------------------#

```
*** =solution
```{r}
Solution1 <- mean(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==0])-mean(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==0])
Solution2 <- mean(UnterHR$LeaveJob[UnterHR$Treatment==1 & UnterHR$Female==1])-mean(UnterHR$LeaveJob[UnterHR$Treatment==0 & UnterHR$Female==1])
```
*** =sct
```{r}
test_object("Solution1")
test_object("Solution2")
success_msg("Good work! We can see a clear difference in the treatment effect among men and women. This is a clear example of a conditional average treatment effect.")
```



--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:
## Introduction to the Causal Inference Bootcamp
*** =video_link
//player.vimeo.com/video/230621577
 

--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:
## Measurement
*** =video_link
//player.vimeo.com/video/230621760


--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:
## Description
*** =video_link
//player.vimeo.com/video/230622159


--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:
## Correlation vs. Causation
*** =video_link
//player.vimeo.com/video/230622365


--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:
## The Average Treatment Effect
*** =video_link
//player.vimeo.com/video/230622767


--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:
## The Unit Level Effect
*** =video_link
//player.vimeo.com/video/230623038


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:
## Understanding Your Unit Level Causal Effect 
Multiple choice question: Suppose you want to learn your own unit level causal effect of eating breakfast on how hungry you are at dinner time. Monday you eat breakfast and write down how hungry you are later on. Tuesday you don't eat breakfast and write down how hungry you are later on. Then your unit level causal effect is the difference between these two numbers.
*** =instructions
- True
- False
*** =sct
```{r}
msg1 = "Unit level causal effects require all over variables to be held constant. In this example, the day of the week is not held constant, and hence is a potential confounder. Try again."
msg2 = “Correct. Unit level causal effects require all over variables to be held constant. In this example, the day of the week is not held constant, and hence is a potential confounder. In order to learn this causal effect directly from data, you would have to eat breakfast on Monday, and write down how hungry you are later on. Then, you would also have to not eat breakfast on that very same Monday, and write down how hungry you are later on. This is impossible, and so you cannot learn the unit level causal effect from the data. Instead, you will have to make assumptions, such as: the day of the week does not affect my hunger. We will talk ideas like this throughout the rest of the videos.”
test_mc(correct = 2, feedback_msgs = c(msg1,msg2))
```


--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:
## The Conditional Average Treatment Effect
*** =video_link
//player.vimeo.com/video/230623221

--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:
## Calculating Ice Cream Recipe Changes 
Suppose Edy's wants to know the effect of changing to a new recipe for chocolate ice cream on how many cartons of ice cream someone buys next month. Consider the following population. There are three people who are regular customers (buy Edy's at least once a month), with unit level causal effects of -10, -6, -5. For example, the first person will buy 10 fewer cartons if Edy's uses the new receipe. There are three people who are not regular customers, with unit level causal effects of -1, 0, 2. What is the difference between CATE(regular customers) and CATE(not regular customers)?
*** =instructions
- -3.33
- -7.33
- 0
- 20
*** =sct
```{r}
msg1 = “Correct! CATE(regular) = [(-10) + (-6) + (-5)]/3 = -7. CATE(not regular) = (-1 + 0 + 2)/3 = 1/3. So the difference is -7 - 1/3 = -7.33. We see that the average effect on regular customers is much different than on non-regulars: the regular customers will buy a lot less ice cream on average.”
msg2 = “Try again: CATE(regular) = [(-10) + (-6) + (-5)]/3 = -7. CATE(not regular) = (-1 + 0 + 2)/3 = 1/3.“
msg3 = "Try again: CATE(regular) = [(-10) + (-6) + (-5)]/3 = -7. CATE(not regular) = (-1 + 0 + 2)/3 = 1/3."
msg4 = "Try again: CATE(regular) = [(-10) + (-6) + (-5)]/3 = -7. CATE(not regular) = (-1 + 0 + 2)/3 = 1/3."
test_mc(correct = 1, feedback_msgs = c(msg1,msg2,msg3,msg4))
```

--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:
## Confounders
*** =video_link
//player.vimeo.com/video/230623543


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:
## Understanding Confounders
Why are confounding variables a potential problem?
*** =instructions
- Because treatment is not randomly assigned
- Because the control groups and treatment groups are not identical
- Because the treatment variable is correlated with an unobserved variable that might affect outcomes
- Because confounders are not observed
*** =sct
```{r}
msg1 = “The main reason we worry about confounders has to do with outcomes, not treatment assignment. Try again."
msg2 = "The main reason we worry about confounders has to do with outcomes, not our sampling technique. Try again."
msg3 = "Correct! Confounders are called *confounders* for a reason---because when they are present, we cannot distinguish the effect of treatment from the effect of the confounder. To learn causal effects, we want to compare people with treatment and people without treatment. If those two groups of people differ in their values of some potential confounding variable, then we can't tell if differences in outcomes are due to differences in treatment, or differences in the confounder."
msg4 = “Unobserved variables are not always a problem in causal inference, because they may not have any effect on outomes. Try again”
test_mc(correct = 3, feedback_msgs = c(msg1,msg2,msg3,msg4))
```

--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:
## Counterfactuals
*** =video_link
//player.vimeo.com/video/230623577


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:
## Counterfactuals and You 
Suppose you hadn't watched this video just now, and weren't reading this question. Instead, you went outside and enjoyed the day with a stroll and ate an ice cream cone, which unfortunately was affected by a terrible curse that would have thwarted your every desire for the rest of your life. So not eating that ice cream and instead taking this course right now has literally saved you from this terrible curse. Right?
*** =instructions
- Yes
- I can’t tell you either way
- No

*** =sct
```{r}
msg1 = “Oops! Think about the data you have about your world, and the data about the counterfactual that you don’t have. Try again."
msg2 = “Correct! The question proposed a counterfactual world where not watching these modules ends in disaster for you, and thus the unit level causal effect of taking the course is to avoid this disaster. Well, you did watch this video and so we will never know what happened if you didn't. It's possible that such a disaster may have happened, but we just don't know. So while you may think this sounds a bit implausible, it can't be refuted with the data you directly observe.”
msg3 = "Oops! Think about the data you have about your world, and the data about the counterfactual that you don’t have. Try again."
test_mc(correct = 2, feedback_msgs = c(msg1,msg2,msg3))
```

--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:
## Statistical Inference vs. Causal Inference
*** =video_link
//player.vimeo.com/video/230623833


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:
## Big Data and Causal Inference 
If I have an enormous amount of data, do I still have to worry about causal inference?
*** =instructions
- It depends
- Yes
- No
*** =sct
```{r}
msg1 = “Correct. In some cases, we don't care about causality. For example, if we are trying to make predictions *in a stable environment* where we are *not* intervening to change policy, then often we don't have to worry about causal inference. A good example of this is weather forecasting. If you want to know what the weather in your town will be like next summer, your best prediction is probably going to just depend on the weather in the previous summers. But if you want to predict the weather next summer after implementing a nationwide cloud-seeding policy to increase the number of clouds on Earth in an effort to cool global temperatures, then you would want to understand the causal effects of treatments on the weather system than just relying on past data. For that difficult question, all the data on weather that exists might not be sufficient to answer your causal question.
”
msg2 = "If this were the case, education would confound the relationship between having and not having the death penalty. We would expect that states with the death penalty have higher underlying homicide rates of homicide, so whatever deterrent effect of the death penalty that we estimated would be smaller than the true deterrent effect. Try again."
msg3 = “Big Data does not solve all problems by magic! Depending on your data and your questions, you may need to worry about causal inference. Try again.“
test_mc(correct = 1, feedback_msgs = c(msg1,msg2,msg3))
```


--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:
## p Hacking and Talking to Ghosts
*** =video_link
//player.vimeo.com/video/230618095


--- type:VideoExercise lang:r aspect_ratio:62.5 xp:50 skills:1 key:
## Bonus Video: How to Read Empirical Papers
*** =video_link
//player.vimeo.com/video/230624036



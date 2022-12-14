# I. About Me

My name is Erik Sundberg. I am currently a Master's student at UW Madison studying Systems and Data Analytics. I graduated with a Bachelor of Science in Industrial Engneering and Economics. After graduation, I worked as an engineer and decided to pursue a career in Data Science.
I am currently working as an Editorial Assitant for UW Madison, and I am leading the development of a website tracking the workflow and performance of peer-reviewers assisting in the management of The Journal of Human Factors and Ergonomics Society. This website is powered using a data warehouse populated using a Python/SQL data pipeline.
This year, I am developing my machine learning skills. To achieve this goal, I am taking mathematical courses in Data Science focuisng on causal interference, matrix methods, and applied machine learning.



# II. Introduction

For this project, I will be examining if the position of the sun during school start times causes a change in performance. To examine this, I will be comparing schools near timezone borders. This will demonstrate the effect becuase schools which are geographically close but exist in different time zones will have differ in start times by one hour. A significant difference in performance may suggest a casual relationship between start time (relative to the position of the sun) and student performance.
The random variable in this scenario will be on what side of the time zone a school is on. This will seperate the schools into two groups. All schools must be near the time zone boarder. Schools which have a later start time (as measured by the actual position of the sun) will be the treatment group. When comparing schools, I will need to account for the average income of parents becuase it has a known impact on acacdemic performance. Further research into confounding variables will be neccesary to justify a casual relationship.
While research has already been done on the benefits of a later start date, this observational study may provide additional insites by identifying the affect of timezone bondaries. Furthermore, examination into additional timezone associations may be warrented based on the results of data exploration. My biggest limitation is that I will not be able to analyze the affect of treatment on an untreated individual. Rather, I will only be measuring long term differences in lifestyle that arise from later start times (relative to the postion of the sun).



# III. Identification

I will how the position of the sun at a school???s start time effects test scores. To identify this effect, I will investigate this as a potential outcomes problem. Thus, time zone will be the treatment and test score will be the outcome. 
Time zones are generally influenced by state lines. However, there are multiple states which have more than one time zone. Kentucky is a state which has a large quantity of schools in both the central time zone and eastern time zone. Education is heavily influenced by state government. By comparing schools only in Kentucky, I will remove the significant effect of state policy on test scores. This will help isolate the effect my treatment has.
Importantly, I will assume that the time zone a school is located in does not have an association with other variables which effect educational outcomes (e.g. district wealth). I believe this assumption is reasonable. Physically being in eastern or western Kentucky???when accounting for other variables???should not affect test scores. 
Let Y(a) represent the outcome given treatment A. Y(a) will be the average high school standardized test scores of a school. let A represent the position of the sun at a school???s start time. In other words, let A represent the time zone a school is in. Let X be a matrix of all other variables affecting the outcome. The variables in X will include parental education, wealth, etc. 
Applying this framework, we can create the following single world intervention graph:

 
  
#### Formal Assumptions
I will make the following assumptions because I am using a potential outcomes framework. 

##### Assumption 1: Positivity 
I will assume there are not negative outcomes. This is reasonable because all test scores are positive, and the variable of time zone will be binary. Furthermore, all variables in the X matrix will be greater than zero. 

##### Assumption 2: Stable Unit Treatment Value.  
I will assume that mapping of time zone onto test scores is a real-valued measurable function. This assumption is reasonable because test score data already exists. In the most extreme case, we would simply have on effect of our treatment on test scores.


##### Assumption 3: Exchangeability
I will assume that the potential outcomes Y(a) are independent from the treatment assignment A. This assumption should hold. Whether a school is physically in western or eastern Kentucky alone should not give inform us how they would perform if they were in a different time zone. However, the time zone of a school in Kentucky may actually provide information on if a school is in Appalachia???a region which lacks a good education system. Therefore, this is the most questionable of my assumptions.  This assumption allows my SWIG to be true. 

#### Identification Proof
First, my swig proves that A|a and X are independent because the outcome Y(a) is a collider. Thus, using my 3 assumptions, we know that 

E[Y(a)] = E[Y|A=a]. 


# IV. Estimation

To conduct Estimation, I will have my treatment Variable A, my outcome assignment Y, and my adjustment variables X. Let X be a matrix containing all known variables which effect a schools performance on the ACT. Becuase we are estimating the effect of our treatment variable A on our outocme Y, we must isolate the effect. 

A regression would be suitable for estimating Y(A). This is because it would regularize for the myriad of other variables affecting test scores. However, for this to work we should include all features which impact a high schools ACT scores in our X matrix. These include family income, parental education, disruptive home situations, and educational achievement (Source 1). If we have a complete dataset, we could then run a regression which would give us the effect of our treatment A. 

Unfortunately, no such dataset exists. However, it is worth noting the expected properties of this regression. First, the errors should be normally distributed. We must also examine any correlations between variables in our X vector to assure there is no auto correlation. A regression should perform well in this setting. Regressions are on of the most widely used tools in data analysis due to their efficiency and simplicity. However, it is worth noting some of the downsides. Due to the massive variability between schools, the effect of our treatment may be dwarfed by more important variables (such as income). This may make it hard to identify the casual effect. 


Works Cited:

1.) https://eric.ed.gov/?id=ED510477#:~:text=Family%20income%2C%20parents'%20level%20of,and%20others%2C%20and%20academic%20achievement.

# V. Sensitivity

Sensitivity analysis is a statistical technique that is used to assess the impact of varying the assumptions or inputs of a model on the output or results of the model. In the context of experiments, sensitivity analysis can be used to determine the robustness of the results of the study by investigating how sensitive the results are to changes in the assumptions or inputs of the model.

One method for conducting sensitivity analysis is known as Manski Sensitivity, named after economist Charles Manski. This method involves varying the assumptions or inputs of the model over a range of reasonable values and observing the impact on the output or results of the model. This allows researchers to assess the robustness of the results and identify potential sources of uncertainty or bias in the study.
	
In this study, the most important assumption is that the variability between schools on opposite sides of the time zones can be accounted for using the data in my dataset. If this assumption proves to be untrue, the validity and reliability of the results may be called into question. If. This is partly because my treatment A indirectly captures differences between regions of Kentucky, even though I have tried to isolate the effects of the sun. Therefore, a violation of this assumption would make my results meaningless. 

An alternative approach to studying the impact of time zones on student performance could be to examine schools districts within each time zone that have similar characteristics. This would increase the similarity among the schools in the sample and strengthen the assumption that there are no unmeasured confounding variables associated with geographic location. While this approach would likely involve reducing the sample size of the study, the increased similarity among the schools in the sample would improve the validity and reliability of the results. 

One assumption that cannot be tested in this study is that all schools are equally affected by sunlight. If factors such as architectural design and local environmental features, such as the density of trees or hills that block sunlight, are significantly related to the potential benefits of a later start time, this could introduce a confounding variable into the data set. In other words, the relationship between starting times and academic performance could be influenced by these factors in ways that are difficult to control for or predict. This could make it difficult to accurately identify the true causal effect of starting times on academic performance.

# VI. Conclusion

In this project, I proposed a methodology for studying the effect of time zones on academic performance. However, my biggest limitation was a lack of data. If public databases containing the necessary information become available in the future, I will be able to conduct my regression analysis and identify the causal effect. Despite the challenge of a lack of data, I believe that a thorough analysis of the relationship between starting times and academic performance could yield valuable insights and contribute to our understanding of how to support students' academic success.


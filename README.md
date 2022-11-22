# I. Introduction

My name is Erik Sundberg
I am currently a Master's student at UW Madison studying Systems and Data Analytics. I graduated with a Bachelor of Science in Industrial Engneering and Economics. After graduation, I worked as an engineer and decided to pursue a career in Data Science.
I am currently working as an Editorial Assitant for UW Madison, and I am leading the development of a website tracking the workflow and performance of peer-reviewers assisting in the management of The Journal of Human Factors and Ergonomics Society. This website is powered using a data warehouse populated using a Python/SQL data pipeline.
This year, I am developing my machine learning skills. To achieve this goal, I am taking mathematical courses in Data Science focuisng on causal interference, matrix methods, and applied machine learning.



# II. 

For this project, I will be examining if the position of the sun during school start times causes a change in performance. To examine this, I will be comparing schools near timezone borders. This will demonstrate the effect becuase schools which are geographically close but exist in different time zones will have differ in start times by one hour. A significant difference in performance may suggest a casual relationship between start time (relative to the position of the sun) and student performance.
The random variable in this scenario will be on what side of the time zone a school is on. This will seperate the schools into two groups. All schools must be near the time zone boarder. Schools which have a later start time (as measured by the actual position of the sun) will be the treatment group. When comparing schools, I will need to account for the average income of parents becuase it has a known impact on acacdemic performance. Further research into confounding variables will be neccesary to justify a casual relationship.
While research has already been done on the benefits of a later start date, this observational study may provide additional insites by identifying the affect of timezone bondaries. Furthermore, examination into additional timezone associations may be warrented based on the results of data exploration. My biggest limitation is that I will not be able to analyze the affect of treatment on an untreated individual. Rather, I will only be measuring long term differences in lifestyle that arise from later start times (relative to the postion of the sun).



# III. Identification

I will how the position of the sun at a school’s start time effects test scores. To identify this effect, I will investigate this as a potential outcomes problem. Thus, time zone will be the treatment and test score will be the outcome. 
Time zones are generally influenced by state lines. However, there are multiple states which have more than one time zone. Kentucky is a state which has a large quantity of schools in both the central time zone and eastern time zone. Education is heavily influenced by state government. By comparing schools only in Kentucky, I will remove the significant effect of state policy on test scores. This will help isolate the effect my treatment has.
Importantly, I will assume that the time zone a school is located in does not have an association with other variables which effect educational outcomes (e.g. district wealth). I believe this assumption is reasonable. Physically being in eastern or western Kentucky—when accounting for other variables—should not affect test scores. 
Let Y(a) represent the outcome given treatment A. Y(a) will be the average high school standardized test scores of a school. let A represent the position of the sun at a school’s start time. In other words, let A represent the time zone a school is in. Let X be a matrix of all other variables affecting the outcome. The variables in X will include parental education, wealth, etc. 
Applying this framework, we can create the following single world intervention graph:

 
  
#### Formal Assumptions
I will make the following assumptions because I am using a potential outcomes framework. 

##### Assumption 1: Positivity 
I will assume there are not negative outcomes. This is reasonable because all test scores are positive, and the variable of time zone will be binary. Furthermore, all variables in the X matrix will be greater than zero. 

##### Assumption 2: Stable Unit Treatment Value.  
I will assume that mapping of time zone onto test scores is a real-valued measurable function. This assumption is reasonable because test score data already exists. In the most extreme case, we would simply have on effect of our treatment on test scores.


##### Assumption 3: Exchangeability
I will assume that the potential outcomes Y(a) are independent from the treatment assignment A. This assumption should hold. Whether a school is physically in western or eastern Kentucky alone should not give inform us how they would perform if they were in a different time zone. However, the time zone of a school in Kentucky may actually provide information on if a school is in Appalachia—a region which lacks a good education system. Therefore, this is the most questionable of my assumptions.  This assumption allows my SWIG to be true. 

#### Identification Proof
First, my swig proves that A|a and X are independent because the outcome Y(a) is a collider. Thus, using my 3 assumptions, we know that 

E[Y(a)] = E[Y|A=a]. 


# IV. Estimation

To conduct Estimation, I will have my treatment Variable A, my outcome assignment Y, and my adjustment variables X. As I have discussed prior, I assume Y(A) is well-defined and has SUTVA. With Identification, I know that E[Y | A=a] = E[Y(a)]
 
Thus, the ideal data set should include X, A, and Y for every observation. X is a vectored value containing data known to effect average standardized test scores. This would include measures such as income, urbanicity, and other key factors. A is our treatment variable which contains the position of the sun at a schools start time. Therefore, we can use a regression to quantify the effect (by measuring the parameter) of my treatment variable A. Furthermore, the ideal dataset should have no less than 30 observations. Ideally, we would have hundreds. 

Thus, to implement this algorithm, we will apply a simple linear regression using Sum of squares. 

(should I discuss the possiblility of other curves being more accurate representations?)
(Is there any point to including additional measures of estimation? I've considered matching, but this experiement does not seem well set up for that.)

It is worth noting the expected properties of this regression. First, the errors should be normally distributed. We must also examine any correlations between variables in our X vector to assure there is no auto correlation. A regression should perform well in this setting. Regressions are on of the most widely used tools in data analysis due to their efficiency and simplicity. However, it is worth noting some of the downsides. Due to the massive variability between schools, the effect of our treatment may be dwarfed by more important variables (such as income). This may make it hard to identify the casual effect.

(Should I go more in depth about properties?)


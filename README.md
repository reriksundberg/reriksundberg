# Estimation

To conduct Estimation, I will have my treatment Variable A, my outcome assignment Y, and my adjustment variables X. As I have discussed prior, I assume Y(A) is well-defined and has SUTVA. With Identification, I know that E[Y | A=a] = E[Y(a)]
 
Thus, the ideal data set should include X, A, and Y for every observation. X is a vectored value containing data known to effect average standardized test scores. This would include measures such as income, urbanicity, and other key factors. A is our treatment variable which contains the position of the sun at a schools start time. Therefore, we can use a regression to quantify the effect (by measuring the parameter) of my treatment variable A. Furthermore, the ideal dataset should have no less than 30 observations. Ideally, we would have hundreds. 

Thus, to implement this algorithm, we will apply a simple linear regression using Sum of squares. 

(should I discuss the possiblility of other curves being more accurate representations?)
(Is there any point to including additional measures of estimation? I've considered matching, but this experiement does not seem well set up for that.)

It is worth noting the expected properties of this regression. First, the errors should be normally distributed. We must also examine any correlations between variables in our X vector to assure there is no auto correlation. A regression should perform well in this setting. Regressions are on of the most widely used tools in data analysis due to their efficiency and simplicity. However, it is worth noting some of the downsides. Due to the massive variability between schools, the effect of our treatment may be dwarfed by more important variables (such as income). This may make it hard to identify the casual effect.

(Should I go more in depth about properties?)


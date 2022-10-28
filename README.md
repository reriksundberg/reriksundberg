### Identification of the effect of timezones on tests scores

### Introduction
  I will how the position of the sun at a school’s start time effects test scores. To identify this effect, I will investigate this as a potential outcomes problem. Thus, time zone will be the treatment and test score will be the outcome. 
  Time zones are generally influenced by state lines. However, there are multiple states which have more than one time zone. Kentucky is a state which has a large quantity of schools in both the central time zone and eastern time zone. Education is heavily influenced by state government. By comparing schools only in Kentucky, I will remove the significant effect of state policy on test scores. This will help isolate the effect my treatment has.
Importantly, I will assume that the time zone a school is located in does not have an association with other variables which effect educational outcomes (e.g. district wealth). I believe this assumption is reasonable. Physically being in eastern or western Kentucky—when accounting for other variables—should not affect test scores. 
  Let Y(a) represent the outcome given treatment A. Y(a) will be the average high school standardized test scores of a school. let A represent the position of the sun at a school’s start time. In other words, let A represent the time zone a school is in. Let X be a matrix of all other variables affecting the outcome. The variables in X will include parental education, wealth, etc. 
	Applying this framework, we can create the following single world intervention graph:

<img width="306" alt="image" src="https://user-images.githubusercontent.com/113559546/198442446-e658b695-04f9-4827-9ac1-b4c93f12e51d.png">

### Formal Assumptions

I will make the following assumptions because I am using a potential outcomes framework. 

# Assumption 1: Positivity 
I will assume there are not negative outcomes. This is reasonable because all test scores are positive, and the variable of time zone will be binary. Furthermore, all variables in the X matrix will be greater than zero. 

# Assumption 2: Stable Unit Treatment Value
I will assume that mapping of time zone onto test scores is a real-valued measurable function. This assumption is reasonable because test score data already exists. In the most extreme case, we would simply have on effect of our treatment on test scores.

(?Is more depth required here? Should the 4 points of STUVA be individually justified?)
# Assumption 3: Exchangeability.
	I will assume that the potential outcomes Y(a) are independent from the treatment assignment A. This assumption should hold. Whether a school is physically in western or eastern Kentucky alone should not give inform us how they would perform if they were in a different time zone. However, the time zone of a school in Kentucky may actually provide information on if a school is in Appalachia—a region which lacks a good education system. Therefore, this is the most questionable of my assumptions.  This assumption allows my SWIG to be true. 
	
Identification

First, my swig proves that A|a and X are independent because the outcome Y(a) is a collider. 

Thus, using my 3 assumptions, we know that E[Y(a)] = E[Y|A=a]. 

Pending Questions for Professor and Peer Review

(Is the proof literally just the proof of potential outcomes?

Am I missing something?

Should I have this proof copied and typed out?

I know the structure of my problems makes identification very easy as I have a simple SWIG, but did I correctly apply the rules?)

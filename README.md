# Logistic-Regression
Logistic Regression predicts whether something is true or false rather than predicting something continuous like size.
![image](https://github.com/shijie96/Logistic-Regression/assets/145702972/27030e88-4ffe-47f8-b245-b97fe1bdf8a7)
Instead of fitting a line to the data, logistic regression fits an ‘s’ shaped ‘logistic function’.
The curve goes from 0 to 1. It means that the curve tells you the probability that a mouse is obese based on its weight. Although logistic regression tells the probability that a mouse is obese or not, it’s usually used for classification, e.g if the probability of a mouse being obese is greater than 50%, then we’ll classify it as obese, otherwise we’ll classify it as ‘not obese’.
![image](https://github.com/shijie96/Logistic-Regression/assets/145702972/46d4a0b4-81d5-4bd9-ba61-c28644f281c1)
Logistic Regression doesn’t have the same concept of a ‘residual’, so it cannot use least squares and calculate R2. Instead it uses something called ‘maximum likelihood’.

# Logistic Regression Details (Part 1: coefficients)
Logistic Regression is a specific type of Generalized linear model (often abbreviated GLM).

With linear regression , the values on the y-axis can be any number. However, the y-axis is confined to probability values from 0 to 1 for logistic regression.
![image](https://github.com/shijie96/Logistic-Regression/assets/145702972/a2a89ca9-c13e-435c-884a-9a4ceddff156)
To solve this problem, the y-axis in logistic regression is transformed from the ‘probability of obesity’ to the ‘log (odd of obesity)’, so, just like the y-axis in linear regression, it can go from negative infinity to positive infinity. 
![image](https://github.com/shijie96/Logistic-Regression/assets/145702972/84cfad12-765c-422f-80a5-93a44c0c265d)
Once, we use log(odds of obesity) to transform the binary variable to a new y-axis. It is similar to ordinary linear regression and we can get intercept and slope estimates. The z-score of the intercept is calculated by intercept estimate divided by standard deviation. 

Next, logistic regression coefficients in the context of testing if a discrete variable on x-axis like ‘whether or not a mouse has a mutated gene’ is related to obesity.
![image](https://github.com/shijie96/Logistic-Regression/assets/145702972/c08066fa-1ff6-42c7-ae3b-f87c5b27f562)
This type of logistic regression is very similar to how a t-test is done using linear regression. 
![image](https://github.com/shijie96/Logistic-Regression/assets/145702972/794bb571-0ec9-4123-ac32-5be297695386)
The two lines come together to form the coefficients in this equation.
Size = Meannormal B1 + (Meanmutate - Meannormal) B2              
The first column in the 2 by 2 matrix corresponds to values for B1 and it turns on the first coefficient Meannormal . The second column corresponds to values for B2 and turns the second coefficient (Meanmutate - Meannormal), ‘off’ or ‘on’ depending on whether it is a 0 or a 1.

When we are dealing with a logistic regression with a discrete variable on the x- axis, the first thing is to transform the y-axis from the probability of being obese to the log (odds of obesity). 
![image](https://github.com/shijie96/Logistic-Regression/assets/145702972/819e6acb-cd5c-4a3a-82e7-511cd04c73bb)
For the first line, we take the ‘Normal gene’ data and use it to calculate the log(odds of obese) for mice with the normal gene.
First line: log(2/4) = log(0.5) = -0.3
Second line: log(6/3) = log(2) = 0.30

Obese = log(odds gene normal) B1 + (log(odds gene mutated) -  log(odd gene normal)) B2
Obese = -0.3 B1 + 0.3 B2
 It tells us, on a log scale, how much having the mutated gene increases (or decreases) the odds of a mouse being obese.

# Part 3: Maximum likelihood
As we know, we transformed the y-axis to positive infinite and negative infinite.
For ordinary linear regression, we use least squares to find out the best fitting line. However, in logistic regression, we use maximum likelihood to fit the best line.

The first thing is that we project the original data points onto the candidate line. This gives each sample a candidate log(odds) value.
![image](https://github.com/shijie96/Logistic-Regression/assets/145702972/5110747a-dc8a-4d7e-b1e2-39b158682c19)
Then we transform the candidate data log(odds) to candidate probabilities using this fancy looking formula…..
P= e log(odds) / (1 + e log(odds))
Now, we use the observed status (obese and no obese) to calculate their likelihood given the shape of the squiggle line.\

Likelihood of data given the squiggle = P1 * P2* ......*Pn

Then, we rotate the line, and calculate the likelihood. 



# # Linear Regression, Clearly Explained!!!

[Video URL](https://www.youtube.com/@statquest)

The main ideas -> 
1. Use Least Square to fit a line to the data
2. Calcualte the R^2
3. Calculate p-value for R2

Example taken of mouse wt(x-axis) vs mouse size
1. Draw a line through the data. 
2. Measure the distance from the line to the data, square each distance and add them. This is residual
3. Rotate the line a bit. Calcualte the Residuals.
4. Keep Rotating

This will help to get Rotations vs *Sum of Squared Residuals*
It helps to get the best fit line which is with the least square error. 
Least square computes 2 parameters:
1. y-intercept
2. slope

As slope of line is not 0, it means knowing mouse's weight will help us make a guess about that mouse's size. 
To check how good our equation is, we will compute R2. 

1. Calculate the average mouse size. 
2. Calcualte SS((mean)) Measure distance from mean to the data point (this is like baseline model) and then square it & sum all i.e, sum of squares around the mean.
   ss(mean) = (data - mean)^2
   variation around mean is    ss(mean)/n
3. Calculate SS(Fit), sum of squared res around our least square fit. (data - line)2
   var(fit) = SS(fit) / n
4. R2 tells us variation in mouse size that can be explained by taking mouse weight into account.
   R2 = (Var(mean) - Var(fit) )/ Var(mean)
5. If R2 is 0.6=60% then it means there's a 60% reduction in variance when we take the mouse weight into account.


When there are 2 or more feature variables like Tail length, body weight to compute the body length, we now try to fit a plane not a line. 
The same way things move, we compute the residuals 
If tail length is useless and doesn't make SS(fit) smaller then least-square will ignore it by making that parameter = 0. 

So, equation with more terms will never perform worse than a simple linear equation. It's because Least Square will cause any term that make SS(fit) worse to be multiplied by 0 and in a sense no longer exist. 

But if by chance a variable like "flip of a coin", it increases the probability that the small mice in dataset might get heads more frequently than large mice. If this happens then we'd get a smaller SS(fit) and  a better R2. 
The more parameters we add to the equation, more opportunities we have for the random events to reduce SS(fit) and a better R2. 
So, people use Adjusted R2 values that scales R2 by the number of parameters. 

R2 is awesome but it misses something.  

Let 2 points are there, SS(mean) = 100 , ss(fit) = 0( because we can always draw a straight line to connect any 2 points) then R2 = 100%. 
You will get same R2 for any 2 random points because a line can directly join those.

So, we need a way to determine if the R2 value is statistically significant.

#### Let's talk about p-value for R2
p-value for R2 comes from something called **"F"**. 
**F** = **The variation in mouse size explained by wt** /  **variation in size not explained by the weight** 

<iframe src="https://drive.google.com/file/d/1IUb5ymUyJItwyFAenJz9x3F4MtrCNCak/preview" width="640" height="100" allow="autoplay"></iframe>


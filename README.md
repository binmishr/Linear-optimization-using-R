# Linear-optimization-using-R

Linear optimization using R, in this tutorial we are going to discuss the linear optimization problems in R.

Optimization is everything nowadays. We all have finite resources and time and we want to make the maximum profit out of that.

Companies want to makes maximum profits based on limited resources they have, yes optimization is the solution for that.

Data scientists can provide optimal solutions based on given constraints to achieve maximum profit.

Significance of Spearman’s Rank correlation
Objective

To find the optimal solution for the problem given below.

Suppose a company wants to maximize the profit for two products A and B which are sold at $25 and $20 respectively.

There are 1800 resource units available every day and product A requires 20 units while B requires 12 units.

Both of these products require a production time of 4 minutes and the total available working hours are 8 in a day.

What should be the production quantity for each of the products to maximize profits?

In this case, the objective function in the problem will be



Max(sales)=max(25×1+20×2)

X1 is the units of product A produced

X2 is the units of product B produced

X1 and x2 are also called decision variables.

The constraints are resources and time in this case.
Resource Constraint

20*x1+12*x2<=1800
Time Constraint

4*x1+4*x2<=8*60

Let’s see how to resolve this problem in R


Load Packages

install.packages("lpSolve")
library(lpSolve)

Decision Variables

Set the coefficients of the decision variables

Objective.in<-c(25,20)

Constraint Matrix

Create constraint matrix

Differences between Association and Correlation

Const.mat<-matrix(c(20,12,4,4),nrow=2,byrow=TRUE)

Constraints

Define the constraints

Time_constraint<-8*60
Resouce_constraint<-1800

RHS for the constraints

Const.rhs<-c(Resouce_constraint, Time_constraint)

Direction

Constraints direction

Paired t test tabled value Vs p value

Const.dir<-c("<","<=")

Optimal Solution

Optimum<-lp(direction="max",Objective.in,Const.mat,Const.dir,Const.rhs)

Optimal values for x1 and x2 are

45, 75

The value of the objective function at an optimal point is

Optimum$objective

2625
Conclusion

From the above output, we can see that the company should produce 45 units of product A and 75 units of product B to get sales of $2625, which is the maximum sales that the company can get given the constraints.

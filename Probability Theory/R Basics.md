[1A](https://ocw.mit.edu/courses/18-05-introduction-to-probability-and-statistics-spring-2014/pages/r-tutorial-1a-basics/)
[1B](https://ocw.mit.edu/courses/18-05-introduction-to-probability-and-statistics-spring-2014/pages/r-tutorial-1b-random-numbers/)
# 1A Basics
## R as a Calculator  
The basic operations: *, +, -, /, ^
```R
> 2+3
[1] 5
> 2*3
[1] 6
> 2/3
[1] 0.6666667
> 2^3
[1] 8
> 2*(3+1)^2
[1] 32
```
Don’t worry for now about the `[1]`. It will play more of a role when R is printing numbers in a list.
## Using Variables
```R
> x = 2+3
# When you assign a value to a variable it does not echo the answer to the screen. You can see the value of x by just using x as a command.
>x
[1] 5
> y = 1+2
> x*y
[1] 15
> z = x^y
> z
[1] 125

# R has another notation for assignment: the arrow: <- . Many R programmers use this. It may seem odd to programmers coming from other languages.
> x <- 3
> x
[1] 3
> x <- 5.412
> x
[1] 5.412
```
## Vectors
A vector is a type of list. Often it is a list of numbers, but it can be a list of other types such as characters.  
You create vectors by using the `c( )` function.
```R
# A vector with 4 entries
> c(1, 2, 3, 4)
[1] 1 2 3 4
# You can store vectors in variables.
> x = c(1.1, 0.0, 3.14, 2.718)
> x
[1] 1.100 0.000 3.140 2.718

# Of course using the arrow instead of equal sign works here.
> x <- c(2,4,6)
> x
[1] 2 4 6

# Sequences of integers are so common that there is a shortcut for making them.
> 1:4
[1] 1 2 3 4
> 3:10
[1]  3  4  5  6  7  8  9 10
> 9:2
[1] 9 8 7 6 5 4 3 2

# A long vector will be displayed over several lines. At
the start of each line in brackets is the index of the first entry on that line.
> x = 1:40
> x
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 
 [15] 15 16 17 18 19 20 21 22 23 24 25 26 27 28 
 [29] 29 30 31 32 33 34 35 36 37 38 39 40
```
## Vector Arithmetic
You can add a number to a vector. This means adding the number to every element of the vector.
```R
> x = c(1,3,5)
> x + 7.1
[1]  8.1 10.1 12.1

# Subtraction, multiplication, division and powers work the same way.
> x = c(1,3,5)
> 7*x
[1]  7 21 35
> x/7
[1] 0.1428571 0.4285714 0.7142857
> 7/x
[1] 7.000000 2.333333 1.400000
> x^6
[1]     1   729 15625
> x^7
[1]     1  2187 78125
> 7^x
[1]     7   343 16807
```
You can add, subtract, multiply and divide vectors of the same size. 
## Accessing entries in a vector
```R
# Entries in vectors are found with the notation x[j]
> x = c(2,4,6,8,10)
> x[1]
[1] 2
> x[2]
[1] 4
> x[3]
[1] 6
> x[4]
[1] 8

# R allows you to access more than one entry at a time
# x has 8 elements
> x = 2*c(1,2,3,4,5,6,7,8)
> x
[1]  2  4  6  8 10 12 14 16
# Notice that we have to put a vector of indices inside the brackets to access the first and second entries in x
> x[c(1,2)]
[1] 2 4
> x[c(1,3,5)]
[1]  2  6 10
# We can access the same entry multiple times.
> x[c(2,2,2,1)]
[1] 4 4 4 2
# Using the colon method of creating vectors is useful here.
> x[2:5]
[1]  4  6  8 10
```
## Functions on Vectors
# We'll start with functions numbers
```R
> sin(1)
[1] 0.841471

> sin(1.4)
[1] 0.9854497

> sin(3)
[1] 0.14112

# R knows about pi
> pi
[1] 3.141593

> sin(pi/2)
[1] 1
> sin(pi/2)

# The exponential function is given by 'exp'.
> exp(0)
[1] 1

> exp(1)
[1] 2.718282

# Sin acts on vectors by taking the sin of each element.
> x = c(1,2,3,4)
> x
[1] 1 2 3 4
> sin(x)
[1]  0.8414710  0.9092974  0.1411200 -0.7568025

# exp also acts on vectors.
> x = c(1,2,3,4)
> exp(x)
[1]  2.718282  7.389056 20.085537 54.598150

# In 18.05 we will use the sum and mean functions on vectors. They take the sum and average respectively of the vectors entries
> x = 1:6
> x
[1] 1 2 3 4 5 6
> sum(x)
[1] 21
> mean(x)
[1] 3.5

# Example: find the sum of the integers from 1 to 1024.
> x = 1:1024
> sum(x)
[1] 524800

# This can be done in one command.
> sum(1:1024)
[1] 524800

# Example: find the sum of the squares of the integers from 1 to 1024.
> x = 1:1024
> sum(x^2)
[1] 358438400

# This can be done in one command.
> sum((1:1024)^2)
[1] 358438400
```
## Matrices
R’s method of creating matrices is a little bit clunky. It works by arranging the entries in a vector into rows and columns.
```R
# A vector of length 10 can be arranged as
a 2x5 or a 5x2 matrix
# Again the syntax is clunky but very clear
> x = 1:10
> x
 [1]  1  2  3  4  5  6  7  8  9 10
> y = matrix(x,nrow=2,ncol=5)
> y
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    3    5    7    9
[2,]    2    4    6    8   10
> z = matrix(x,nrow=5,ncol=2)
> z
     [,1] [,2]
[1,]    1    6
[2,]    2    7
[3,]    3    8
[4,]    4    9
[5,]    5   10

# Notice in the examples above that R builds the matrices one column at a time. That is, our vector 1 to 10 runs in sequence down the columns. For 18.05 this is usually fine. 

# However the matrix() function, like most R functions, has a lot of optional parameters that allow you to control its behavior. Here's how to make it buid a matrix by rows
> z = matrix(x,nrow=2,ncol=5, byrow = TRUE)
> z
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    2    3    4    5
[2,]    6    7    8    9   10
```
## Accessing Entries in Matrices
The square bracket notation is used by giving both the row and column indices.
```R
> x = 1:10
> y = matrix(x,nrow=2,ncol=5)
> y
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    3    5    7    9
[2,]    2    4    6    8   10
> y[1,1]
[1] 1
> y[2,3]
[1] 6
```
## Sums and Means on Matrices
```R
# Start by creating a matrix to practice on.
> x = 1:10
> y = matrix(x,nrow=2,ncol=5)
> y
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    3    5    7    9
[2,]    2    4    6    8   10

# To sum each of the columns we use the colSums function. 
> y
     [,1] [,2] [,3] [,4] [,5]
[1,]    1    3    5    7    9
[2,]    2    4    6    8   10

# y has five columns so colSums(y) produces 5 numbers.
> colSums(y)
[1]  3  7 11 15 19

# y has two rows so rowSums(y) produces 2 numbers.
> rowSums(y)
[1] 25 30


# Likewise rowMeans(y) and colMeans(y):
> rowMeans(y)
[1] 5 6
> colMeans(y)
[1] 1.5 3.5 5.5 7.5 9.5
```
## Getting Help
```R
# R and RStudio have complete documentation on all R functions. The lower right window in RStudio has a help tab you can use. The help contains a lot of information, so you will have to learn to filter out what you don't need.

# It's often faster to ask for help from the command line using a question mark.
> ?mean
# Try it, the result will appear in the help window.
```

# 1B Random Numbers
In order to run simulations of experiments with random outcomes we make use of R’s ability to generate random numbers. More precisely it generates a ‘***pseudo-random***’ number, which behaves in many ways like a truly random number.
## The function sample(x, k, replace = TRUE)
sample(x,k) generates a random permutation of k objects from the vector x. That is, all k choices are different.
```R
# start with a vector x with 5 elements.&nbsp; 
> x = 1:5 
> x 
[1] 1 2 3 4 5

# randomly sample 3 of the elements of x.&nbsp; 
> sample(x,3) 
[1] 2 5 1 
> sample(x,3) 
[1] 3 1 4 
> sample(x,3) 
[1] 1 2 5 
# Note every element is chosen at most once.

# randomly sampling 5 elements of x is a permutation of all 5 elements.&nbsp; 
> sample(x,5) 
[1] 1 3 2 5 4 
> sample(x,5) 
[1] 2 3 1 4 5

# You can't pick more than 5 different elements from a set of 5 things, so R gives an error.&nbsp; 
> sample(x,6) 
Error in sample.int(length(x), size, replace, prob) :&nbsp;&nbsp; 
 cannot take a sample larger than the population when 'replace = FALSE'
```

**Allowing repeated elements**     
Sometimes you want to allow repeats. For example when  we roll a die repeatedly we expect to see numbers repeating. We can think of this as picking a random element from a set and then putting it back, i.e. replacing it, so it can be drawn again.

In R we do this by setting the optional argument `replace=TRUE`
```R
# Note that we get can get repeated values&nbsp; 
> sample(x,3,replace=TRUE) 
[1] 3 1 4 
> sample(x,3,replace=TRUE) 
[1] 4 5 4 
> sample(x,3,replace=TRUE) 
[1] 2 1 5 
> sample(x,5,replace=TRUE) 
[1] 5 1 5 1 4 
> sample(x,5,replace=TRUE) 
[1] 3 5 5 2 1 
> sample(x,5,replace=TRUE) 
[1] 4 2 3 2 1


# Now there is no problem asking for more than 5 things from a set of 5 elements.&nbsp; 
> sample(x,12,replace=TRUE) 
[1] 1 1 2 1 4 2 3 4 1 2 4 5 
> sample(x,12,replace=TRUE) 
[1] 3 2 5 1 4 2 4 1 4 5 3 1
```

To generate an m x n array of random values we can use the function sample function followed by the matrix function.

Let’s simulate rolling a dice.  
We use 1:6 to make vector (1,2,3,4,5,6).
```R
# Generate a 3 x 4 array of random dice rolls.&nbsp; 
> y = sample(1:6, 12, replace=TRUE) 
> matrix(y,nrow=3,ncol=4) 
     [,1] [,2] [,3] [,4] 
[1,]    1    3    6    1
[2,]    2    2    3    6
[3,]    2    1    4    3

# Or we could make it a 2 x 6 array.   
> matrix(y,nrow=2,ncol=6)  
     [,1] [,2] [,3] [,4] [,5] [,6]
[1,]    1    2    2    6    4    6
[2,]    2    3    1    3    1    3
```
## Simulation
First let’s simulate rolling 1 die 3 times and checking if one of the rolls was a 6.
```R
# First we use sample to generate 3 samples from 1:6   
> x = sample(1:6,3, replace=TRUE)  
> x  
[1] 6 4 1

# To check if any of the 3 rolls are 6 we use the following command. It returns a vector of TRUE or FALSE depending on whether that entry of x is 6 or not. Note the use of the double equal sign. We can't use a single equal sign because that would mean 'set the value of x to 6'. Compare the result with the value of x above.   
> x == 6  
[1] TRUE FALSE FALSE

#  We can also see which elements of x are less than 6   
> x < 6  
[1] FALSE TRUE TRUE
```
Now let’s roll the die 5000 times and see what fraction of the rolls give 6. We expect that about 1/6 of them will be.
```R
# Simulate 1000 rolls   
> x = sample(1:6,1000, replace=TRUE)

# x == 6 gives a vector of TRUE or FALSE. R is clever, when we sum the vector: each TRUE counts as 1 and each FALSE counts as 0. So the sum is the number of TRUE's. In this case that means the number of 6's, which happens to be 168.    
> sum(x == 6)   
[1] 168

# Divide by 1000 to get the fraction of 6's.   
> sum(x == 6)/1000   
[1] 0.168

# Compare that with the theoretical value of 1/6.   
> 1/6   
[1] 0.1666667   
# Not bad!
```

Now let’s estimate the probability of getting at least one 6 in 4 rolls.

Goal: estimate the probability of getting at least one 6 in 4 rolls.     
Experiment: roll 1 die 4 times and check for a 6.  
Repeat the experiment 10 times and see what fraction of times this happens.
```R
# So you can see all the commands at once, we'll show them all and then explain them later. For commenting, we'll put a command number before each '>'    
1. > x = matrix(sample(1:6, 4*10, replace=TRUE), nrow=4, ncol=10)   
2. > x   
    [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10]   
[1,]    5    6    1    1    3    6    1    4    6     1   
[2,]    3    6    6    4    3    2    2    1    6     5   
[3,]    2    3    5    2    5    3    4    6    2     5   
[4,]    2    6    6    5    5    3    1    4    5     3
3. > y = (x==6)   
4. > y   
     [,1]  [,2]  [,3]  [,4]  [,5]  [,6]  [,7]  [,8]  [,9] [,10]   
[1,] FALSE  TRUE FALSE FALSE FALSE  TRUE FALSE FALSE  TRUE FALSE   
[2,] FALSE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE   
[3,] FALSE FALSE FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE   
[4,] FALSE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
5. > z = colSums(y)   
6. > z   
[1] 0 3 2 0 0 1 0 1 2 0
7. > z > 0   
[1] FALSE  TRUE  TRUE FALSE FALSE  TRUE FALSE  TRUE  TRUE FALSE   
8. > sum(z > 0)   
[1] 5
9. > mean(z > 0)   
[1] 0.5
```
    # Command 1: Generate a 4 by 10 random array. Each column represents one experimental trial of 4 rolls. The 10 columns represent the 10 trials.

    Command 2: Display x

    Command 3: See which of the rolls are 6’s. Note the double equals to check which rolls were 6. The result y is an array of TRUE or FALSE. You can check that it picks out the 6’s.

    Command 4: Display y

    Command 5: Sum each of the columns. The result is then number of 6’s in each trial (column).

    Command 6: Display z

    Command 7: If the column sum is greater than 0 there was at least one TRUE in the column, that is at least one 6. This command returns a vector of TRUE or FALSE representing  whether or not the experiment yielded a 6.

    command 8: sum the vector in command 7 to get the number of trials that yielded a 6. We see that 5 out of 10 trials did.

    command 9: The mean function is just the sum divided by the number of trials. This is just 5/10 = .5. Half the trials yielded a 10.

```R
# Let's repeat this but with 1000 trials instead of 10. Without all the comments it's pretty short.   
> x = matrix(sample(1:6, 4*1000, replace=TRUE), nrow=4, ncol=1000)   
> y = (x==6)   
> z = colSums(y)   
> sum(z > 0)   
[1] 525   
> mean(z>0)   
[1] 0.525
```
Our estimate of the probability of at least one 6 in 4 rolls is .525. This is pretty close to the theoretical value of .518.
```R
The dim() function   
# We can always check that x has 4 rows and 1000 columns using the dim() function.   
> dim(x)   
[1]    4 1000
```
## One more simulation
```R
# Goal: estimate the probability of getting a sum   
of 7 when rolling two dice.   
1. > ntrials = 10000   
2. > x = matrix(sample(1:6, 2*ntrials, replace=TRUE), nrow=2, ncol=ntrials)   
3. > y = colSums(x)   
4. > mean(y == 7)   
[1] 0.1658
```
    Command 1: We assign the number of trials to the variable ntrials. Writing code like this makes it easier to modify later. If we want to change the number of trials to 7 we just have to change this one line of code.   
    
    Command 2: we create 10000 columns with 2 rows. That is, we run 10000 experiments of rolling 2 dice.   
    
    Command 3: we sum each of the columns, i.e., we sum the two dice.   
    
    Command 4: we find the fraction of sums that are 7.

    Note, this is essentially the exact answer of 1/6.

Exercise: Try to estimate the probability of two sixes  when rolling two dice.
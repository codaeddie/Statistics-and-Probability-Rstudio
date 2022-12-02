# Statistics-and-Probability-Rstudio
A catalog of all my coursework and teaching for Statistics 550 at SDSU 
---

# Probability Distributions

### ⬇️⬇️⬇️READ ME FIRST⬇️⬇️⬇️

### Distributions

When working with different statistical distributions, we often want to make probabilistic statements based on the distribution. We typically want to know one of four things:

-   A random draw of values from a particular distribution.
-   The density (pdf) at a particular value.
-   The distribution (cdf) at a particular value.
-   The quantile value corresponding to a particular probability.

For each probability distribution there are typically four functions available that start with a `r`, `d`, `p`, and `q`.

-   The `r` function is the one that actually **simulates random numbers **from that distribution.
-   `d` for density, : compute the pdf or pmf
-   `p` for computing the cumulative distribution function
-   `q` for quantile function (inverse cumulative distribution)

If you’re only interested in simulating random numbers, then you will likely only need the `r `functions and not the others. However, if you intend to simulate from arbitrary probability distributions using something like rejection sampling, then you will need the other functions too.

!! **READ ME FIRST \*\***⬆️\***\*⬆️\*\***⬆️\*\*

## Binomial Distribution (✅ or ❌)

| `dbinom(x, size, prob)`                    | P(X = x), the probability that X = `x`                                           |
| ------------------------------------------ | -------------------------------------------------------------------------------- |
| `pbinom(q, size, prob, lower.tail = TRUE)` | P(X =&lt; q), the probability that X takes a value less than or equal to `q`     |
| `rbinom(n, size, prob)`                    | Generates numbers which follow a binomial distribution with the given parameters |

In R, the function `dbinom` provides the pmf of the binomial distribution:

`dbinom(x = success ,n = size, p = probability)`  gives:

P(X=x) for X∼Binom(n,p).

**Example** 🪙 For X the number of heads when three coins are tossed, the pmf is computed with R:

    x <- 0:3
    dbinom(x, 3, 0.5)
    ## [1] 0.125 0.375 0.375 0.125

* * *

**Example**🎲 What is the probability of getting exactly three “2's” in eight rolls?

```javascript
# P(X = 3)
#function dbinom has this frame:
#dbinom( success - in this case landing on a value three times,
#        size - in this case # of rolls,
#        probability of event happening -landing on a "2" = 1/6)

dbinom(3, 8, 1/6)
## [1] 0.125 0.375 0.375 0.125
```

* * *

**Example** 🎲

Suppose 100 dice are thrown. What is the expected number of sixes? What is the probability of observing 10 or fewer sixes?

We assume that the results of the dice are independent and that the probability of rolling a six is 1/6. The random variable X is the number of sixes observed, and

X∼Binom(100,1/6).

Then E[X]=100⋅16≈16.67.

That is, we expect 1/6 of the 100 rolls to be a six. The probability of observing 10 or fewer sixes in R:

    sum(dbinom(0:10,100,1/6)
    ## [1] 0.04269568

R also provides the function `pbinom`, which is the cumulative sum of the pmf.

`pbinom(x,n,p)`

This gives:

P(X≤x) for X∼Binom(n,p).

We could compute the probability of observing 10 or fewer sixes in 10 rolls as:

    # P(X <= 10)
    pbinom(10,100,1/6)
    ## [1] 0.04269568

* * *

**Example \*\***🗳️\*\*

Suppose Alice and Bob are running for office, and 46% of all voters prefer Alice. A poll randomly selects 300 voters and asks their preference. What is the expected number of voters who will report a preference for Alice? What is the probability that the poll results suggest Alice will win?

Let “success” be a preference for Alice, and X be the random variable equal to the number of polled voters who prefer Alice. It is reasonable to assume that

X∼Binom(300,0.46)

as long as our sample of 300 voters is a small portion of the population of all voters. We expect that 0.46⋅300=138 of the 300 voters will report a preference for Alice.

For the poll results to show Alice in the lead, we need (X > 150). To find this, we must compute:

1

−

P

(

X

≤

150

)

```javascript
[1-pbinom(150,300,0.46)]()
## [1] 0.07398045
```

There is about a 7.4% chance the poll will show Alice in the lead, despite her imminent defeat.

R provides the function `rbinom` to simulate binomial random variables. The first argument to `rbinom` is the number of random values to simulate, and the next arguments are **_n_** and **_p_**. Here are 15 simulations of the Alice vs. Bob poll:

```javascript
[rbinom(15,300,0.46)]()
##  [1] 132 116 129 139 165 137 138 142 134 140 140 134 134 126 149
```

In this series of simulated polls, Alice appears to be losing in all except the fifth poll where she was preferred by 165/300= 55%  of the selected voters.

We can compute P(X>150) using:

```javascript
X <- rbinom(10000,300,0.46)[mean(X > 150)]()
## [1] 0.0714
```

* * *

## Geometric Distribution ❌❌✅

X∼Geom(p)

> The number of failures before the first success occurs.

The functions `dgeom`, `pgeom` and `rgeom` are available for working with a geometric random variable X∼Geom(p):

-   `dgeom(x,p)` is the pmf, and gives P(X=x)
-   `pgeom(x,p)` gives P(X≤x)
-   `rgeom(N,p)` simulates N random values of X.

* * *

**Example \*\***🎲\*\*

A die is tossed until the first 6 occurs. What is the probability that it takes 4 or more tosses?

We define success as a roll of six, and let **_X_** be the number of failures before the first success. Then X∼Geom(1/6), a geometric random variable with probability of success 1/6.

We cannot perform the infinite sum with `dgeom`, but we can come close by summing to a large value of x:

```javascript
[sum(dgeom(3:1000, 1/6))]()
## [1] 0.5787037
```

Rather than summing the pmf, we may use `pgeom`:

```javascript
[1 - pgeom(2,1/6)]()
## [1] 0.5787037
```

Finally, we can use simulation to approximate the result:

```javascript
[X <- rgeom(10000,1/6)]()
[mean(X >= 3)]()
## [1] 0.581
```

* * *

**Example \*\***🏀\*\*

Let **_X_** be the random variable which counts the number of free throws Steph Curry makes before missing one. We model a Steph Curry free throw as a Bernoulli trial, but we choose “success” to be a missed free throw, so that P=0.1 and X∼Geom(0.1).

The expected number of “failures” is

E[X]=(0.90/0.1)=9

which means we expect Steph to make 9 free throws before missing one. To make 20 in a row,

P

(

X

≥

20

)

=

1

−

P

(

X

≤

19

)

,

```javascript
[1 - pgeom(19,0.1)]()
## [1] 0.1215767
```

we see that Steph Curry could run off 20 (or more) free throws in a row about 12% of the times he wants to try. **(This is not factual, please don't come at me sideways \*\***❤️\***\*)**

* * *

## Normal Distribution: 📊

| `dnorm(x, mean, sd)` | probability density function     | evaluate the Normal probability density (with a given mean/SD) at a point (or vector of points)                             |
| -------------------- | -------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| `pnorm(q, mean, sd)` | cumulative distribution function | evaluate the cumulative distribution function for a Normal distribution                                                     |
| `qnorm(p, mean, sd)` | quantile function                | returns critical values in the normal distribution for a given percentile with a given mean and a given standard deviation. |
| `rnorm(n, mean, sd)` | random number generator          | generate random Normal variates with a given mean and standard deviation                                                    |

* * *

We can use `pnorm()` to calculate cumulative probabilities. For example, let’s calculate the probability that our random variable X takes a value less than or equal to -1.

```javascript
pnorm(-1, 0, 1)
## [1] 0.1586553
```

We can also calculate the probability that X takes some value within a certain interval. For example, let’s calculate P(-2 &lt;= X &lt;= 1)

```javascript
pnorm(1, 0, 1) - pnorm(-2, 0, 1)
## [1] 0.8185946
```

The R function `pnorm` computes the cdf of the normal distribution, as

`pnorm(x)` =P(Z≤x).

Using this, we can compute the probability that Z lies within 1, 2, and 3 standard deviations of its mean: (It's okay if you have no idea what this all means)

![image.png](media_Probability%20Distributions/image.png)

Now lets plot the Normal curve in Rstudio

```javascript
# create a sequence of 100 equaly spaced numbers between -4 and 4
temp1 <- seq(-4, 4, length=100)

#create a vector of values that shows the height of the distribution
temp2 <- dnorm(temp1)

 # plot x and y as a scatterplot with connected lines (type = "1")
 # also add labels on your x-axis
 plot(temp1,temp2, type= "1", lwd= 2, axes= FALSE, xlab= "", ylab= "")
 axis(1, at= -3:3, labels=c("-3s","-2s","-1s","mean","1s","2s","3s"))
```

This is the output:

![image.png](media_Probability%20Distributions/940f98c9-04ff-4a33-9332-538cc888f41a_image.png)

* * *

**Example \*\***👶\*\*

The birth weights of babies are known to be normally distributed with a mean weight of 120 ounces and a standard deviation of 20 ounces.

-   A “low birth weight” baby is one that is born in the 5th percentile of this distribution. This is of concern for a variety of reasons, such as the fact that low birth weight babies have lower rates of survival than normal birth weight babies.
-   A baby that is born at this weight or lower is considered low birth weight.
-   We can use the `qnorm()` function to do this.
-   The first argument 0.05 is the percentile we’re aiming for (in this case the fifth percentile)
-   The second and third arguments are the mean and standard deviation of the normal distribution curve that we’re considering, in this case 120 and 20 respectively.

```javascript
qnorm(0.05, 120, 20)
## [1] 87.10293
```

This returns a value of about 87.1 ounces. About 5.4lbs.

⤵️⤵️⤵️⤵️

Another birth weight category is “very low birth weight”, which is a birth weight less than or equal to 52 ounces. In what percentile is this weight threshold?

To answer this question, we can use `pnorm()`.

```javascript
pnorm(52, 120, 20)
## [1] 0.0003369293
```

⤵️⤵️⤵️⤵️ ⤵️⤵️⤵️⤵️

Now let’s use the information we’ve found so far to answer a trickier question: given that a baby is born with low birth weight, what is the probability that this baby has very low birth weight?

This is a conditional probability question. The most transparent and intuitive way to answer this is to save the two relevant probabilities that we need to calculate the conditional one as variables and then use them together in a subsequent step to calculate the answer.

```javascript
pLow <- pnorm(qnorm(0.05, 120, 20), 120, 20)
pVeryLow <- pnorm(52, 120, 20)

pVeryLowGivenLow <- p_very_low / p_low
pVeryLowGivenLow

## [1] 0.006738585
```

* * *

**Example \*\***📝\*\* 💯

ACT scores are normally distributed with a mean of 18 and a standard deviation of 6. SAT scores are normally distributed with a mean of 500 and a standard deviation of 100.

Suppose a student named Jill takes the SAT and gets a score of 680. Her classmate Jack plans to take the ACT. What score does Jack need to get so that he does as well as Jill?

This question seems poorly phrased at first. How can we compare SAT and ACT scores if they’re measured on different scales? Since these test scores are normally distributed, all we need to do is standardize the scores for both tests.

We can do this using z scores, which is something that you have certainly learned about if you’ve taken a Statistics class before. Z scores for SAT and ACT scores will make these test scores comparable because they’ll be on the same scale. We will then compare them using the standard normal distribution, which has a mean of 0 and a standard deviation of 1.

To calculate z scores, we’re going to create a simple function called `z_score()` which contains the formula for calculating this value. Its arguments are the variables that we need for this formula. Let’s try it out on Jill’s SAT score of 680.

    [z_score <- function(x, mean, sd){]()
    [  z_score <- (x - mean) / sd]()[  ]()
    [  return(z_score)]()[}]()[z_score(680, 500, 100)]()
    }

    z_score(680, 500, 100)

    ## [1] 1.8

    [pnorm(1.8)]()
    ## [1] 0.9640697

This answer tells us that Jill’s score is 1.8 standard deviations above the average for the SAT. This corresponds to a score that is in about the 96th percentile, meaning she did better than about 96% of students who took this test.

⬇️⬇️⬇️⬇️⬇️⬇️⬇️⬇️

In order for Jack to do equally well on the ACT, he needs to score in the same percentile for that test. What score does this correspond to for this test? Once again we turn to `qnorm()` for this calculation.

```javascript
qnorm(pnorm(1.8), 18, 6)
## [1] 28.8
```

According to our calculation, in order for Jack to do as well on the ACT as Jill did on the SAT, he would need to get a score of 28.8.

* * *

## Poisson Distribution🃏

| `dpois(x, lambda)`                    | P(X = x), the probability that there will be `x` successes per period for an event with an average number of `lambda` successes                                                                                                                                                                              |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `ppois(x, lambda, lower.tail = TRUE)` | P(X &lt;= x), the cumulative probability that there will be `x` or fewer successes per period for an event with an average number of `lambda` successes. Returns P(X > x), the cumulative probability that there will be more than `x` successes per period for the same variable when `lower.tail = FALSE`. |
| `rpois(n, lambda)`                    | Returns `n` randomly generated numbers that follow a Poisson distribution with an average number of `lambda` successes                                                                                                                                                                                       |

* * *

**Example \*\***👶\*\* Data from the maternity ward in a certain hospital shows that there is a historical average of 4.5 babies born in this hospital every day. What is the probability that 6 babies will be born in this hospital tomorrow?

First, let’s calculate the theoretical probability of this event using `dpois()`.

The number of successes we’re considering is 6, so we will set `x = 6`.

Additionally, this historical average of 4.5 babies per day is our value for lambda, so we will set `lambda = 6`.

```javascript
dpois(6, 4.5)
## [1] 0.1281201
```

The theoretical probability of 6 babies being born tomorrow if the historical average is 4.5 is about 13%.

🆗 What about the probability of more than 6 babies being born?

```javascript
ppois(6, 4.5, lower.tail = FALSE)
## [1] 0.1689494
```

This theoretical probability is about 16.9%. Remember that cumulative probability functions in R calculate P(X > x) when `lower.tail = FALSE`. Here it calculated P(X > 6) = P(X >= 7).

* * *

**Example \*\***🚘\*\* Suppose that the number of accidents per month at a busy intersection in the center of a certain city is 7.5. This event follows a Poisson distribution and `lambda = 7.5`

\`\`

Every time an accident occurs at this intersection, the city government has to pay about $25,000 to clean up the area. What is the average cost of these accidents per year?

-   This question is a lot easier than it probably sounds. We know that the average number of accidents per month is 7.5.
-   We also know that there are 12 months in a year, so the average number of accidents per year is just the product of these two numbers.
-   Finally, since we also know the average cost per accident, the average cost of accident clean-up per year for this city is just the product of these three numbers.

```javascript
7.5 * 12 * 25000
## [1] 2250000
```

In a typical year, this city can expect to pay about $2.25 million in accident clean-up costs for this intersection.

### 🆗 🆒 Now do it using Poisson ⤵️⤵️⤵️

-   First, we’ll simulate the annual accident cost for one year. We’ll use `n = 12` because `lambda = 7.5` represents the average number of accidents per month, and we want to simulate 12 months. We will save these results as a variable called `accidents`.
-   Next, we’ll multiply each element inside of `accidents` by 25,000 in order to calculate the average cost per month of accident clean-up. Finally, we will add these monthly costs together to get the total annual cost.

```javascript
accidents <- rpois(12, 7.5)
cost <- sum(25000 * accidents)

cost
## [1] 2325000
```

In this simulation, the total cost of cleaning up after accidents was about $2.32 million.

Now we’re going to use `replicate()` to simulate accident costs at this intersection for 1,000 years. We’re using a high number so that we can get a good look at what this distribution looks like.

```javascript
accidents <- rpois(12, 7.5)
costSim <- replicate(1000, sum(25000 * accidents))
mean(costSim)
## [1] 2475000
```

In this simulation, the mean cost of accident clean-up is about $2.48 million, which is quite close to the theoretical total.

* * *

Lastly, the continuous uniform distribution, meaning that every value between the two end points has an equal probability of being sampled.

Here's the code to produce 100 values between 1 and 100, and then print them

```javascript
RandomNumbers <- runif(100, 1, 100)
RandomNumbers
##  [1] 22.290 33.655 89.835 38.535 24.601 11.431  7.047 94.958 83.703 76.847
##  [11] 58.429 20.667 25.796 91.821  8.741 65.696 24.262  8.077 51.399 19.652
##  [21] 64.883 33.258 55.488  6.828 14.925 11.480 72.783  2.549 78.706 49.563
##  [31] 10.829 27.653 70.304 96.759 12.614 66.610 82.467  8.506 71.719 86.586
```

* * *

          

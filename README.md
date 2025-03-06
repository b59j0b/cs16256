java c
BCSC/CSC/DSCC 229, DSCC 449: Computer Models of Human 
Perception and Cognition 
Homework Assignment #2 
Instructions: Answer all questions below. Include all requested calculations and graphs. Also include the Python code that you wrote to answer the questions. When writing text or equations, please write NEATLY!
(0) (Part A) At the top of the document you turn in, place your name and the date. (Part B) Next, please take the honor pledge. That is, write (by hand using a pen): “I affirm that I have not given or received any unauthorized help on this assignment, and that this work is my own.” Then sign your name.
(1) [WARNING: This problem is mathematically challenging. Don’t be surprised if you struggle with it. Indeed, it may be smart to first work on other homework problems, and then return to this problem if time permits.] (Adapted from Problem 3.4 from an early draft of the textbook by Ma, K¨ording, and Goldreich) Many Bayesian inference problems involve a product of two or more Gaussians (also known as normal distributions). A convenient property of Gaussians is that their product is also Gaussian. In this problem, we will lead you through an example to derive this property yourself. Consider an observer who infers a stimulus s from a measurement x (this is the scenario we considered in the lecture titled “Building a Bayesian Model”). Suppose the stimulus distribution p(s) (this is the prior distribution) is a Gaussian with mean µ and standard deviation σs, and suppose the measurement distribution p(x|s) (this is the likelihood function) is a Gaussian distribution with mean s and standard deviation σ.
(a) Write down the equations for p(s) and p(x|s).
(b) Use Bayes’ rule to write down the equation for the posterior distribution p(s|x).
Substitute p(x|s) and p(s), but do not simplify.
The numerator is a product of two Gaussians. The denominator p(x) is a normalization factor that ensures that the integral of the posterior distribution equals 1. For now, we will ignore the denominator and focus on the numerator.
(c) Apply the rule eA eB = eA+B to simplify the numerator.
(d) Expand the two quadratic terms in the exponent.
(e) Rewrite the exponent to the form. as2 + bs + c, where a, b, and c are constants.
(f) Rewrite the expression you obtained in (e) in a simpler form, ec1(s+c2)2+c3, with c1, c2, and c3 constants. [Hint: any quadratic function of the form. as2 + bs + c can be written as

This re-writing is known as “completing the square”.]
(g) Now rewrite your expression into the form.

Express µcombined and σcombined in terms of x, σ, µ, and σs. [Hint: Recall we’re considering the “Normal-Normal” model. In this model, the posterior distribution is a normal distribution with mean µcombined and variance σcombined2. Recall the formulas for µcombined and σcombined2.]
(h) Recall that p(s|x) is a distribution and that its integral should therefore be equal to 1. However, the expression that you obtained in (g) is not properly normalized because we ignored p(x). Modify the expression such that it is properly normalized, but without explicitly calculating p(x). [Hint: Note that eZis a constant that does not depend on s?]
(2) (Adapted from Problem 3.2 from an early draft of the textbook by Ma, K¨ording, and Goldreich) In this problem, we numerically calculate a posterior distribution. Suppose the stimulus distribution p(s) is Gaussian with mean 20 and standard deviation 4. The measure-ment distribution p(x|s) is Gaussian with standard deviation σ = 5. A Bayesian observer infers s from an observed measurement x = 30. We are now going to calculate the posterior probability density using numerical methods (coded in Python).

Figure 1: Example of a graph for Question 2 showing a likelihood function, a prior distribution (values sum to 1/stepsize), and a posterior distribution (normalized and then scaled so its values sum to 1/stepsize).
(a) Define a vector of hypothesized stimulus values s: (0, 0.2, 0.4, . . . , 40).
(b) Compute the likelihood function p(x|s) and the prior p(s) on this vector of s values.
[Hint: Without extra work, the values of the prior distribution will not sum to one (instead, they should sum to 1/stepsize where stepsize = 0.2). That is because we are approximating a continuous distribution by a discrete distribution. In addition, the values of the likelihood function will not sum to one. (But keep in mind that the likelihood function is not a distribution, and thus its values do not need to sum to one.)]
(c) Multiply the likelihood and the prior elementwise. In Python, elementwise multiplication of two vectors can be achieved using the “*” command.
(d) Divide this product by its sum over all s (normalization step). This step yields the posterior distribution p(s|x). After completing this step, the posterior probabilities will sum to one.
(e) Convert this posterior probability mass function into a probability density function by dividing by the step size you used in your vector of s-values (e.g., 0.2). (Before this conversion, the values of the posterior will sum to 1. After this conversion, the values of the posterior will sum to 1/stepsize.)
(f) Plot the likelihood, prior (values sum to 1/stepsize), and posterior (normalized and then scaled so its values sum to 1/stepsize) in the same plot. [Hint: See Figure 1.]
(g) Is the posterior wider or narrower than the likelihood and prior? Do you expect this based on the equations we discussed?
(h) Change the standard deviation of the measurement distribution to a very large value (e.g., σ = 10) and redraw your plot. What happens to the posterior? Can you explain this?
(i) Change the standard deviation of the measurement distributio代 写BCSC/CSC/DSCC 229, DSCC 449: Computer Models of Human Perception and Cognition Homework Assignment #2Python
代做程序编程语言n to a very small value (e.g., σ = 1) and redraw your plot. What happens to the posterior? Can you explain this?
(3) (Adapted from an early draft of the textbook by Ma, K¨ording, and Goldreich) Repeat Question (2), but instead of starting with a value of the measurement x, start with a value of the stimulus s = 10. Based on this value of s, draw a random value of x from the measurement distribution p(x|s) (with σ = 5). (Although you know the true value of s, pretend you don’t know this value. Your goal is to infer the posterior distribution of s given this value of x.) Repeat this process nine times (each time you will sample x and then infer posterior p(s|x)). Make a figure with nine graphs, each graph showing the likelihood function, prior distribution (values sum to 1/stepsize), and posterior distribution (normalized and then scaled so its values sum to 1/stepsize) for an individual repetition. You should observe that, repetition to repetition, the likelihood function and posterior probability density function “jump around”. Observe how the posterior shifts under the influence of the “jumping” likelihood function and stationary prior. Explain.
(4) (Adapted from an early draft of the textbook by Ma, K¨ording, and Goldreich) Continuing from Questions (2) and (3), generate a distribution of maximum-a-posteriori (MAP) and maximum likelihood (ML) estimates by:
(a) drawing a single s from the stimulus distribution p(s);
(b) drawing a single x from the measurement distribution p(x|s) (with σ = 5), and calculating the posterior distribution p(s|x) (normalized and scaled so that its values sum to 1/stepsize).
(c) For each of 1000 repetitions of (a) and (b), show a scatter plot of the MAP estimate (y-axis) against the true stimulus s (x-axis). On a separate graph, plot the MLE (i.e., measurement x) against the true stimulus s. [Hint: See Figure 2.]

Figure 2: (Left) Scatter plot of the MAP estimate (y-axis) against the true stimulus s (x-axis). (Right) Scatter plot of the MLE estimate (y-axis) against the true stimulus s (x-axis). Each plot contains 1000 dots, one dot for each repetition.
(d) Repeat (a), (b), and (c) twice. In the first repetition, make the measurement standard deviation large (σ = 10). In the second repetition, make the measurement standard deviation small (σ = 1). When this standard deviation is small, the MAP and MLE plots should look similar. Why? When this standard deviation is large, the MAP plot looks flat, whereas the MLE plot looks very scattered. Why?
(5) (Adapted from Problem 5.7 from an early draft of the textbook by Ma, K¨ording, and Goldreich) In Chapters 3, 4, and 5, we were able to derive analytical expressions for the posterior distribution and the response distribution. For more complex psychophysical tasks, however, analytical solutions often do not exist but we can still use numerical methods. To gain familiarity with such methods, we will work through the cue combination model of Chapter 5 using numerical methods. We assume that the experimenter introduces a cue conflict between the auditory and the visual stimulus: sA = 5 and sV = 10. The standard deviations of the auditory and of the visual noise are σA = 2 and σV = 1, respectively. We assume a flat (uniform) prior over s.
(a) Randomly draw an auditory measurement xA and a visual measurement xV from their respective measurement distributions. (It’s okay if a measurement has a negative value.)
(b) Plot the corresponding elementary likelihood functions, p(xA|s) and p(xV |s), in one sfigure. (Recall that likelihood functions do not need to be normalized.) For the range of possible s values, generate an array of values that start at -10, end at 30, and have a stepsize of 0.2.
(c) Calculate the combined likelihood function, p(xA, xV |s), by numerically multiplying the elementary likelihood functions in Python. Plot this function. (Again, this function does not need to be normalized.)
(d) Calculate the posterior distribution p(s|xA, xV) by normalizing and then scaling the combined likelihood function. (The posterior distribution p(s|xA, xV) should be normalized and then scaled so that its values sum to 1/stepsize.) Plot this distribution in the same figure as the likelihood functions.
(e) Use Python to find the MAP estimate of s (i.e., the value of s at which the posterior distribution p(s|x) is maximal).
(f) Compare with the MAP estimate of s computed with an analytic equation using the measurements drawn in (a). For convenience, here is the analytic equation:

(g) In the above, we simulated a single trial and computed the observer’s MAP estimate of s, given the noisy measurements xA and xV on that trial. If an analytical solution does not exist for the distribution of MAP estimates, we can repeat the above procedure many times to approximate this distribution. Here, we practice this method even though an analytical solution is available in this case. Draw 100 pairs (xA, xV ) and numerically compute the observer’s MAP estimate of s for each pair as in (e).
(h) Compute the mean of the MAP estimates obtained in (g) and compare with the mean

Figure 3: (Left) Histogram representation of p(sMAP|xA, xV) based on 100 MAP estimates. estimate predicted by an analytic equation that uses the true values for sA and sV:

(i) Make a histogram representation of p(sMAP|xA, xV) based on the 100 MAP estimates obtained in (g) (in Python, use the “numpy.histogram” function). [Hint: See Figure 3.]
(j) Relative auditory bias is defined as the mean MAP estimate minus the true auditory stimulus, divided by the true visual stimulus minus the true auditory stimulus. Compute relative auditory bias for your estimates.


         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com

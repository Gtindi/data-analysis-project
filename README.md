# data-analysis-project: The Tips Data Set 
## Elizabeth Daly

### HDip Data Analytics 2019 Fundamentals of Data Analysis Assessment

Git-hub repository at:
https://github.com/elizabethdaly/data-analysis-project.git

- Jupyter notebook: tips-data-analysis.ipynb
- Dataset: tips.csv

![Tips](images/tip.jpg)

# Table of contents
1. [Introduction](#introduction)

2. [Description of the data set](#section1)

3. [Regression](section2)
    
3. [Relationships between variables](#section3)
    
4. [Work done by other people on the Tips data set](#section4)
    
5. [Conclusion](#conclusion)

6. [References](#references)

## 1. Introduction <a name="introduction"></a>
This README describes work done on the Tips data set for the Fundamentals of Data Analysis module assessment due 29 November 2019. Resources used include Python and associated packages Jupyter, matplotlib, and Seaborn. The analysis takes the form of a single Jupyter notebook of filename given above. To view this file, download it from this repository and run Jupyter notebook, which comes as part of the Anaconda distribution of Python (as do the other packages listed above). Alternatively, view a static version of the notebook (by providing its GitHub url) using Jupyter Nbviewer. The Tips data set is incuded in the Seaborn visualization library. It can be loaded provided one has access to the internet when running the notebook. For the sake of completeness, I have downloaded the data set from the site referenced in the project instructions, and I include it in this repository as a csv file. I have also tried to break the Jupyter notebook into sections which roughly correspond to the sections of this README.

##  2. Description of the data set <a name="section1"></a>
The Tips data set contains 244 rows of data relating to tips left in a restaurant. I will assuming that the currency is $, as tipping is standard practice in the US. The data set includes the total bill, tip, number in the party, day of week, time of day, gender of the diner, and whether or not they are a smoker. I would say that the basic question is: does the tip amount depend on the total bill? One can also ask if the other variables influence the tip amount. Some of these questions will be addressed in section 3. <!--put in a ref-->
I often use sites such as Medium.com to see how other people have investigated data sets using Python. Two examples of such exploratory data analyses are given in the reference list. The very first step is always to check if the data needs cleaning by looking for duplicate rows, zero values or NaNs where they shouldn't be, etc. Our data set is small enough to inspect visually and it looks fine. Counting the number of valid entries in each column confirms this. 

Pandas **decribe()** can provide a quick summary of the data set as outlined in the notebook. However, without looking at the data in more detail, we cannot yet state what we think a typical diner is. What I mean is, just because most of the diners are male, smokers, and eating dinner on Saturday when we consider one variable at a time, that doesn't mean that all of these conditions are met simultaneously. 


##  3. Regression <a name="section2"></a>
For this part of the assessment, we have been asked to analyse if there is a relationship between the total bill and the tip amount. The simplest relationship would be a linear one. That's reasonable when we consider that tips (especially in the US) are usually a fixed percentage of the total bill. In the notebook we first use Seaborn to visualize any linear relationships between our two variables of interest using Seaborn regplot. This does not give us any fitting parameters such as the slope and intecept of the linear fit, or any metrics to assess the quality of the fit, but it's a good start. We then move on to using two packages, Statsmodels and scikit-learn, to perform linear regression and return fitting parameters and metrics. Statsmodels is a Python package for performing statistical analysis of data - we are interested in the OLS (Ordinary Least Squares) module for performing linear regression. OLS involves fitting a linear model with coefficients to minimize the residual sum of squares between the observed data points and the targets predicted by the linear approximation. Scikit-learn is a machine learning package which can also perform OLS fitting. Strictly speaking there is no need to perform regression with both packages, but I do it once in the notebook and then stick to scikit-learn, which will be useful if we want to make any predictions using the dataset. In regression, R<sup>2</sup> is the coefficient of determination, a measure of how close the data points are to the fitted regression line; or how much of the variation in the data is explained by the linear model. It ranges from 0 to 1, and in general, higher values of R<sup>2</sup> are better. However, as the minitab [] link in the references discusses, that's not the full story. That reference states that in fields which try to predict human behaviour (the tips dataset falls into this category), values of R<sup>2</sup> less that 0.5 are not unusual; we find R<sup>2</sup> = 0.457 on average. It's also important to take into account the appropriateness of the model when assessing R<sup>2</sup>. Another model (perhaps a high-order polynomial fit) may produce a better R<sup>2</sup> but wouldn't be a good way to model how tip amount varies with total bill. The results of regression on all of the data, and on subsets of it, are presented in the table below.

Fit         | R<sup>2</sup> | slope | intercept
------------|---------------|-------|----------
All           | 0.457     | 0.105 | 0.920     |
size = 2      | 0.232     | 0.078 | 1.292     |
size = 2,3,4  | 0.438     | 0.105 | 0.920     |
F smokers     | 0.266     | 0.068 | 1.701     |
M smokers     | 0.232     | 0.073 | 1.425     |
F non-smokers | 0.686     | 0.128 | 0.452     |
M non-smokers | 0.670     | 0.140 | 0.348     |
day = Thur    | 0.660     | 0.128 | 0.512     |
day = Fri     | 0.597     | 0.095 | 1.109     |
day = Sat     | 0.495     | 0.121 | 0.519     |
day = Sun     | 0.251     | 0.070 | 1.753     |

What can we conclude from this? That the data is fitted well by a linear model for non-smokers (regardless of sex) and for day = Thursday; these subsets result in the largest R<sup>2</sup> values and also high slopes. Maybe considering data from non-smokers on Thursday would produce the most reliable predictions of tip given total bill?

We can use our linear regression parameters to predict the tip amount for any total bill, say a bill of $100. 
- Using all of the data, we predict a tip of $11.42 for this total bill amount;
- For male non-smokers only, we predict a tip of $14.32;
- Considering data from Thursday alone, we predict a tip of $13.29;
- In contrast, Sunday data predicts just $8.77 as a tip.

As the average total bill in this restaurant is just less than $20 and the maximum is about $50 it's unlikey that anyone would ever spend $100 here in the first place!

ML predict classify?

## 4. Relationships between variables <a name="section3"></a>

## 5. Work done by other people on the Tips data set <a name="section4"></a>
Regression using all cat vars.

## 6. Conclusion <a name="conclusion"></a>

## 7. References <a name="references"></a>
- [1]  Anaconda Distribution
https://www.anaconda.com/
- [2] Python Software Foundation
https://www.python.org/
- [3] Project Jupyter
https://jupyter.org/
- [4] Sharing Jupyter notebooks
https://nbviewer.jupyter.org/
- [5] seaborn: statistical data visualization
https://seaborn.pydata.org/index.html#
- [6] matplotlib: Python plotting library
https://matplotlib.org/
- [7] The Tips dataset from Michael Waskom
https://github.com/mwaskom/seaborn-data/blob/master/tips.csv
- [8] Description of what is contained in the tips set
https://www.kaggle.com/ranjeetjain3/seaborn-tips-dataset
- [9] How to investigate a data set with Python
https://towardsdatascience.com/hitchhikers-guide-to-exploratory-data-analysis-6e8d896d3f7e
- [10] Data analysis with Python
https://medium.com/@onpillow/01-investigate-tmdb-movie-dataset-python-data-analysis-project-part-1-data-wrangling-3d2b55ea7714
- [11] Python for Data Analysis: Data Wrangling with Pandas, NumPy, and IPython. 
Wes McKinney. ISBN-13: 978-1491957660 ISBN-10: 1491957662
- [12] Pandas In 10 Minutes || Wes McKinney
https://www.youtube.com/watch?v=1MGCD8SQp3k
- [13] Good description of quartiles on Seaborn plots
https://towardsdatascience.com/analyze-the-data-through-data-visualization-using-seaborn-255e1cd3948e
- [14] Ordinary Least Squares in statsmodels
https://www.statsmodels.org/dev/examples/notebooks/generated/ols.html
- [15] Generalized Linear Models in scikit-learn
https://scikit-learn.org/stable/modules/linear_model.html#ordinary-least-squares
- [16] How to run Linear regression in Python scikit-Learn
https://bigdata-madesimple.com/how-to-run-linear-regression-in-python-scikit-learn/
- [17] A beginner’s guide to Linear Regression in Python with Scikit-Learn
https://towardsdatascience.com/a-beginners-guide-to-linear-regression-in-python-with-scikit-learn-83a8f7ae2b4f
- [18] Regression Analysis: How Do I Interpret R-squared and Assess the Goodness-of-Fit?
https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit
- [19] PYTHON MACHINE LEARNING EXAMPLE – LINEAR REGRESSION
https://devarea.com/python-machine-learning-example-linear-regression/#.XbbfgOj7Q2w
- [20] STAT 503 Case Study 1: Restaurant Tipping
https://dicook.public.iastate.edu/stat503/05/cs-tips2.pdf

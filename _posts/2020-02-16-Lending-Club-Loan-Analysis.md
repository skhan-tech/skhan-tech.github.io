## Four Secrets Hidden within Lending Club Loan Data

*By: Saleem Khan*

![Loans]({{ site.url }}/images/banknotes.jpg)

<sub><sup>Photo by Alexander Mils from Pexels</sup></sub>

# Key Takeaways
  - **7.41%**  
    - The percent of overall bad loans within the Lending Club portfolio in 2018.
  - **22.89%** 
    - The actual percent of bad loans when removing "current" loans which have not fully paid out yet.
  - **Small Businesses** 
    - Tend to default the most when examining the most frequent borrowers.
  - **Machine Learning** 
    - Can be used to create a portfolio which beats the average total return for randomly chosen loans.

# Background
Founded in 2006, Lending Club is the world's largest peer-to-peer lender. They disrupted the traditional bank-based personal lending market by allowing retail investors to lend directly to individuals wanting to borrow. The Lending Club loan pool has grown steadily since its founding. In the last 3 years the platform originated nearly $18B in new loans.

# Problem Statement
  - **What is the actual default rate for Lending Club loans?**
    I wanted to take a deeper dive into the actual default rates within Lending Club so investors can make a more informed decision about their risks. 
  - **Who tends to defaults the most?**
    I wanted to see whether risk was pooled within a certain borrower type or loan purpose so we can make sure to have a diversified portfolio.
  - **Is it possible to use a classification model to determine, with high accuracy, whether a loan will default?**
    I wanted to use a classification model to determine whether we can beat the average total return for a randomly selected pool of loans. 
    
# Exploratory Data Analysis
Lending Club is quite unique in that it offers all members access to loan data going back to their inception. If you visit the [Lending Club Statistics](https://www.lendingclub.com/statistics/additional-statistics?) page you will be able to download data and statistics going back to 2007. However, for the purpose of this excercise I decided to look at the past three years worth of data. 

After downloading the dataset one of the first things you notice is how verbose it is. There are nearly 150 unique columns of information ranging from the basics (e.g. loan amount, debt-to-income and interest rate) through to detailed attributes such as the number of derogatory public records and tax liens. This makes the dataset increbily rich and full of potential predictive power. 

![LoansByStatus]({{ site.url }}/charts/loans_by_loan_status.png)

A majority of the loans within the 2018 dataset are "current". Lending Club distinguishes between seven distinct loan statuses. However, for my goal of generating a machine learning model there are really only two statuses that I care about: whether a loan turned out to be a good loan (i.e. fully paid) or a bad loan (i.e. default or charged off). These two states will be my dependant variable (i.e. the output i'm trying to predict) in my machine learning model. One thing to note here also is that I am not including any loans that are late or in a grace period. As you can see from the chart above these statuses don't occur very often and would not be statistically relevant since we would not have outcomes that can be included in our dependent variable.

**What is the Overall Default Rate for Lending Club Loans?**

This is a bit of a perspective-based question. It really depends on whether you only want to look at loans where there is an outcome (e.g. a binary answer of wheter the loan defaulted or not) or whether you wanted to look at the entire Lending Club portfolio en masse. 

| Overal      | Count       | Percent |
| ----------- | ----------- |---------|
| Good Loans  | 458,551     |92.59%   |
| Bad Loans   | 36,691      |7.41%    |

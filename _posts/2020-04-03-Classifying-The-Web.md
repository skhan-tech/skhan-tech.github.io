## Big Data & Machine Learning for B2B Marketers

*By: Saleem Khan* 

![Marketers]({{ site.url }}/images/top-view-photo-of-people.jpg)

# Key Takeaways
  - **25.1%**  
    - The approximate percentage of websites that can be classified as businesses or e-commerce related on the open web.
  - **650 Million** 
    - The number of web pages that are potential businesses that B2B marketers could market to. This number is based on 2.6 Billion web pages collected in February of 2020 by a web archive called Common Crawl.
  - **11 to 1** 
    - Based on the above analysis, for every 11 people in the world there is one business.

# Background
In this excercise I will be examining the use of web archive data to produce valuable insights and data assets for B2B marketers. Specifically, knowing whether a website is a business or not is a very important first step. I will be walking through the steps required to produce a dataset that can put data scientists on a path to extracting this valuable information for their marketing teams. 

# Problem Statement
  - **Is it possible to use data from the web to identify businesses?**
  
    I wanted to develop a machine learning model that can look at the raw text of a web page and determine whether it is a business or not. 
   
# Goal
The ultimate goal here is to use a classifier to produce a curated list of business websites that can then be further categorized based on keywords. These further categorizations will, for instance, classify a business as being a pizza parlor, a flower shop or a bank. This sort of information is key in targeted B2B marketing. A final goal would be to pull all relevant contact information such as e-mail  phone and address.

# Approach
The approach I will be taking here is threefold:

1. **Dataset** 

<img src="../images/common-crawl.png" alt="Common Crawl" title="Common Crawl" width="200" height="75" />

[Common Crawl](http://www.commoncrawl.org) is an open repository of web crawl data. This data is refreshed monthly with a history that goes back to 2011. Each month contains nearly 260 Terabytes of information. To put this number in perspective, if you were to print out all this monthly information you would have a stack of papers about 16,000 miles tall. That is enough to wrap more than half way around the circumfernce of the Earth. All of the data in CommonCrawl from 2011 to the present day would take you to the moon and back over 6 times!

2. Classification

<img src="../images/scikit_learn.png" alt="Common Crawl" title="Common Crawl" width="200" height="75" />


<img src="../images/spark-logo.png" alt="Common Crawl" title="Common Crawl" width="200" height="75" />
<img src="../images/scikit_learn.png" alt="Common Crawl" title="Common Crawl" width="200" height="75" />
<img src="../images/amazon-s3.png" alt="Common Crawl" title="Common Crawl" width="200" height="75" />





# Conclusion

**Final Thoughts**

**Code** - All python code for this project can be found in my GitHub respository: [GitHub](https://github.com/skhan-tech/BusinessClassifier)

Intro to Data Science
==================

Brought to you by [Lesley Cordero](http://www.columbia.edu/~lc2958) and [ADI](https://adicu.com)

## Table of Contents

- [0.0 Setup](#00-setup)
    + [0.1 Python & Pip](#01-python-pip)
    + [0.2 R & R Studio](#02-r-r-studio)
    + [0.3 Other](#03-other)
- [1.0 Background](#10-background)
    + [1.1 What is Data Science?](#11-what-is-data-science)
        * [1.1.1 What do you mean by data?](#111-what-do-you-mean-by-data)
    + [1.2 Is data science the same as machine learning?](#12-is-data-science-the-same-as-machine-learning)
    + [1.3 Why is Data Science important?](#13-why-is-data-science-important)
- [2.0 Data Science Process](#20-data-science-process)
    + [2.1 What is a "Data Science" Problem?](#21-what-is-a-data-science-problem)
    + [2.2 ...So where do I begin?](#22-so-where-do-i-begin)
    + [2.3 Given Problem](#23-given-problem)
        * [2.3.1 Open Data](#231-open-data)
    + [2.4 Given Data](#24-given-data)    
- [3.0 Python vs R](#30-python-vs-r)
    + [3.1 Python](#31-python)
    + [3.2 R Programming](#32-r-programming)
    + [3.3 Conclusion](33-conclusion)
- [4.0 Tackling a Data Problem](#40-tackling-a-data-problem)
    + [4.1 Data Preparation](#41-data-preparation)
    + [4.2 Data Cleaning](#42-data-cleaning)
    + [4.3 Data Fun](#43-data-fun)
- [5.0 Resources](#50-resources)


## 0.0 Setup

This guide was written in Python 2.7 and R 3.2.3.

### 0.1 Python & Pip

Download [Python](https://www.python.org/downloads/) and [Pip](https://pip.pypa.io/en/stable/installing/).

### 0.2 R & R Studio

Install [R](https://www.r-project.org/) and [R Studio](https://www.rstudio.com/products/rstudio/download/).

### 0.3 Other

```
package.install("pdftools")
```

```
pip install nltk
```

## 1.0 Background


### 1.1 What is Data Science?

Data Science is the application of statistical and mathematical methods to problems involving, usually large, sets of data.

#### 1.1.1 What do you mean by data? 

Data is essentially anything that can be recorded/transcribed - numerical, text, images, sounds, anything! 

### 1.2  Is data science the same as machine learning?

Well, no. They merely have overlap. Whereas the topic of machine learning involves lots of theoretical components we won't worry about, data science takes these methods and applies them to the real world. 

### 1.3 Why is Data Science important? 

Data Science has so much potential! By using data in creative and innovative ways, we can gain a lot of insight on the world, whether that be in economics, biology, sociology, math - any topic you can think of, data science has its role. 

## 2.0 Data Science Process

It might seem like data scientists concentrate on the statistical concepts to tackle a data science problem. But the truth is that data Science is much more than the tools we use. It is the combined thought processes we engage with to come up with the best and most efficient solution to a data science problem.

You might have heard of the 80|20 rule in Economics? Data Science has its own version of the 80|20 rule, in that only 20% of your time as a data scientist is spent actually working on gaining insights from your data, whereas about 80% of it is spent managing, preparing, and cleaning the data.

### 2.1 What is a "Data Science" problem?

If your problem involves the use of data in some capacity, then it's probably a data science problem! What type of data that is doesn't matter - all that matters is that you're using it, along with mathematical tools, to gain insight into whatever problem you happen to be focusing on. 

### 2.2 ...So where do I begin?

A big part of data science is figuring out what to work on. There are two ways of going about finding an interesting problem, in my experience. 

### 2.3 Given Problem

The first is you're given a problem (or you think of one yourself), and you have to find that data before beginning the process of finding insight. How hard or easy this problem is dependent on the data available to you. If you're working at a company, do they have this data for you to use already? If you're working on a side project, is the accumulated data available for public use? 

These are all questions you should be asking yourself when first starting a data science project: <b> Where will my data come from?</b>

One glorious thing about Data Science is<b> O P E N  D A T A </b>

#### 2.3.1 Open Data

What's open data, you ask? Simple, it's data that's freely  for anyone to use! Some examples include things you might have already heard of, like APIs, online zip files (yum), or by scraping data!

You might be wondering where this data comes from - well, it can come from a variety of sources, but some common ones include large tech companies like Facebook, Google, Instagram. Others include large institutions, like the US government! Otherwise, you can find tons of data from all sorts of organizations and individuals. 

###2.4 Given Data

The second, is you're given data and you have to work with it until you find something interesting. If you figure out there's nothing interesting, move on a find a new project. It happens to the best of us.

## 3.0 Python vs R

Python and R are two commonly used programming languages in the realm of data science. Some data scientists prefer R, others prefer R; regardless, both are useful programming languages to feel comfortable with if you're interested in Data Science. With that said, in this tutorial we'll highlight some differences and work with both of them through a small data science project.

### 3.1 Python

If your data analysis needs integration with a web application or database, Python is probably your best bet. Compared to R, the support for these sorts of application is much better since it's more of a general-purpose language.


### 3.2 R Programming

Meanwhile, if your data analysis demands standalone computing or exploratory work, R is a great choice because of its strong statistical support.

### 3.3 Conclusion

Depending on who you ask is the answer you'll get, but having a workflow that employs the strengths of both Python and R is the optimal strategy. As I've alluded to before, R is great for preliminary analysis, whereas Python is great for final use cases - final products.

## 4.0 Tackling a Data Problem

So let's start our first data science problem! Here you'll find Jae's [course evaluations](http://www.cs.columbia.edu/~jae/3157/files/eval.pdf)


### 4.1 Data Preparation

So we begin by scraping the text off the pdf in R. R has a great package for scraping data from pdfs. 

``` R
library(pdftool)
download.file("http://www.cs.columbia.edu/~jae/3157/files/eval.pdf5.pdf, "eval.pdf", mode = "wb")

eval <- pdf_text("eval.pdf")

```
Just to see that it works, let's try a couple of examples.

```
# first page text
cat(eval[1])
```
Here's page 1!

```
# second page text
cat(eval[2])
```

There's page 2! 

Pretty neat, huh? Next, let's write all this data to textfiles.

``` R
sink("evals.txt")
sink(eval)
```

For sake of working both with R and Python, let's start coding in python. First, let's retreive the data from the file and reconstruct our dictionary data type.

``` python
pair = {'name': name,'location': location}
with open('./evals.txt', 'a') as f:
     f.writelines('{}:{}'.format(k,v) for k, v in pair.items())
     f.write('\n')
```

### 4.2 Data Cleaning

Now let's start cleaning the data. 

``` python
for i in range(len(eval)-1):
    dict[i].split('\n')
```

``` python
n = 0
for i in range(len(eval)-1):
    if n < 7:
    eval.pop(eval[i])
```

### 4.3 Data Fun

Finally, we get to the best part: finding insights on the data. 
```python
from nltk.book import *
import string, re

fdist1 = FreqDist(text1)
```

```
tokens = text.split() # split on whitespace
keyword = re.compile(target, re.IGNORECASE)

for index in range( len(tokens) ):
    if keyword.match( tokens[index] ):
        start = max(0, index-window)
        finish = min(len(tokens), index+window+1)
        lhs = string.join( tokens[start:index] )
        rhs = string.join( tokens[index+1:finish] )
        print "%s [%s] %s" % (lhs, tokens[index], rhs)
```

Finally we walk through the array of words, looking for our matches. If keyword matches the array element at the current index, we want to print out the matching word, surrounded by its context. We compute start and finish indices of the context explicitly to ensure we don’t ask for a negative index or one past the end of our array. Finally, we construct the left and right hand sides of the concordance, and print out the result using a simple template.

There are no doubt hundred of ways to improve and extend this script, but it does what it is meant to. So, on to more interesting tasks.


## 5.0 Resources

[Johns Hopkins Data Science Coursera](https://www.coursera.org/specializations/jhu-data-science) <br>
[List of Public Datasets](https://github.com/caesar0301/awesome-public-datasets)<br>

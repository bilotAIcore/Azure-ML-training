---
Date: "2019-08-27"
Step: 'Data analysis'
Description: Data inspection & manipulation exercise, using the diabetes data.
---

## 1. Import Data
__Source__: Azure Blob

__SAS__: ask for this

__File has header__: TRUE

__Use cached results__: TRUE

## 2. Convert to CSV
<p>After adding this operator, connecting it to the **Import Data** operator, and running the experiment, open the converted data in a new __R__ Notebook.</p>

<p>This opens a new Azure (Jupyter) Notebook, using R-language. 
After running the first two cells, in the next empty cell, 
type:
```r
summary(dat) 
```

<p>
and press <code>shift+enter</code>. This will print out the basic 
statistical summary of each variable. In the next cell, type two 
commands:</p>
```r
prop_zero = colSums(dat==0)/nrow(dat)
round(prop_zero,2)
```
<p>The first line calculates the proportion of zeros in each column,
while the second simply rounds the result to precision of two signigicant numbers. </p>

<p>From the result it is clear that there are many missing values in the data; zero-values do not make any sense, except for <code>Pregnancies</code> and <code>Outcome</code>. Try to see how the number of remaining rows changes when you drop all missing values. Does it make sence?</p>

## 3. Execute R Script
<p>To fix the data, such that zeros are coded to missing values,
the best way is to execute a script, either using **R** or **Python**. This example uses **R**. Posting the following code *R cript* section of the operator and runnig the experiment will produce the desired outcome:
</p>

```r
# Get data from input port:
dataset1 <- maml.mapInputPort(1) # class: data.frame

# select columns to be modified:
cols = setdiff(names(dataset1),c('Pregnancies', 'Outcome'))
for( i in cols){
    # select rows to be affected:
    rows = dataset1[,i] == 0
    # make replacement: 
    dataset1[rows,i] = NA
}

# Send data to the output Dataset port:
maml.mapOutputPort("dataset1");
```
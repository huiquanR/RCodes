# 0. Basics

## 0.1 Calculation

```R
2 + 2
8 - 1
3 * 3
3 / 3
3 ^ 3
log(2.718)
log10(1000)
scale(50, center = 25, scale = 5)
mean(c(1,2,3,4))
sd(c(1,2,3,4))
```

## 0.2 Write Notes

```R
# If you begin a line with POUND "#", 
# it means you are writing a note.
# R won't execute the notes.
# Notes are helpful to explain your codes to others,
# or simply to yourself - when you 
# revisit them a year(a month/a week/a day) later.
# Well, that depends on ...
```

Some people write notes before a line of codes, some do it after a line of codes.

```R
# load library #
library(ggplot2)

# or

library(ggplot2) # loading ggplot2 for plotting
```

### 0.2.1 Code Blocks and Titles

If you are using RStudio as your IDE for R programming, then you may find this function in RStudio very helpful: Code Blocks.

To divide code blocks, simply seperate them with a line of these (in between you can name the code blocks):

```R
 # Section One --------------------------------- 
 # Section Two ================================= 
 ### Section Three ############################# 
```
To be honest, though RStudio claimed these to be different, I personally don't find these sections differ at all. They are not nested... Hmm... Maybe they should be.


## 0.3 Objects in R environment

In R, we are working with objects in R environment. 
The objects include dataframes, vectors, lists, functions, ...

- To know who they are, run:
```R 
ls()
# > ls()
# [1] "mydata"
```

- To remove this object, run:
```R 
rm(mydata)
```

- To remove objects other than ideal ones, 
- Run (often used when you want to clean the working environment):
```R 
rm(list = setdiff(ls(), c("TheBelovedDataSet1", "TheBelovedDataSet2")))
```

### 0.3.1 Generate an object - Vector

```R 
# create a numeric vector #
a = c(1, 1, 2, 3, 4)

# to know the class/type of vector#
class(a)
typeof(a)
mode(a)

# to calculate the mean of all the numbers in a #
# > mean(a)
# [1] 2.2
# > stats::median(a)
# [1] 2
# > pracma::Mode(a) # Please note - pracma::Mode is different from base::mode
# [1] 1

# create a string vector #
b = c("Japan", "India", "India", "Korea")
# pracma::Mode cannot deal with strings.#
# create another function to find mode values of a string vector.
fun_Mode = function(x) {names(sort(-table(x)))[1]}
fun_Mode(b)
# > fun_Mode(b)
# [1] "India"
```

### 0.3.2 List

```R
# try these and see the outcomes.
a = list(1,2) 
a = list(rm, 2) # please note in this case, rm is a FUNCTION
a = list("rm", 2) # please note in this case, "rm" is a string element
```

### 0.3.3 Matrix

```R 
# use matrix function to create function.
a = matrix(1:9, nrow = 3, ncol = 3)
a = matrix(1:9, nrow = 3)
a = matrix(1:9, nrow=3, byrow=TRUE)    # fill matrix row-wise; default is by-column.

# cbind - column-wise; rbind - row-wise.
a = cbind(c("Jack", "John", "Joe"), c("Sally", "Sue", "Sam"))
# > a
#     [,1]   [,2]   
#[1,] "Jack" "Sally"
#[2,] "John" "Sue"  
#[3,] "Joe"  "Sam"  
a = rbind(c("Jack", "John", "Joe"), c("Sally", "Sue", "Sam"))
# > a
#     [,1]    [,2]   [,3] 
#[1,] "Jack"  "John" "Joe"
#[2,] "Sally" "Sue"  "Sam"

t(a) # transpose a matrix
#     [,1]   [,2]   
#[1,] "Jack" "Sally"
#[2,] "John" "Sue"  
#[3,] "Joe"  "Sam" 
```

### 0.3.4 Data Frames
```R 
a = data.frame(a)
```

### 0.3.5 User-Defined Functions 

```R 
FUNMAX = function(x) {
    max(x)
}
b = c(1,2,3,4)
FUNMAX(b)

# b = c(1,2,3,4)
# > FUNMAX(b)
# [1] 4
```

### 0.3.6 Other Common Objects in Your Environment 

```R 
a = lm(DV ~ male, data = mydata) # fitting a linear model
class(a) # the object would be an "lm" object.
# [1] "lm"
```

```R 


```

## 0.4 Indexing/Locating Elements in Data/Matrix - Cells/Rows/Columns

- Basic Indexing

```R 
a 
#     [,1]   [,2]   
#[1,] "Jack" "Sally"
#[2,] "John" "Sue"  
#[3,] "Joe"  "Sam" 

# indexing
a[1,] # 1st row
a[,1] # 1st column
a[1]  # 1st element
a[5]  # 5th element (counting from 1st, then down by column, so the 5th would be "Sue")
a[c(2:3,),]
```

### 0.4.1 "$" Dollar mark - A$a$aa
```R 

```
### 0.4.2 mydata[1,]
```R 


```
### 0.4.3 mydata[,2]
```R 

```

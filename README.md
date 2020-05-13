- Version: MAY/13/2020

- Welcome to the page, which contains some commonly used codes for social science research.
I am only an entry-level user of R, so this might be too simple for you, or contain some mistakes.
Feel free to advise me if you have a better idea somewhere. Thanks.

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

## 0.2 Objects in R environment

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

## 0.2.1 Generate an object - Vector

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

## 0.3 List

```R 

```

## 0.4 Matrix

```R 

```

## 0.5 Data Frames
```R 

```

## 0.6



# 1. Prepare the Working Environment
In this section, I listed some functions to begin an analysis.

## 1.1 Check and change the system status

```R 
# Report Sys and Envir information #
Sys.info()    # will display OS version, etc.
sessionInfo() # will display R version, Locale, Loaded Packages

# getPackageInfo returns information on attached packages 
# including name, version and source.
envDocument::getPackageInfo() 
#	                Name                                        Value
#	1        envDocument                   2.4.1 CRAN CRAN 2019-08-08

# set system locale to Simplified Chinese #
Sys.setlocale(, "CHS")
```

## 1.2 Install R Packages from CRAN/GitHub/Old Packages

```R 
# Regular Installation from CRAN
install.packages(c("rgeos", "scales", "tidyselect", "vctrs"))

# Install from a GitHub source
devtools::install_github('bbc/bbplot')

# Install an old version (maybe they work better, maybe they no longer exist on CRAN, ...)
install_version("fiftystater", version = "1.0.1", repos = "http://cran.us.r-project.org")
install_version("zipcode", version = "1.0", repos = "http://cran.us.r-project.org")
```

## 1.3 Load the packages

```R 
# In R, loading packages can be easy. #
library(easypackages) # this is loading one package.

# This is naming a list of packages (let's call it paclist) you want to load;
paclist = c("sjmisc", "sjPlot",
            "ggplot2", "graphics", 
            "grid", "gridExtra")

# Next, we will use one line to load them all.
easypackages::libraries(paclist) # this means using *libraries* FUNCTION in *easypackages* PACKAGE
```

# 2. Read/Write Data

## 2.1 Read/Write CSV files

```R 
# read.table function; header = T - meaning first row contains variable names.
mydata = read.table("X:/a.csv", header = TRUE, sep = ",")

# default header = T.
mydata = read.csv("X:/address.csv")

# if the first row begins with data - then header = F.
mydata = read.csv("X:/address.csv", header = F)

# if you need to specify encoding
mydata = read.csv("X:/data_SH.csv", header = TRUE, sep = ",", encoding = "ASCII")

# Write/Output CSV
write_csv(mydata, "X:/data_SH.csv")
```



## 2.2 Read/Write Excel files

```R 
# load packages
library(xlsx)
# encoding needs to be specified if Chinese/Japanese strings are not displayed properly.
mydata = xlsx::read.xlsx("X:/2019.xlsx", sheetName="Sheet 1", encoding = "UTF-8") 

# a quicker version:
library(readxl)
mydata = readxl::read_xlsx("X:/2020.xlsx")

# Write/Output Excel
writexl::write_xlsx(mydata, "X:/2020.xlsx")
```

## 2.3 Read/Write Stata files

```R 
# read.dta {foreign} - version 5-12
mydata = readstata13::read.dta13("X:/2018.dta")

# read.dta13 - for Stata 13 and newer
mydata = readstata13::read.dta13(file = "X:/2018.dta", encoding = "cp936")

# Write/Output Stata Data File and specify version
haven::write_dta(mydata, version = 13, "X:/2018.dta")

```
## 2.4 Read SAS files
## 2.5 Read SPSS files

# 3. Know Your Data
## 3.1 A quick overview
## 3.2 Variable names
## 3.3 Variable classes
## 3.4 Describe Categorical Variables
## 3.5 Describe Numeric Variables

# 4. Clean your data
## 4.1 Knowing what you are doing
## 4.2 Rename
## 4.3 Generate New Var
## 4.4 Creating a dummy - ifelse FUNCTION
## 4.5 Recode a multi-level factor - within FUNCTION
## 4.6 Relevel the Factor
## 4.7 Numeric Transformation - log, standardize, scale

# 5. Descriptive Stats
## 5.1 Frequency Tables
## 5.2 Mean, Median, Mode, SD
## 5.3 Min, Max, Quintiles

# 6. Descriptive Plots
## 6.1 Bar
## 6.2 Pie
## 6.3 Line
## 6.4 Box
## 6.5 Histogram

# 7. Missings
## 7.1

# 8. Data Analysis
##

# 9. Model Visualization and Outputs
##

# 10. Robustness
##

# 11. GIS and Maps
##

# 12. Social Network Analysis
##

# 13. Agent Based Modelling
##

# 14. NLP
##

# 15. WebScraping
##

# 16. RShiny
##


- Thanks.

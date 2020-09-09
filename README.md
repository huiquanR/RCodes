# Version: Sep/09/2020

- Welcome. This page contains some commonly used codes for social science research. I am only an entry-level user of R, so this might be too simple for you, and it might contain some rookie mistakes. So please feel free to advise me if you have a better idea somewhere. 
- Sincerely, thanks!

[https://github.com/huiquanR/RCodes/blob/master/Markdown/00_Basics.md] (00_Basics)

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

```R
wvsdf$kids = NA
wvsdf = within(wvsdf, {
  kids [X011_1 == "No child"] = 0
  kids [X011_1 == "1 child"] = 1
  kids [X011_1 == "2 children"] = 2
  kids [X011_1 == "3 children"] = 3
  kids [X011_1 == "4 children"] = 4
  kids [X011_1 == "5 children"] = 5
  kids [X011_1 == "6 children"] = 6
  kids [X011_1 == "7 children"] = 7
  kids [X011_1 == "8 or more children"] = 8
})
dist_tab(wvsdf$kids)
```

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

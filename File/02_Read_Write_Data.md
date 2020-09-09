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

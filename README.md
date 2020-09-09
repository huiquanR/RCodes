# Version: Sep/09/2020

- Welcome. This page contains some commonly used codes for social science research. I am only an entry-level user of R, so this might be too simple for you, and it might contain some rookie mistakes. So please feel free to advise me if you have a better idea somewhere. 
- Sincerely, thanks!

[https://github.com/huiquanR/RCodes/blob/master/Markdown/00_Basics.md] (00_Basics)

[https://github.com/huiquanR/RCodes/blob/master/Markdown/01_Environment.md] (01_The R Working Environment)

[https://github.com/huiquanR/RCodes/blob/master/Markdown/01_Environment.md] (02_Read or Write Data in R)

[https://github.com/huiquanR/RCodes/blob/master/Markdown/01_Environment.md] (01_The R Working Environment)

[https://github.com/huiquanR/RCodes/blob/master/Markdown/01_Environment.md] (01_The R Working Environment)

[https://github.com/huiquanR/RCodes/blob/master/Markdown/01_Environment.md] (01_The R Working Environment)

[https://github.com/huiquanR/RCodes/blob/master/Markdown/01_Environment.md] (01_The R Working Environment)

[https://github.com/huiquanR/RCodes/blob/master/Markdown/01_Environment.md] (01_The R Working Environment)

[https://github.com/huiquanR/RCodes/blob/master/Markdown/01_Environment.md] (01_The R Working Environment)

[https://github.com/huiquanR/RCodes/blob/master/Markdown/01_Environment.md] (01_The R Working Environment)


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

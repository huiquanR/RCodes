
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


# 4. Clean your data

## 4.1 Knowing what you are doing

Before stepping in to data analysis, you want to make sure the data are **clean**. The step to ensure this, is called data cleaning or data cleansing. According to [Wiki](https://en.wikipedia.org/wiki/Data_cleansing), there are five criteria of a high-quality dataset:

- validity
- accuracy
- completeness
- consistency
- uniformity

In actual process of social science research, there are different stages and steps to ensure the criteria named above. For example, data collection is a big part if you want to ensure your questionnaires are asking the right questions (validity), your interviewers are effective (high response rate, high completeness, high consistency), the answers are specific enough for respondents to give clear answers (accuracy), and so on. These steps are important, but many researchers today are using data that have already been collected. In this context, data cleaning means something more specific: to check the problems already in your data, and take care of them.

Here I list a few tasks that I commonly do in data cleaning:

- Give proper names for variables.
  - This helps you to keep track your variables and make your codes friendly for other collaborators.
- Generate new variables based on existing ones, or from scratch.
  - Always generate new varibles. I recommend this even if your old variables are ready-to-go.
- Check and change class/attributes of variable.
- Check problems, such as typos (string), extreme values (numeric), and missings, and take care of them.

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

# 17 Miscellaneous 其他

## 环境查看和设置 ##

```R 
# 
sessionInfo()
Sys.setlocale('LC_ALL', locale = "English_United States.1252")

# system code page: 936
# Sys.setlocale('LC_ALL', locale = "chinese")
# Sys.setlocale(locale = "CHT")
# Sys.setlocale(locale = "English")
# Sys.setlocale("LC_TIME", "English")
# Sys.getlocale()

memory.size(max=TRUE)
memory.limit(100000)
```

## 检查缺失值 ##

```R 
ValidResponse = function(i) {
  a1 = length(i[!is.na(i)])
  a2 = length(i)
  a3 = a1/a2
  return(a3) }

# 对a变量，依据b（例如wave、year）进行分组检查有效回复率
Check_Wave = function(a, b) {
  k1 = by(a, b, ValidResponse)
  k2 = list(k1)
  k3 = data.frame(do.call("rbind", k2))
  k4 = gsub(deparse(substitute(a)), pattern = "$", replacement = "_", fixed = T)
  rownames(k3) = k4
  
  k5 = as.data.frame(table(b))
  k6 = as.character(unlist(k5[1]))
  k7 = gsub(deparse(substitute(b)), pattern = "$", replacement = "_", fixed = T)
  k8 = paste(k7, k6, sep = "_")
  colnames(k3) = k8
  return(k3)
}

# 对每个录入变量，将wave作为分组依据，检查有效回复率（对上述函数输入了固定的参数b）
All_Wave_Check = function(i) {
  k1 = Check_Wave(i, wvsdf$wave)
  return(k1)
}
```

## 对Stata等来源的已贴标签数据进行转化：将文字标签转为字符串型取值##

```R 
Clean_Label = function(i) {
  trimws(labelled::to_character(i))
}
```

## 最新的150个变量（对tail输入参数即可）##

```R 
NewestVar = function(i) {tail(names(i), 150)}
```

## 对取值经由字符型转化，可减少报错和强制输出NA等问题 ##

```R 
toFAC = function(i) {as.factor(as.character(i))}
toNUM = function(i) {as.numeric(as.character(i))}
```

## 提取众数 ##

```R 
Find_Mode = function(x) {
  ux = unique(as.character(x))
  ux[which.max(tabulate(match(x, ux)))]
}
```

## 碎片化指数计算函数 ##

```R 
# Fractionalization Index: function #
Frac_Index = function(x) {
  a1 = qdap::dist_tab(x)
  a2 = a1$dataframe$percent
  a3 = a2/100
  a4 = sum(a3^2)
  a5 = 1 - a4
  return(a5)
}

names(wvsdf9)
wvsdf9 = ddply(wvsdf9, 
  .(country),
  mutate,
  Rel_Frac = Frac_Index(religion))

```

## 作图主题自定义样例 ##

```R 
library(ggplot2)
theme_USER = theme_grey()+
  theme(plot.title = element_text(lineheight=2, hjust=.5, vjust=1.5),
        title=element_text(size=rel(1.5), family="Century"), # controlling the title, xylabs
        axis.text.x = element_text(size=rel(1.5), family="Century"),
        axis.text.y = element_text(size=rel(1.5), family="Century"),
        legend.text=element_text(size=rel(1.3), family="Century"),
        #legend.position="top",
        legend.direction="vertical",
        legend.key = element_rect(size = 1.3, color = 'white'),
        #legend.background = element_rect(fill="light yellow", size=.5, linetype="dotted"),
        legend.position=c(0.19,0.88), # first number;second number: 1 ->0 down
        legend.key.size = unit(0.6, "cm"))
 ```
 
 
## 分组计算Mean/SD ##

```R 
 #
data_summary <- function(data, varname, groupnames){
  require(plyr)
  summary_func <- function(x, col){
    c(mean = mean(x[[col]], na.rm=TRUE),
      sd = sd(x[[col]], na.rm=TRUE))
  }
  data_sum<-ddply(data, groupnames, .fun=summary_func,
                  varname)
  data_sum <- rename(data_sum, c("mean" = varname))
  return(data_sum)
}
#

df2 <- data_summary(event, varname="prcp", 
                    groupnames=c("city"))
```

## 柱状图 ##

```R 
# stat=bin
ggplot(event,aes(x = factor(1), fill = city)) + 
  geom_bar(width = 1) + 
  coord_polar(theta="y")+
  scale_fill_manual(values = c("steelblue", "light yellow"),
                                          name="社运发生地",
                                          labels=c("纽约市", "华盛顿特区"))
```


## 清理中文字符中常见空格和全角标点等问题 ##

```R 
# a user-defined function cleaning spaces/brackets
qingli = function(d)
{d = gsub("[:space:]", "[:blank:]", d, fixed = TRUE)
d = gsub(" ", "", d, fixed = TRUE) 
d = gsub("　", "", d, fixed = TRUE)
d = gsub(",", "", d, fixed = TRUE)
d = gsub("（", "(", d, fixed = TRUE)
d = gsub("）", ")", d, fixed = TRUE)}
TOTAL$NAME1 = qingli(TOTAL$NAME)
TOTAL$NAME1 = genX(TOTAL$NAME1, "(", ")")
```

## 对文字型取众数，对数值型取均值 ##

```R 
MEAN1  = function(d) {mean(d, na.rm = T)}
VALUE1 = function(d) {if (is.numeric(d)) {MEAN1(d)}
  else {pracma::Mode(d)}}
STAT = function(x) {ifelse(is.numeric(x), Mean(x), Mode(x))}

varlist = setdiff(names(wvsdf_impute), "country")
names(wvsdf_impute)
data = wvsdf_impute %>%  group_by(country) %>% summarise_at(vars(varlist), funs(VALUE1))
```










## 

##


```R 
############################################
############################################

#### Customized Functions ####


############################################
############################################

# 以下函数是对allEffects的objects进行模型效应提取和规范命名。
allEff_toDF = function(i) {
  # function to get "AllEffects"
  Extract_allEffectsObj = function(i) {
    # count the order #
    # determine whether using 1st/2nd order term #
    ORDER_NUM = function(i) {
      a1 = sapply(i, names)
      a2 = colnames(a1)
      a3 = stringr::str_count(a2, pattern = ":") # 此处是检测有没有交互项。
      return(a3+1)
    } # 如是二项相乘，则此处返回2；如没有交互项，此处返回1.
    
    # first-order (no interaction) #
    EFF1 = function(i) {
      a1 = as.data.frame(i)
      a2 = as.data.frame(a1[1])
      a3 = a2[,1:3] # 前三列即可。
      names(a3) = c("TERM", "fit", "se")
      return(a3)
    }
    
    # second-order (interaction) & Collapse #
    
    EFF2 = function(i) {
      a1 = as.data.frame(i)
      a2 = as.data.frame(a1[1])
      a3 = a2[,3:4] # 此处较为ad hoc仍需generalize
      a4 = a2[,1:2]
      
      COLLA = function(d) {paste0(d, collapse = "_")} # 将交互项（如有）则粘贴为一个字串 
      a5 = apply(a4, 1, COLLA)
      a6 = cbind(a5, a3)
      
      names(a6) = c("TERM", "fit", "se") # 项、预测值、标准误
      return(a6)
    }
    
    if (ORDER_NUM(i)>=2) {
      return(EFF2(i))
    } else {
      return(EFF1(i))
    } # 交互则EFF2；否则EFF1即可。
    
  } # maybe we could generalize this to higher-order interaction
  
  a = Extract_allEffectsObj(i)
  g = a[FALSE,]
  n = 1
  for (n in 1:length(i)) {
    g2 = Extract_allEffectsObj(i[n])
    g = rbind(g, g2)  
    n = n + 1
  }
  return(g)
} # 以上函数是对allEffects的objects进行模型效应提取和规范命名。


############################################
############################################

# 提取term的文字标签。针对的是ZIP模型的零膨胀模型部分。
# 用到的函数包括
# attr() 属性标签
# str() 查看对象结构
# attributes()$term.labels # 提取标签
# $terms 

get_MODEL_Labels = function(i) {attributes(i$terms$zero)$term.labels}

############################################
############################################

ZIP_fit = function(zipmodel) {
  termlist = get_MODEL_Labels(zipmodel)
  effect_each = function(i) {
    a1 = ggeffects::ggemmeans(model = zipmodel, 
                              terms = i)
    a1 = subset(a1, select = c(x, predicted))
    a1$x = as.character(a1$x) # this has to be done to avoid rbind errors (factor type)
    a1 = as.data.frame(a1) # this has to be done to avoid rbind errors (data attributes)
    return(a1)
  }
  a2 = do.call(rbind, lapply(termlist, effect_each))
  return(a2)
}


############################################
############################################


Get_NB_Terms = function(i) {
  a1 = allEff_toDF(allEffects(i))
  a2 = as.character(a1$TERM)
  return(a2)
}
 

Paired_IndexZeroinfl = function(c, d, a, b) {
  # c & d: glm models (pre, post)
  # a & b: zeroinfl models (pre, post)
  # get predicted values from Zero-infl models #
  termlist = Get_NB_Terms(c)
  n1 = ZIP_fit(a)
  n2 = ZIP_fit(b)
  PRE = n1$predicted
  POST= n2$predicted
  fit = log(POST/PRE)
  ratio = exp(fit)
  
  # get matrix from glm.nb models #
  e1 = allEffects(c)
  e2 = allEffects(d)
  getMat = function(i) {
    d = i$model.matrix
    return(d)
  }
  mat1 = do.call(rbind, lapply(e1, getMat))
  mat2 = do.call(rbind, lapply(e2, getMat))
  
  # get vcov #
  a1 = vcov(a)
  a2 = vcov(b)
  cov1 = a1[1:(0.5*sqrt(length(a1))),1:(0.5*sqrt(length(a1)))]
  cov2 = a2[1:(0.5*sqrt(length(a2))),1:(0.5*sqrt(length(a2)))]
  
  # 4. Calculate s.e from model matrix and vcov 
  v.d = mat1%*%cov1%*%t(mat1)+mat2%*%cov2%*%t(mat2)
  se = sqrt(diag(v.d))
  upper = exp(fit + 1.96*se)
  lower = exp(fit - 1.96*se)
  model = deparse(substitute(a))
  ci.d = data.frame(cbind(model, termlist, PRE, POST, ratio, se, lower, upper))
  return(ci.d)
}
```

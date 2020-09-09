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

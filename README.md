Welcome to the page, which contains some commonly used codes for social science research.
I am only an entry-level user of R, so this might be too simple for you, or contain some mistakes.
Feel free to advise me if you have a better idea somewhere :+1:

# 1. Prepare the Working Environment
In this section, I listed some functions to begin an analysis.

## 1.1 Check and change the system status

```R 
# Report Sys and Envir information #
Sys.info()    # will display OS version, etc.
sessionInfo() # will display R version, Locale, Loaded Packages
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
paclist = c("questionr", "devtools", "cplm", "lubridate", 
            "rgeos", "dplyr", "car", "Matrix", "utils", "mice", 
            "sp", "timeDate", "data.table", "effects", "ggeffects",
            "sjlabelled", "sjmisc", "sjPlot",
            "ggplot2", "graphics", "grid", "gridExtra",
            "haven", "pacman", "qdap", "readstata13", "stats",
            "stringr", "ggthemes", "bbplot", "ggmap", "gganimate", 
            "maptools", "tidyverse", "MASS", "rsatscan", "desc", 
            "readxl", "pscl", "xlsx", "texreg", "RCurl", "rvest", 
            "scales", "fiftystater", "Cairo", "scatterpie", "zipcode")

# Next, we will use one line to load them all.
easypackages::libraries(paclist) # this means using *libraries* FUNCTION in *easypackages* PACKAGE
```

# 2. Read in the data files

## 2.1 Read CSV files

```R 
# Report Sys and Envir information #
Sys.info()    # will display OS version, etc.
sessionInfo() # will display R version, Locale, Loaded Packages
```
## 2.2 Read Excel files

```R 
# Report Sys and Envir information #
Sys.info()    # will display OS version, etc.
sessionInfo() # will display R version, Locale, Loaded Packages
```
## 2.3 Read Stata files

```R 
# Report Sys and Envir information #
Sys.info()    # will display OS version, etc.
sessionInfo() # will display R version, Locale, Loaded Packages
```
## 2.4 Read SAS files

```R 
# Report Sys and Envir information #
Sys.info()    # will display OS version, etc.
sessionInfo() # will display R version, Locale, Loaded Packages
```
## 2.5 Read SPSS files

```R 
# Report Sys and Envir information #
Sys.info()    # will display OS version, etc.
sessionInfo() # will display R version, Locale, Loaded Packages
```

# 3. Know your data
# 4. Clean your data
# 5. Descriptive Stats
# 6. Descriptive Plots
# 7. Missings
# 8. Data Analysis
# 9. Model Visualization and Outputs
# 10. Robustness
# 11. GIS and Maps
# 12. Social Network Analysis
# 13. Agent Based Modelling
# 14. NLP
# 15. WebScraping
# 16. RShiny


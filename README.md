## Welcome to the page, which contains some commonly used codes for social science research.


# 1. Prepare the working environment
## 1.1 Check and change the system status

```R 
# Report Sys and Envir information #
Sys.info()    # will display OS version, etc.
sessionInfo() # will display R version, Locale, Loaded Packages
```

## 1.2 Load the packages

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


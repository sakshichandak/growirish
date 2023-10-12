Grow Irish Project
================

## GitHub Documents

This is an R Markdown format used for publishing markdown documents to
GitHub. When you click the **Knit** button all R code chunks are run and
a markdown file (.md) suitable for publishing to GitHub is generated.

## Including Code

You can include R code in the document as follows:

``` r
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
library(DBI)
library(dbplyr)
```

    ## 
    ## Attaching package: 'dbplyr'

    ## The following objects are masked from 'package:dplyr':
    ## 
    ##     ident, sql

``` r
library(odbc)

odbcListDrivers()
```

    ##                                                      name        attribute
    ## 1                                              SQL Server         APILevel
    ## 2                                              SQL Server ConnectFunctions
    ## 3                                              SQL Server        CPTimeout
    ## 4                                              SQL Server    DriverODBCVer
    ## 5                                              SQL Server        FileUsage
    ## 6                                              SQL Server         SQLLevel
    ## 7                                              SQL Server       UsageCount
    ## 8                Microsoft Access Driver (*.mdb, *.accdb)       UsageCount
    ## 9                Microsoft Access Driver (*.mdb, *.accdb)         APILevel
    ## 10               Microsoft Access Driver (*.mdb, *.accdb) ConnectFunctions
    ## 11               Microsoft Access Driver (*.mdb, *.accdb)    DriverODBCVer
    ## 12               Microsoft Access Driver (*.mdb, *.accdb)        FileUsage
    ## 13               Microsoft Access Driver (*.mdb, *.accdb)        FileExtns
    ## 14               Microsoft Access Driver (*.mdb, *.accdb)         SQLLevel
    ## 15 Microsoft Excel Driver (*.xls, *.xlsx, *.xlsm, *.xlsb)       UsageCount
    ## 16 Microsoft Excel Driver (*.xls, *.xlsx, *.xlsm, *.xlsb)         APILevel
    ## 17 Microsoft Excel Driver (*.xls, *.xlsx, *.xlsm, *.xlsb) ConnectFunctions
    ## 18 Microsoft Excel Driver (*.xls, *.xlsx, *.xlsm, *.xlsb)    DriverODBCVer
    ## 19 Microsoft Excel Driver (*.xls, *.xlsx, *.xlsm, *.xlsb)        FileUsage
    ## 20 Microsoft Excel Driver (*.xls, *.xlsx, *.xlsm, *.xlsb)        FileExtns
    ## 21 Microsoft Excel Driver (*.xls, *.xlsx, *.xlsm, *.xlsb)         SQLLevel
    ## 22            Microsoft Access Text Driver (*.txt, *.csv)       UsageCount
    ## 23            Microsoft Access Text Driver (*.txt, *.csv)         APILevel
    ## 24            Microsoft Access Text Driver (*.txt, *.csv) ConnectFunctions
    ## 25            Microsoft Access Text Driver (*.txt, *.csv)    DriverODBCVer
    ## 26            Microsoft Access Text Driver (*.txt, *.csv)        FileUsage
    ## 27            Microsoft Access Text Driver (*.txt, *.csv)        FileExtns
    ## 28            Microsoft Access Text Driver (*.txt, *.csv)         SQLLevel
    ##                   value
    ## 1                     2
    ## 2                   YYY
    ## 3                    60
    ## 4                 03.50
    ## 5                     0
    ## 6                     1
    ## 7                     1
    ## 8                     3
    ## 9                     1
    ## 10                  YYN
    ## 11                02.50
    ## 12                    2
    ## 13        *.mdb,*.accdb
    ## 14                    0
    ## 15                    3
    ## 16                    1
    ## 17                  YYN
    ## 18                02.50
    ## 19                    2
    ## 20 *.xls,*.xlsx, *.xlsb
    ## 21                    0
    ## 22                    3
    ## 23                    1
    ## 24                  YYN
    ## 25                02.50
    ## 26                    2
    ## 27         *.txt, *.csv
    ## 28                    0

``` r
con <- DBI::dbConnect(odbc(),
                      Driver = "SQL Server",
                      Server = "mcobsql.business.nd.edu",
                      UID = "MSBAstudent",
                      PWD = "SQL%database!Mendoza",
                      Port = 3306, 
                      Database = "ChicagoCrime")
```

# R and RStudio
## RStudio Overview
RStudio is an IDE for the R programming language, which is mainly used for statistical analysis.

## Connecting to SQL Server
R requires the following libraries to connect to an SQL server in R:

- _odbc_ – to make the connection to the ELDB server.
- _rstudioapi_ – to provide a secure password entry.
- _dplyr_ – to provide some query syntax.
- _dbplyr_ – to translate the _dplyr_ syntax to SQL.

Import the libraries and create a connection in your RStudio console (replace { } with own credentials):

```r
> library(dplyr)
> library(dbplyr)
> library(odbc)
> library(rstudioapi)
> eldb_con <- dbConnect(odbc(),
+                  Driver = "SQL Server"
+                  Server = ""eldb.qmul-ceg.net) 
+                  Database = "eldb2025" 
+                  UID = "{ceg username}" 
+                  PWD = rstudioapi::askForPassword("Database Password"),  
+                  Port = 1433)
```

A pop-up box will appear asking for your database password.

![](../../_img/Connect/Rimage067.png)

Once you enter your password, you are fully connected to the database and can now access all the available databases and tables under the Connections tab.

![](../../_img/Connect/Rimage068.png)

The _dbplyr_ and _dplyr_ libraries provide the syntax to pass the SQL data into R table objects.

```r
> diabetes<-tbl(eldb_con, "diabetes")
> glimpse(diabetes)
> diabetes %>%
+     filter(area_id =="CH") %>%
+     group_by(ods_code)
```

Or the database can be queried directly using SQL.

```r
> diabetes_tbl<-dbFetch(
+     dbSendQuery(eldb_con, "SELECT TOP 10 * FROM diabetes"))
> print(diabetes_tbl)
```


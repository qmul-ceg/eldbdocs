# R and RStudio

To connect to the SQL server in R you will need the following libraries installed:

- _odbc_ – to make the connection to the ELDB server.
- _rstudioapi_ – to provide a secure password entry.
- _dplyr_ – to provide some query syntax.
- _dbplyr_ – to translate the _dplyr_ syntax to SQL.

Import the libraries and create a connection in your RStudio console:

![](../../_img/Connect/Rimage065.png)

A pop-up box will appear asking for your database password.

![](../../_img/Connect/Rimage067.png)

Once you enter your password, you are fully connected to the database and can now access all the available databases and tables under the Connections tab.

![](../../_img/Connect/Rimage068.png)

The _dbplyr_ and _dplyr_ libraries provide the syntax to pass the SQL data into R table objects.

![](../../_img/Connect/Rimage071.png)

Or the database can be queried directly using SQL.

![](../../_img/Connect/Rimage073.png)
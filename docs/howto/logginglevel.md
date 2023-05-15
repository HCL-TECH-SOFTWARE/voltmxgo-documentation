# Monitoring a Logging Level

## About this procedure
This procedure guides you on how to check your log file using the specific logging level.


## Before you start
 You must use the import domino application.


## Check the logging level

!!!Note
    This Logging Level is specified for import domino application only.

1. Go to Help menu&rarr;Logging level&rarr;click the current level you want. For reference see (link)

    !!!Note
    The default level is **Info**. For each level of logging, you must restart the Iris to take effect the level that you have chosen. After restarting the Iris the current level will be the level that you have chosen and this will be the defualt level of the logging.

## View the logging details

1. For Mac, go to the **Iris** directory. This is found inside your local user directory. 
2. Open the **irisdata**&rarr;**Logs**&rarr;**ielogs** directory.
3. Select and open the `iris.log` file name using **TextEdit** app.

    !!!note
        Upon selecting the logging level, all the lagging properties will be saved in the `iris.log `.
        -It included the date and time, the logging level, and the logging description.

### Expected result
![](../assets/images/dilogging.png){: style="height:80%;width:80%"}



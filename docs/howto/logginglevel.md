# Monitor logging level

## About this procedure
This procedure guides you on how to monitor your log file using the specific logging level.

## Check the logging level

!!!Note
    The logging level in Iris will only affect the logs for importing a domino application at the moment.

1. Go to Help&rarr;Logging level, and  click the current level you want. For your reference, see [Logging levels](../references/reflogginglevels.md).

    !!!Note
        The default level is **Trace**. For each level of logging, you must restart the Iris to take effect the level that you have chosen. After restarting the Iris the chosen level will be the default level of the logging.

## View the logging details
### For mac and windows
1. Go to the **Iris** directory. This is found inside your local user directory. 
2. Open the **irisdata**&rarr;**Logs** directory.
3. Select and open the `iris_development.log` file name using **Text Editor** app.
### Expected result

#### For mac
![](../assets/images/dilogging.png){: style="height:80%;width:80%"}

#### For windows
![](../assets/images/diloggingwin.png){: style="height:80%;width:80%"}
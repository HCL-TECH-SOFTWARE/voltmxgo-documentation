# Set logging level

## About this procedure
This procedure guides you on how to check and set the logging level, and access the log files. For more information, see [Logging levels](../references/reflogginglevels.md). 

!!!Note
    The logging level in Iris will only affect the logs for importing a Domino application at the moment.

## Check the logging level

- Go to **Help** &rarr; **Logging Level**. The current logging level is indicated.

    !!!note
        The default level is **Trace**. 

## Set the logging level

- Go to **Help** &rarr; **Logging Level**, and then choose a logging level based on the level of details you want to find in the logs. To learn the description of each logging level, see [Logging levels](../references/reflogginglevels.md).

    !!!note
        You must restart Volt MX GO Iris after setting a new logging level.

## View the logs

1. From your user directory:

    - For Windows, go to **Iris** &rarr; **irisdata** &rarr; **logs**.

    ![](../assets/images/diloggingwin.png){: style="height:80%;width:80%"}

    - For Mac, go to **Iris** &rarr; **irisdata** &rarr; **logs** &rarr; **ielogs**. 

    ![](../assets/images/dilogging.png){: style="height:80%;width:80%"}

2. Open the `iris_development.log` file to view the logs.


# Logging levels
Logging levels are essential for monitoring and evaluating activities that take place throughout the execution of Volt MX Go Iris. Log files contain information about the events happening in Volt MX Go Iris, especially during Design Import use. Users can select the appropriate logging level based on the level of log details they wish to capture. 

|Logging Level|Description|
|----|----|
|Info|Logs informational messages highlighting the estimated progress of the application. Failing to review the logs in this logging level doesn't result in missing important data.|
|Trace|Logs all the information about the application to give full visibility of what's happening to the application.|
|Error|Logs error events, such as stopping one or more features from correctly functioning, that might still allow the application to continue running.|
|Debug|Logs detailed information about events useful to debug the application.
|Warn|Logs harmful situations, such as process interruption, that don't affect the whole application.|
|Fatal|Logs severe error events that might lead the application to abort.|


<!--
|Info|The standard log level signifies that something has occurred, the application has processed a request, etc. The information captured using the INFO log level should be simply informative, and failing to review them on a regular basis shouldn't result in missing crucial data.|
|Trace|This level of logging is the most detailed, but you usually don't need it unless you need to see everything that's going on in your program and in any third-party tools you use.|
|Error |The log level that should be used when the app runs into a problem that stops one or more features from functioning correctly. You can also look at the ERROR log level for errors.|
|Debug|This level is less detailed than the TRACE level, but it still has more information than you need for everyday use. Use the DEBUG log level to store information that may be needed for deeper analysis and fixing. |
|Warn |The log level that indicates an unanticipated application error has occurred. For instance, a problem or situation that interrupts one of the processes, but not the application as a whole.|
|Fatal|Logs describing an unrecoverable program or system crash, or a major malfunction that requires quick action.|-->


# Logging levels
Log levels are essential for monitoring and evaluating activities that take place throughout the execution of Iris. Log files contain information about the events that happen in Iris, especially during Design Import. Log levels allows the user to select the level they wish to capture during execution of events in Iris.
## Criteria in logging levels

|  **Logging Levels**     | **Description** |
| -----------     | -----------		|
| Info   | The standard log level signifies that something has occurred, the application has processed a request, etc. The information captured using the INFO log level should be simply informative, and failing to review them on a regular basis should not result in missing crucial data.|
| Warn | The log level that indicates an unanticipated application error has occurred. For instance, a problem or situation that interrupts one of the processes, but not the application as a whole.|
| Error | The log level that should be used when the app runs into a problem that stops one or more features from functioning correctly. You can also look at the ERROR log level for errors.|
| Trace| This level of logging is the most detailed, but you usually don't need it unless you need to see everything that's going on in your program and in any third-party tools you use. The TRACE logging setting is likely to be very detailed.|
| Fatal|Logs describing an unrecoverable program or system crash, or a major malfunction that requires quick action.|
|Debug| This level is less detailed than the TRACE level, but it still has more information than you need for everyday use. Use the DEBUG log level to store information that may be needed for deeper analysis and fixing. |

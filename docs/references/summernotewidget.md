# SummernoteEditor widget

The SummernoteEditor widget enables you to add a WYSIWYG editor to your form for handling rich text with links, tables, images, videos, and character styles. 

Following are some use cases of the SummernoteEditor widget:

- **Feedback**: User feedback can comprise multiple lines of text. The SummernoteEditor widget is apt in all the scenarios for taking user feedback.
- **Comments section**: The SummernoteEditor widget is apt for applications that support users’ comments. 

Widgets are added to your application using Iris or from the code. For more information on using widgets in Iris, see [Designing an Application](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_user_guide/Content/Part_II_CreatingAnApplication.html){: target="blank"} in the [Iris User Guide](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_user_guide/Content/Introduction.html){: target="blank"}.

## Methods

|setData| | |
|---|---|---|
||Description|This API enables you to set a value onto the SummernoteEditor widget.|
||Syntax|`setData(data)`|
||Parameters|`data`<br>This is mandatory and specifies the text value set on the SummernoteEditor widget.|
||Return value|none|
||Remarks|Setting the value to the SummernoteEditor widget can be done without explicitly calling the syntax. Assigning a value on the "data" property triggers the `setData` function. 
||Example|`self.instanceDetails.data = *value*`|
|**getData**| | |
||Description|This API enables you to get the value from the SummernoteEditor widget.|
||Syntax|`getData()`|
||Return value|Returns a string containing the HTML string content of the value entered into the SummernoteEditor widget.|
||Remarks|Getting the value of SummernoteEditor widget can be done without explicitly calling the syntax. Calling the `data` property triggers the `getData` function.|
||Example|`data["Details"] = self.instanceDetails.data`|

## Properties

|data|||
|---|---|---|
||Description|Specifies a general or descriptive text for the SummernoteEditor widget.|
|**ID**|||
||Description|Unique identifier consisting of alphanumeric characters.|

## Additional information

To learn how to import the Summernote Editor component, see [Import Summernote Editor](../howto/summernote.md).
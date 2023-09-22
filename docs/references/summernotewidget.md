# Summernote Editor 

The Summernote Editor component enables you to add a WYSIWYG editor to your form for handling rich text with links, tables, images, videos, and character styles. 

Following are some use cases of the Summernote Editor component:

- **Feedback**: User feedback can comprise multiple lines of text. The Summernote Editor component is apt in all the scenarios for taking user feedback.
- **Comments section**: The Summernote Editor component is apt for applications that support users’ comments. 

For more information on components in Iris, see [Use Components](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_user_guide/Content/C_UsingComponents.html){: target="blank"} and [Creating Applications with Components](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_user_guide/Content/C_DesigningWorkingWithComponents.html).

## Methods

|setData| | |
|---|---|---|
||Description|This API enables you to set a value onto the Summernote Editor component.|
||Syntax|`setData(data)`|
||Parameters|`data`<br>This is mandatory and specifies the text value set on the Summernote Editor component.|
||Return value|none|
||Remarks|Setting the value to the Summernote Editor component can be done without explicitly calling the syntax. Assigning a value on the "data" property triggers the `setData` function. 
||Example|`self.instanceDetails.data = *value*`|
|**getData**| | |
||Description|This API enables you to get the value from the Summernote Editor component.|
||Syntax|`getData()`|
||Return value|Returns a string containing the HTML string content of the value entered into the Summernote Editor component.|
||Remarks|Getting the value of Summernote Editor component can be done without explicitly calling the syntax. Calling the `data` property triggers the `getData` function.|
||Example|`data["Details"] = self.instanceDetails.data`|

## Properties

|data|||
|---|---|---|
||Description|Specifies a general or descriptive text for the Summernote Editor component.|
|**ID**|||
||Description|Unique identifier consisting of alphanumeric characters.|

## Additional information

To learn more, see [Summernote Editor](https://summernote.org/){: target="_blank" rel="noopener noreferrer"}.
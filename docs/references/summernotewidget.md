# Summernote Editor 

The Summernote Editor component enables you to add a WYSIWYG editor to your form for handling rich text with links, tables, images, videos, and character styles. 

Following are some use cases of the Summernote Editor component:

- **Feedback**: User feedback can comprise multiple lines of text. The Summernote Editor component is apt in all the scenarios for taking user feedback.
- **Comments section**: The Summernote Editor component is apt for applications that support users’ comments. 

For more information on components in Iris, see [Use Components](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_user_guide/Content/C_UsingComponents.html){: target="blank"} and [Creating Applications with Components](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_user_guide/Content/C_DesigningWorkingWithComponents.html).

## Methods

Methods are used by the form to interact with the Summernote Editor component.

**To configure a method**:

1. In the Project Explorer in Volt Iris, click the Templates tab.
2. Expand the components node, if needed, and then select the component. In this case, select Summernote Editor.
3. In the **Properties** pane, click the **Action** tab.
4. Click **Manage Methods** to open the **Manage Methods** dialog.

You can now configure the component methods. For more information, see [Manage Methods](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_user_guide/Content/C_CreatingComponent.html#manage-methods-of-a-component-with-a-contract){: target="_blank" rel="noopener noreferrer"}.


|setData| | |
|---|---|---|
||Description|This method enables you to set a value for the Summernote Editor component.|
||Syntax|`setData(data)`|
||Parameters|`data`<br>A string parameter that sets the value of the Summernote Editor component.|
||Return value|none|
||Remarks|Setting the value of the Summernote Editor component can be done without explicitly calling the syntax. Assigning a value on the "data" property triggers the `setData` function. 
||Example|`self.instanceDetails.data = "Test"`|
|**getData**| | |
||Description|This method enables you to get the value of the Summernote Editor component.|
||Syntax|`getData()`|
||Return value|Returns a string containing the HTML string content of the value entered in the Summernote Editor component.|
||Remarks|Getting the value of Summernote Editor component can be done without explicitly calling the syntax. Calling the `data` property triggers the `getData` function.|
||Example|`object["Details"] = self.instanceDetails.data`|
|**checkOrRemoveFile**|||
||Description|This method enables you to check if the Summernote Editor component has a specific attachment on its content. This method also enables you to remove the attachment file if needed.|
||Syntax|`checkOrRemoveFile(fileName, removeFile = false)`|
||Parameters|`fileName`</br> A string value parameter for checking if a specified filename exists on the content of the Summernote Editor component. </br></br> `removeFile` </br> An optional boolean parameter for enabling the removal of the file from the content of the Summernote Editor component when it's set to *true*. By default, the parameter is set to *false*.|
||Return value|Returns a Boolean value of *true* if a file exists, and *false* if a file isn't found in the content ofthe  Summernote Editor component.|
||Remarks|The `removeFile` parameter can be left out if you won't remove a file from the Summernote Editor component. Only the `fileName` parameter is required.|
||Example|For only checking if a file exists: </br> `self.instanceDetails.checkOrRemoveFile (“TestFile.pdf”)` </br></br> For removing a file:</br> `self.instanceDetails.checkOrRemoveFile(“TestFile.pdf”, true)`
|

## Properties

You need a default property to build the Summernote Editor component. The table shows properties that hold the values of a field. 

**To configure a property**:

1. In the **Project Explorer** in Volt Iris, click the **Templates** tab.
2. Expand the components node, if needed, and then select the component. In this case, select Summernote Editor. 
3. In the **Properties** pane, click the **Component** tab.
4. Click **Manage Properties** to open the **Manage Properties** dialog.

You can now configure the component properties. For more information, see [Manage Properties](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_user_guide/Content/C_CreatingComponent.html#manage-properties-of-a-component-with-a-contract){: target="_blank" rel="noopener noreferrer"}.

|data|||
|---|---|---|
||Description|It's the called property when assigning or retrieving a value from the Summernote Editor component.|
|**ID**|||
||Description|Unique identifier consisting of alphanumeric characters.|

## Additional information

To learn more, see [Summernote Editor](https://summernote.org/){: target="_blank" rel="noopener noreferrer"}.
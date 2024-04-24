# Configure VoltFormula's Rosetta API Options

## About this procedure

This procedure describes how to configure the Rosetta API based on what you need when using the Rosetta formula.

- API Configuration
- Intellisense Configuration
- Conversion Configuration 

## Procedure

1. Click the **Project Settings** icon .
    
    ![settings](../assets/images/vfrosettasetting.png){: style="height:80%;width:80%"}

2. In the **Project Setting** window, click the **VoltFormula** tab.

    !!!tip
        Hover over the **info** tooltip icon beside the labels or text boxes for more information.
    
    ![settings](../assets/images/vfsetting.png)

3. Enter values and select options as required. Refer to the following table for more information. 

    |Rosetta area | Rosetta area sections | Description|
    |-------------|------------|------------|
    |**API Configuration**| |Allows you to configure options specific to the APIs' implementation and execution.  |
    | |**Register Custom API**|Allows you to upload a file with custom APIs. Refer to the [API reference documentation](../javadoc/index.html){: target="_blank" rel="noopener noreferrer"} under the rosetta-api module for method `registerAPI` for more details on expected file format and parameters.|
    | |**Preferred API Implementation**| Allows you to specify whether to execute the **Notes Formula** or the **Open Formula** implementation when calling an API method, which has an existing implementation in either formula language. Example, `@Abs()` and `=ABS()` are encapsulated by Rosettas `abs()` method. Selecting `Notes` option makes Rosetta call the Notes implementation. Usually, either implementation behaves the same. But in other cases, there may be differences in parameters, execution, or returned results. For example, most Notes formula functions allow lists to be passed in as arguments while OpenFormula allows lists as ranges for only a number of methods. Refer to the [API reference documentation](../javadoc/index.html){: target="_blank" rel="noopener noreferrer"} for details on each API.|
    | **Intellisense Configuration**| |Allows you to include names of formulas that won't be implemented and not yet implemented in the formula list IntelliSense. When **Include no plans to implement items** is selected, the names of the formulas that won't be implemented are shown as ~~strikethrough text~~. If **Include not yet implemented items** is selected, the names of the formulas that aren't yet implemented are shown but appears dimmed.|
    |**Converter Configuration**| |Allows you to configure options related to how formulas are converted into their corresponding Rosetta-enabled JavaScript.|
    | |**Passthrough unrecognized formula language into JavasSript conversion results**|Allows you to specify whether the converter allows unrecognized formula code to be part of the JavaScript conversion results without any massaging, or if it should throw an error when encountering unrecognizable formula code. This allows greater flexibility but also exposes the API to injection of code. **Use with care**.|
    | |**Convert as native Javascript**|Allows you to specify whether the converter uses native JavaScript or API calls for methods where a native JavaScript function exists. For example, convert `@If( )` into JavaScript native `if( )` or call the API `rosettajs.Logical.if( )`.  Sometimes, it makes sense and produces cleaner code to select "convert into native JavaScript" than using the API. Other times, you may want to go through the API call itself to allow for additional checks and/or handle the parameters differently.|
    | |**Conversion Delay**|Allows you to specify the delay in millisecond before the converters are invoked for a formula conversion. The default is normally acceptable. If there is no delay, the converters are re-invoked on every keystroke when entering the formula (calling the converters this often isn't needed). A longer delay invokes the converters less often.|
    |**Version Information**| |Indicates the `SDK` plugin,`API`,`Converter`, and `Prettifier` versions.|

3. Click **Done**.

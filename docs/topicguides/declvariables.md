# Using variables in formulas

## Overview

There are two mechanisms by which the Rosetta Converter accepts and converts variables into JavasScript:

- [LET function](https://support.microsoft.com/en-us/office/let-function-34842dd8-b92b-4d3f-b325-b8b8f9908999){: target="_blank" rel="noopener noreferrer"} in Excel[^1]
- JSP style syntax (code passthrough)

[^1]: Excel is a registered trademark or trademark of Microsoft Corporation in the United States and/or other countries.

## Using LET function with OpenFormula

**LET function**

```
=LET(x, 5, SUM(x, 1))
```
![LET function example](../assets/images/vflet.png)

## Using JSP style syntax

The converter uses **JSP expression** syntax in **OpenFormula** formulas to provide capabilities for formula conversion not currently possible with strict OpenFormula syntax. For more information, see [**JSP expression syntax**](https://docs.oracle.com/javaee/5/tutorial/doc/bnaov.html){: target="_blank" rel="noopener noreferrer"}.

Example:

- **OpenFormula:**

    ![OpenFormula example](../assets/images/vfjsp.png)

Although Notes formula language already provides means to declare variables, the converter can also use the **JSP expression** syntax in a ***Notes*** formula.

Examples:

- **Notes formula** with native notes variable declaration expression:
    
    ![Notes formula example](../assets/images/vfnotesnative.png)


- **Notes formula** with JSP-based variable declaration expression:

    ![Notes formula example](../assets/images/vfnotesjsp.png)

    
!!!note
    To use JSP expression in formulas, select **Passthrough unrecognized formula language into JavasSript conversion results** checkbox. For more information, see [**Configure VoltFormula's Rosetta API Options**](../howto/configrosetta.md).

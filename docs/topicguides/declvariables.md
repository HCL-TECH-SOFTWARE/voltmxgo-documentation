# Declaring variables in formulas

## Using variables in formulas

There are two mechanism by which the Rosetta Converter accepts and converts variables into JavasScript:

- LET function
- JSP style syntax (code passthrough)

## LET function with OpenFormula

**Let function**

```
=LET(x, 5, SUM(x, 1))
```
![alt text](../assets/images/vflet.png)

## JSP Style Syntax

The converter makes use of **JSP expression** syntax in **OpenFormula** formulas to provide capabilities to formula conversion not currently possible with strict OpenFormula syntax. For more information, see [**JSP expression syntax**](https://docs.oracle.com/javaee/5/tutorial/doc/bnaov.html){: target="_blank" rel="noopener noreferrer"}.

Example:

- **OpenFormula:**

    ![alt text](../assets/images/vfjsp.png)

Although Notes formula language already provides means to declare variables, the converter can also make use of the **JSP expression** syntax in a ***Notes*** formula.

Examples:

- **Notes formula** with native notes variable declaration expression:
    
    ![alt text](../assets/images/vfnotesnative.png)


- **Notes formula** with JSP based variable declaration expression:

    ![alt text](../assets/images/vfnotesjsp.png)

    
!!!note
    To use JSP expression in formulas, select **Passthrough unrecognized formula language into JavasSript conversion results** checkbox. For more information, see [Configure VoltFormula's Rosetta API Options](../howto/configrosetta.md).

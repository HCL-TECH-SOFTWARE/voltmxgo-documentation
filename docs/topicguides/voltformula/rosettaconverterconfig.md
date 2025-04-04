# Rosetta Converter configuration options

## Overview

The Rosetta Converter converts formula code (Notes or Excel[^1]/OpenFormula) into a JavaScript equivalent. It takes advantage of the available Rosetta API library implementations as needed. It creates a JavaScript code snippet comprised of the native JavaScript elements as well as calls to the corresponding APIs. 

The Rosetta Converter is an integral part of the VoltFormula process. It allows the developer to write code using formula languages and takes care of providing the JavaScript equivalents. It is written in JavaScript using regex rules and [ANTLR (ANother Tool for Language Recognition)(antlr4)](https://www.antlr.org/ "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../assets/images/external-link.svg){: style="height:13px;width:13px"} rules.

[^1]: Excel is a registered trademark or trademark of Microsoft Corporation in the United States and/or other countries.

## Configuration options

The Rosetta Converter has several options to manipulate the formula to JavaScript conversion behaviors. All options are accessible directly through the converter's configuration object getters and setters. In Volt MX Go Iris, you can access these options on the VoltFormula tab in the Project Settings dialog.

- **allowPassthrough** 

    This option is set to *false* by default.

    Formula language that's not known are transferred to the JavaScript results intact. In this way, the formula can be artificially altered with code that's not necessarily formula language, and the resulting JavaScript will contain such code. 
    
    !!!warning "Important"
        Use this option with caution as it can be used to inject executable code.

    Example:

    ```
    n = @Abs(-5);
    console.log(n);
    ```

    In the example, `console.log()` isn't a valid formula language. If the option **allowPassthrough** is true, then the resulting JavaScript looks like this:

    ```
    var n = rosettajs.Math.abs(-5);
    console.log(n);
    ```

    If the option **allowPassthrough** is false, which is the default, then conversion result throws an exception that looks something like this:

    ```
    [{
        "line": 2,
        "column": 11,
        "message": "no viable alternative at input 'console.log('"
    }]
    ```

- **_stripNumbers**

This option is set to true by default. 

- **_paramAsFieldName** 

This option is set to true by default.

- **_nativeness**


This option controls whether conversion into native JavaScript vs calling API functions for code elements that exist natively in JavaScript, such as:

    - @Do
    - @DoWhile
    - @For
    - @If
    - @While
    - @True
    - @False

Example:

when "@True": true,

```
yes := @True
```

converts to:

```
var yes = true;
```

when "@True": false,

```
yes := @True
```

converts to:

```
var yes = rosettajs.Logical.true();
```

## Default

```java
{
  _allowPassthrough: false,
  _stripNumbers: true,
  _paramAsFieldName: true,
  _nativeness: {
    "_global": true, // true =all native js
    "@Do": true,
    "@DoWhile": true,
    "@For": true,
    "@If": true,
    "@While": true,
    "@True": true,
    "@False": true
  },
}
```

## Getters, setters, and checkers

- `<converter>.config.getAllowPassthrough()`
- `<converter>.config.getNativeness(formula)`
- `<converter>.config.getParamAsFieldName()`
- `<converter>.config.getStripNumbers()`
- `<converter>.config.setAllowPassthrough(allow)`
- `<converter>.config.setNativeness(formula, native)`
- `<converter>.config.setParamAsFieldName(convert)`
- `<converter>.config.setStripNumbers(strip)`

## Additional information

For more information, see [Configure VoltFormula's Rosetta API Options](../../howto/voltformula/configrosetta.md).

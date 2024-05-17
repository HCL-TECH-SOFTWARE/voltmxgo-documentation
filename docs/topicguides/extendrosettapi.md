# Extending Rosetta API

## Overview

Since the API is a **JavaScript object**, you can extend the API library by adding to the object structure any number of custom categories and/or method definitions, as long as you adhere to the schema structure. For this, helper extension registration methods are provided within the API configuration object of the Rosetta library.

## Samples

- Sample array of JSON objects used to extend the API via the `<rosettajs>.API.registerAPIs()` method using note custom category and custom language capabilities:

    ```json
    [
        {
            'name': 'hello0',
            'lang': 'notes function',
            'cat': 'Text',
            'code': function (name) {
            return 'hello ' + name;
            }
        },
        {
            'name': 'goodbye',
            'lang': 'notes command',
            'cat': 'Text',
            'code': function (name) {
            return 'bye bye ' + name;
            }
        },
        {
            'name': 'weather',
            'lang': 'open formula',
            'cat': 'CustomMailCategory',
            'code': function (zip) {
            return 'Sunny in ' + zip;
            }
        },
        {
            'name': 'getEmployeeId',
            'lang': 'MyCustomFormulaLang',
            'cat': 'MyEmployeeMethods',
            'code': function (id) {
            return id + 'is Chief Custodian';
            }
        }
        ]
    ```

- Sample array of JSON objects used to extend the API via the `<rosettajs>.API.registerAPIs()` method (note mixed code):

    ``` json    
    [
        {
            'name': 'MyAbs(n)',
            'lang': 'notes function',
            'cat': 'Math',
            'code': '@Abs(n);'
        },
        {
            'name': 'AbsPlus1',
            'lang': 'notes function',
            'cat': 'Custom',
            'code': n => Math.abs(n) + 1
        },
        {
            'name': 'MyExcelAbs(n)',
            'lang': 'open formula',
            'cat': 'Custom',
            'code': '=ABS(n)'
        }
    ]
    ```

## Using Formula language in the extension code

In addition to extending via **JavaScript implementations**, when the `code` property of the extension input has Formula language instead of a JavaScript function, the registration method converts the formula into JavaScript and registers the resulting JavaScript as the code for the particular extension.

## Additional information

For more information, see [Register and unregister custom Rosetta API](../howto/regunregconfig.md). 

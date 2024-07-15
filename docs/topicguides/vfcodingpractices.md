# VoltFormula useful tips and information 

## Accessing data from UI context versus database context

### How does VoltFormula address Database Fields vs Form Fields DOM elements?

In Domino, the field data of a form field is directly and automatically tied to the database. Changing the value of the field in the UI changes the value in the database when the form is saved. In Volt MX Go Iris, a field on a form in the UI isn't directly tied to the back end by default.

For VoltFormula, the API implementations of `@GetField` and `@SetField` Notes Formula functions address the specified field as a database field or UI form field by default, such as setting API context to 'all' by default, with the latter one overriding the database field value if applicable. For `@GetField` and `@SetField` to be strict with the database fields, one must set the context to *db*, such as `@Context("db");`, since the default is to try to get it from all sources: the database first, then the UI second, and if the UI exists, the database value is ignored.

**Examples**

- To access data from the database field and then from the UI form field if it exists:

    Formula:

        ```
        @Context("all");  <-- optional, as `all` is already the default context
        @GetField("Foo");
        ```
    JavaScript:

        ```javascript
        voltmx.rosettajs.VoltFormula.context("local"); // optional, as `all` is already the default context
        voltmx.rosettajs.Document.getField("Foo");
        ```

- To access data from the UI form fields only:

    Formula:

    ```
    @Context("local");
    @GetField("Foo");
    ```

    JavaScript:

    ```javascript
    voltmx.rosettajs.VoltFormula.context("local");
    voltmx.rosettajs.Document.getField("Foo");
    ```

- To access data from the database fields only:

    Formula:

    ```
    @Context("db");
    @GetField("Foo");
    ```
    
    JavaScript:

    ```javascript
    voltmx.rosettajs.VoltFormula.context("db");
    voltmx.rosettajs.Document.getField("Foo");
    ```

## Formulas

### Mixing formula languages with other languages

The Rosetta Converter can process formula language mixed with other language artifacts by making use of the **allowPassthrough** option. This way, a formula snippet of code can be augmented with other code, such as JavaScript, to have the resulting converted code combine the different languages for a desired result. For more information, see [**Using JSP style syntax**](declvariables.md#using-jsp-style-syntax) and **allowPassthrough** option in [**Rosetta Converter configuration options**](rosettaconverterconfig.md#configuration-options).

### How does VoltFormula maintain project formulas?

Every JavaScript snippet created from a formula conversion process is tracked in Volt MX Go Iris via a formula ID formatted as `@formula_<unid>`. 

Example: `@formula_1714617343910.3508708517553434` 

When the formula code is changed on the JavaScript side for a given formula result, Volt MX Go Iris tracks it as a discrepancy between the formula code and the JavaScript code. If the developer attempts to edit the formula language after making changes to the corresponding formula JavaScript code, Volt MX Go Iris warns about the formula discrepancy. The developer has the option to either restore the JavaScript code to the original formula or view the formula without altering the JavaScript counterpart.

In a Volt MX Go Iris project, the formulas defined are stored under `resources/rosetta` in the project directory in the Volt MX Go Iris workspace. These files arent exposed in the Volt MX Go Iris UI project files.
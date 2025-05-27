# Representing view selection formulas in API

## SELECT (Formula Language)

The SELECT reserved word defines criteria for the selection of documents in an agent that runs a formula, in a view, or during replication. You use a SELECT statement before an expression to define the set of documents that you want to change, see in a view, or replicate.

## Syntax

`SELECT formula ;`

## Usage

Using SELECT in the formula eliminates the need to go through the database to select the documents. You can run the filter macro on all the documents in the database, and the SELECT statement performs the selection process. For views, a selection formula can ideally be used at design time in the definition of the view on the server. The view, when accessed, presents entries that match the formula.

Selection Formulas retrieve a specified list of documents that match the selection formula.

With Volt MX Go, the database is somewhat hidden. The client communicates with the backend using services such as Integration, Object, Offline, Orchestration, or Workflow. Access to the Notes database is through an adapter within a Foundry Service. Object Service is the service for building Enterprise apps, so this is the first implementation choice. Integration Service and Offline Object Service can be secondary implementation choices.

A client app can write to any of these backend services, but each requires a different set of APIs.

From Rosetta's standpoint, we need to support each of these services within our APIs that use them. To do this, we're expanding the app config support:

```
const config = {
  _notes: "notes",
  _openFormula: "openformula",
  _defaultAPI: "notes",

  serviceType: {
    _integration: "integration",
    _objects: { online: "online-objects", offline: "offline-objects" },
    _orchestration: "orchestration",
    _workflow: "workflow",
    _engagement: "engagement",
    _defaultServiceType: "online-objects" },

  framework: {
    _voltmx: "vmx",
    _javascript: "js",
    _defaultFramework: "js"
  }
};
```

The `defaultService` is Object services (`object`). Each API that requires these services needs to support all the services, the initial implementation should be using the Object Services.

## Document selection

The selection of documents involves: 

1. Calling `SelectDocuments()` to perform the SELECT formula operation.

    `export async function SelectDocuments (svcName, viewName, formulaSelection)`

    wherein:

    `svcName` - serverName : database (serverName isn't used, database is the Object Service name)

    `viewName` - Form or Table name within the Object Service (maps to Notes DB Table name)

    `formulaSelection` - Notes selection formula for selecting documents for API to return

    !!!note
        The API returns a *Promise*, which has to be handled by the caller to access returned data.

1. Fetching **all** documents from the specified Notes database (Object Service) with the API.

    The following opens the database using Object Service and retrieves all documents:

    ```
    if (FileOpenDatabase(svcName, viewName)) {
      let promise = All();
      promise.then( onSuccess, onFailure );
    }
    ```

1. Filtering the document list with the API based on Notes `formulaSelection`.

    - Put the Notes `formulaSelection` within an `"@If"` test to return true if the selection is a match for a particular document.

        `formulaSelection = "@If(" + formulaSelection + "; 1 ; 0);";`

    - Use the JavaScript from Notes converter to generate a JavaScript string for the `formulaSection`.

        `let js = getRosettaJSFromNotes(rosettajs, formulaSelection);`

        `js = "try { return " + js + " } catch(err) { return 0; }";`

    - Create the db field names and values as JavaScript strings so that the `formulaSelection` can reference them.

        ```
        // dynamically create db variables
        for (let i=0; i < results.length; i++) {
            let selection = "";

            for (let k in results[i]) {
                let value = results[i][k];
                let delimiter = "";
                if (typeof value === "number") { 
                  delimiter =  ""; 
                } else { 
                    value = value.startsWith('[') && value.endsWith(']') ?
                    JSON.parse(results[i][k]).toString() : value;
                }
                selection += 'const ' + k + ' = ' + delimiter + value + delimiter + ';';
            }
    
            // Prepend the DB fields to formula selection string.**
     
            // Add formulaSelection query to Function
            selection += js;

            // Perform the formula selection. 
            // Execute the javascript string using the Javascript "Function()" API.  
            // If it returns "true" then the document is added to the results.

            /* eslint-disable */
            let func = new Function("rosettajs", selection);
            /* eslint-enable */
            let select = func(rosettajs);

            // select record if condition is met
            if (select) { 
               selectedResults.push(results[i]); 
            }
        }
        ```

    !!! note

        Results are returned in a *Promise*.
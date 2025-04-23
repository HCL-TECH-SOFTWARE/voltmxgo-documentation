# Additional considerations

Lists additional considerations you must be aware of when using Volt MX Go and related actions you must take.

## Domino server and Notes database names used within APIs

When importing a Domino application into Volt Iris, Design Import converts formulas as defined in Domino. The formula functions that refer to Domino databases use a server name and a Notes `.nsf` database name. These server and database references must be replaced with the Volt MX Object Service name created by Design Import.

Example 1:

In Domino: `@Command([FileOpenDatabase]; server : database ; view; key )`

In Volt Iris: `@Command([FileOpenDatabase]; object-service-name ; view; key )`

Example 2:

In Domino: `@Command([Compose]; server : database ; form )`

In Volt Iris: `@Command([Compose]; object-service-name ; form )`

!!! warning "Important"

    Anywhere the server name and Notes `.nsf` database name appear in a formula must be replaced with the Object Service name.

## Differences in the behavior of `@Command` formulas that access data in Notes and Volt Iris

- In Notes, the `@Commands` to access data provide UI support when invoked. In Volt Iris, these `@Commands` are implemented as commands without UI support.

- In Notes, you can call `@Compose` without explicitly calling `@FileOpenDatabase`. In Volt Iris, you are required to call `@FileOpenDatabase` before calling `@Compose` or before calling any other DB-related function.

- In Volt Iris, many DB `@Functions` depend on the currently selected document. So not only does the database need to be open, but a document needs to be selected. This can be done as part of the call to `@FileOpenDatabase` using the **key** field or by using specific VoltFormula APIs that set the current document.

After Design Import completes the import of the Domino application that includes formulas, update the code to include calls to `@FileOpenDatabase` where needed and set the currently selected document.

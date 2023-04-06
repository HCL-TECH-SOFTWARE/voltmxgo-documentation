# Introducing Volt MX Go

Volt MX Go modernizes and extends the value of your Domino applications with the market leading, multi-experience platform Volt MX by:

- connecting Volt Foundry to your Domino applications with a dedicated Domino Adapter via the Domino REST API while guided by the simple and fast First Touch app
- modernizing or creating new multi-experience applications in Volt Iris on your Domino back-end data and applications
- expanding who can code applications built in Domino through VoltFormula, allowing for app modernization or migration without requiring a complete rewrite of the code
- importing existing Domino views, forms, and fields into Volt Foundry via Design Import to get a head start on your Volt MX Go applications 

Volt MX Go includes the following components:

- VoltFormula
- Design Import
- Domino Adapter
- First Touch
- Domino REST API

## VoltFormula

VoltFormula expands who can code Domino applications by allowing app modernization or migration without requiring a complete rewrite of the code. VoltFormula includes the following features:

- Execution of a defined list of APIs for NotesFormula and OpenFormula through the Rosetta API library.
- Conversion of formulas into Rosetta API Javascript through Rosetta converter.
- Provides developers with a custom version of Volt Iris to allow them to:
    - Add formulas and convert them to the appropriate Rosetta API Javascript.
    - Edit resulting Javascript formulas.
    - See the results of the formula being written.
    - Use IntelliSense for suggestions of APIs available and associated help text.
    - Choose UI widgets from the default widget library equivalent to NotesFormula UI widgets (for example, @prompt to paint dialog in a window).
- Provides sample formulas
- Configure Rosetta in Iris to specify how the conversion of formulas to Javascript behaves. For example, should the “If” statement become a Rosetta call to API or convert to native Javascript “If”.
- Configure Rosetta for how API behaves when running under an app created in Iris. For example, should it execute OpenFormula ABS formula or NotesFormula ABS formula.

## Design Import

Design Import reads a Domino app through the Domino REST API, retrieves design elements from the app, including forms, views, and agents, and presents them to the user. The user can then decide which forms and fields to import. 

Design Import builds the forms and views within Volt Iris and make them actionable against object services in the Domino Adapter (CRUD operations). The forms and views are presented as a simplified list for better navigation.
## HCL Domino Adapter

The HCL Domino Adapter makes Domino a core part of the Foundry Object Services so that Volt MX apps can interact with Domino databases in the same way they can for relational databases. With the Domino Adapter, you can connect to your Domino database as an endpoint via the Domino REST API. Domino Adapter includes the following features: 

- Form-based CRUD (post, get, put, delete)
- Form-based PATCH 
- View-based GET (non-parameterized) 

## First Touch

The First Touch app walks the administrator through establishing a connection to the Domino server and installs and presents users with a sample application (“Recipes”) in Iris to show how to use the Domino Adapter, connect Volt Foundry to the Domino back end, and leverage the Domino Adapter and Domino REST APIs. The First Touch app promotes a good user experience when establishing connections and importing sample apps into Volt Foundry by:

- gathering necessary data from the administrator to connect to the Domino REST API server
- authenticating using the credentials, creating schema and scope, creating view and app, and initializing inside the Domino REST API
- preparing a zip file for import into Volt Foundry and importing the app
- displaying a message informing the user that everything is ready

The sample application has features such as:

- displaying recipe cards that are clickable to show list of ingredients and instructions
- performing CRUD operations on Domino back end to create, edit, delete a recipe 

## Domino REST API

HCL Domino REST API provides secure REST API-based access to HCL Domino servers and databases. Designed to highlight Domino as a world class, modern, standards-compliant, cloud native and enterprise-level collaboration platform, it adds contemporary REST APIs to Notes and Domino, enabling a modern programming experience with the tools of your choice. 

For more information, see [HCL Domino REST API Documentation](https://opensource.hcltechsw.com/Domino-rest-api/index.html).


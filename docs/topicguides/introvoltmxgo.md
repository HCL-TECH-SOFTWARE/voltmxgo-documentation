# Introducing Volt MX Go

Volt MX Go modernizes and extends the value of your Domino applications with the market-leading, multi-experience platform Volt MX by:

- connecting Volt Foundry to your Domino applications with a dedicated Domino Adapter via the Domino REST API while guided by the simple and fast First Touch app
- modernizing or creating new multi-experience applications in Volt Iris on your Domino back-end data and applications
- expanding who can code applications built in Domino through VoltFormula, allowing for app modernization or migration without requiring a complete rewrite of the code
- importing existing Domino views, forms, and fields into Volt Foundry via Design Import to get a head start on your Volt MX Go applications 

Volt MX Go includes the following components:

- [First Touch](#first-touch)
- [Design Import](#design-import)
- [VoltFormula](#voltformula)
- [Domino Adapter](#domino-adapter)
- [Domino REST API](#domino-rest-api)
- [VoltScript](#voltscript)

![Volt MX Go](../assets/images/VoltMXGoDiagram.png)

## First Touch

First Touch walks the administrator through establishing a connection to the Domino server and installs and presents users with a sample recipe catalog app in Volt Iris to show how to use the Domino Adapter, connects Volt Foundry to the Domino back end, and leverages the Domino Adapter and Domino REST APIs. The First Touch app promotes a good user experience when establishing connections and importing sample apps into Volt Foundry by:

- gathering necessary data from the administrator to connect to the Domino REST API server
- authenticating using the credentials, creating schema and scope, creating views and applications, and initializing inside the Domino REST API
- preparing a zip file for import into Volt Foundry and importing the app
- displaying a message informing the user that everything is ready

The [sample recipe catalog app](firsttouchapp.md) has features such as:

- displaying recipe cards that are clickable to show list of ingredients and instructions
- performing CRUD operations on Domino back end to create, edit, delete a recipe

## Design Import

Design Import reads a Domino application through the Domino REST API, retrieves design elements from the application, including forms, views, and agents, and presents them to the user. The user can then decide which forms and fields to import.

Design Import builds the forms and views within Volt Iris and makes them actionable against object services in the Domino Adapter (CRUD operations). The forms and views are presented as a simplified list for better navigation.

## VoltFormula

VoltFormula expands who can code Domino applications by allowing application modernization or migration without requiring a complete rewrite of the code. VoltFormula includes the following features:

- Execution of a defined list of APIs for NotesFormula and OpenFormula through the Rosetta API library.
- Conversion of formulas into Rosetta API JavaScript through Rosetta converter.
- Provides developers with a custom version of Volt Iris to allow them to:
    - Add formulas and convert them to the appropriate Rosetta API JavaScript.
    - Edit resulting JavaScript formulas.
    - See the results of the formula being written.
    - Use IntelliSense for suggestions of APIs available and associated help text.
    - Choose UI widgets from the default widget library equivalent to NotesFormula UI widgets (for example, @prompt to paint dialog in a window).
- Provides sample formulas.
- Maintains list of formulas used in applications.
- Configuration of Rosetta in Volt Iris to specify how the conversion of formulas to JavaScript behaves. For example, should the `If` statement become a Rosetta call to API or convert it to native JavaScript `If`.
- Configuration of Rosetta for how API behaves when running under an application created in Volt Iris. For example, should the API execute OpenFormula ABS formula or NotesFormula ABS formula.

## Domino Adapter

Domino Adapter makes Domino a core part of the Volt Foundry Object Services so that Volt MX applications can interact with Domino databases in the same way they can for other object service endpoint types, such as relational databases. Domino Adapter access to a Domino database is via the Domino REST API. Domino Adapter includes the following features:

- Form-based CRUD (post, get, put, delete)
- Form-based PATCH
- View-based GET
- Offline objects within the limits of Volt Foundry

## Domino REST API

HCL Domino REST API provides secure REST API-based access to HCL Domino servers and databases. Designed to highlight Domino as a world class, modern, standards-compliant, cloud native and enterprise-level collaboration platform, it adds contemporary REST APIs to Notes and Domino, enabling a modern programming experience with the tools of your choice.

For more information, see [HCL Domino REST API Documentation](https://opensource.hcltechsw.com/Domino-rest-api/index.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"}.

## VoltScript

VoltScript is a [BASIC](https://en.wikipedia.org/wiki/BASIC "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"} scripting language evolved from LotusScript&#174;, which was developed for the Lotus Software family of products. The language has been extended for use with HCL Volt MX Go as a server-side scripting language running within the Foundry middleware layer. VoltScript includes:

- Visual Studio Code extension for allowing developers to write code in VS Code
- Linux Docker image for allowing Mac developers to use the VS Code extension
- Language enhancements for improving consistency and ease of use
- Open-source helpers, such as a library with advanced collection and map collections, a unit testing framework, and a serializer and deserializer for JSON-based object persistence
- A toolkit for scaffolding the various VoltScript extensions and script code and autogenerating starter code and related documentation
- Various VoltScript Extensions for supporting various processes, such as data access over HTTP to specific or generic REST services, handling JSON data, interacting with the operating system and files, managing input parameters

To learn more about the **early access version** of VoltScript, see [VoltScript Documentation](https://help.hcltechsw.com/docs/voltscript/early-access/index.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../assets/images/external-link.svg){: style="height:13px;width:13px"}.

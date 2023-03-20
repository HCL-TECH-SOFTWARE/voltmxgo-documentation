# Introducing Volt MX Go

Volt MX Go modernizes and extends the value of your *Domino* applications with the market leading, multi-experience platform Volt MX by:

- connecting Volt Foundry to your Domino applications with a dedicated Domino Adapter via Domino REST API while guided by the simple and fast First Touch application
- modernizing or creating new multi-experience applications in Volt Iris on your Domino back-end data and applications
- expanding who can code *Domino* applications through VoltFormula, allowing for app modernization or migration without requiring a complete rewrite of the code
- importing existing *Domino* views, forms, and fields into Volt Foundry via Design Import to get a head start on your Volt MX Go applications 

Volt MX Go includes the following components:

- *VoltFormula*
- *Design Import*
- *Domino Adapter*
- *First Touch*
- *Domino REST API*

## VoltFormula

## Design Import

## Domino Adapter

Domino Adapter intends to make Domino a core part of the Foundry Object Services so that Volt Iris apps can interact with Domino databases in the same way they can for relational databases. With Domino Adapter, you can connect to your Domino database as an endpoint via Domino REST API. Domino Adapter includes the following features: 

- Form-based CRUD (post, get, put, delete)
- Form-based PATCH 
- View-based GET (non-parameterized) 

## First Touch

The First Touch app installs and presents users with sample applications (“Recipes”) in Iris to show how to use Domino Adapter, connect Volt Foundry to the Domino back end, and leverage Domino Adapter and Domino REST APIs. The First Touch app promotes a good user experience when establishing connections and importing sample apps into Volt Foundry by:

- gathering necessary data from the admin to connect to the Domino REST API server
- authenticating using the credentials, creating schema and scope, creating view and app, and initializing inside Domino REST API
- preparing a zip file for import into Volt Foundry and importing the app
- displaying a message informing the user that everything is ready

The sample applications have features such as:

- displaying recipe cards that are clickable to show list of ingredients and instructions
- performing CRUD operations on Domino back end to create, edit, delete a recipe 


## Domino REST API

HCL Domino REST API provides a secure REST API with access to HCL Domino servers and databases while running on HCL Domino and HCL Notes on Windows, Linux, and Mac. Designed to re-establish Domino as a world class, modern, standards-compliant, cloud native and enterprise-level collaboration platform, it adds contemporary REST APIs to Notes and Domino, enabling a modern programming experience with the tools of your choice. 

For more information, see [HCL Domino REST API Documentation](https://opensource.hcltechsw.com/Domino-rest-api/index.html).


The HTML specification is maintained by the W3C.
	
--8<-- "samplesnippet.md"

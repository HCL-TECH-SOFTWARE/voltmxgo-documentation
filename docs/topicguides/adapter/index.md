# Domino Adapter

The Domino Adapter makes Domino a core part of the Volt MX Go Foundry Object services so that Volt MX apps can interact with Domino databases in the same way they can for relational databases.

## Authorization

The Domino Adapter interacts with Domino for both configuration and run-time activities by leveraging the Domino REST API, which requires an authorization token. The Domino Adapter relies directly on the Identity service of Volt MX Go Foundry and indirectly on the OAuth REST API of Domino REST API to obtain valid authorization tokens for configuration and runtime. 

## Object Services

Domino Adapter supports Object services that enables model-driven app design and development by following a micro-services architectural approach to create reusable components and link them to fit into your solution. By using Object services, you can define your preferred data model, which defines how your app wants to interact with its data.

When creating an Object service in Volt MX Go Foundry for Domino, the Volt MX Go Foundry administrator associates the Object service to a single Domino REST API server URL. The Volt MX Go Foundry administrator can associate more than one Object service with the same Domino REST API server URL if desired. Domino object models are generated in the Object Service from the scopes defined in Domino REST API.

The `object` of the Object service essentially has two components:

- [Data Model](datamodel.md) refers to the definition of the fields that comprise the object definition.

- [Methods](method.md) refers verbs for interacting with the data, for example GET, POST.

For more information, see [Object Services](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_user_guide/Content/Objectservices.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../assets/images/external-link.svg){: style="height:13px;width:13px"} in the HCL Volt MX documentation.

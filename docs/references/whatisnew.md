# What's new

The section provides information on the latest features, improvements, and resolved issues related to Volt MX Go.


## Volt MX Go v2.0.1

### New features
*VoltScript* is a [BASIC](https://en.wikipedia.org/wiki/BASIC){: target="_blank"} scripting language for use with HCL Volt MX Go as a server-side scripting language running within the Foundry middleware layer. *VoltScript* includes:

- Visual Studio Code extension for allowing developers to write code in VS Code
- Linux Docker image for allowing Mac developers to use the VS Code extension
- Language enhancements for improving consistency and ease of use
- Open-source helpers, such as a library with advanced collection and map collections, a unit testing framework, and a serializer and deserializer for JSON-based object persistence
- A toolkit for scaffolding the various VoltScript extensions and script code and autogenerating starter code and related documentation
- Various VoltScript Extensions for supporting various processes, such as data access over HTTP to specific or generic REST services, handling JSON data, interacting with the operating system and files, managing input parameters

To learn more about the **early access version** of VoltScript and related components, see [HCL VoltScript Documentation](https://help.hcltechsw.com/docs/voltscript/early-access/index.html){: target="_blank"}.  

### Improvements


### Resolved issues

##### Domino Adapter
- Using special characters as part of the search parameter for the `$filter` in the `GET` method returned errors as the regex that decoded special characters didn't decode all hex characters. An example is the `=` sign in the search parameter value `col1 eq "B=S"`. Performing a GET method with `$filter=col1 eq "B=S"` would return an error, while performing the GET method with `$filter=col1 eq Bx_003dS` would work.    
- The `$FILES` field wasn't usable for the `$filter` query parameter to find documents with a specified attachment, for example, `$filter=x_0024FILES eq attName.txt`. 
- An incorrect access token was used for an operation when multiple users performed operations simultaneously while using a shared connection instance to a Domino REST API server.  
- Iris threw an exception on a `GET` operation on view data models when the maximum depth of the view hierarchy is more than two hierarchy levels. An example of a view hierarchy with more than two hierarchy levels is a document with a response and a response to that response. 

### Others

- Added troubleshooting entry related to kubectl commands failing.
- Added known limitation related to using helm charts on supported Kubernetes platform. 
##### Domino Adapter
- Added procedure for [generating CRUD forms for an Object Service](../howto/codegen.md).
- Added known limitation related to deleting offline documents. 


## Volt MX Go v2.0

HCL Volt MX Go v2.0 allows you to extend the value of your Domino applications using the industry-leading, multi-experience platform Volt MX. The innovative features of Volt MX Go include:

- *VoltFormula* for expanding who can code applications built in Domino and allowing app modernization without a complete code rewrite 
- *Design Import* for importing existing Domino views, forms, and fields into Volt Foundry, giving you a head start on modernizing or creating new multi-experience applications in Volt Iris that are connected to your Domino back-end data and applications
- *Domino Adapter* and *Domino REST API* for connecting Volt Foundry to your Domino applications
- *First Touch* for guiding users in establishing connections and importing sample apps into Volt Foundry

???note "Early access version changes"
    For the updates and changes in the early access version, see [Early Access Version changes](earlyaccesschanges.md).

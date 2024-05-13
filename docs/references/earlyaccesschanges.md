# Early Access version changes

The section provides information on the features, improvements, and resolved issues related to the early access version of Volt MX Go.

## Early Access v3

### New Features

- Added Summernote Editor component in Volt MX Go Iris to allow users to enter or edit rich text content in  **Create** and **Update** forms generated from Domino objects. For more information, see *Import Summernote Editor*<!--(../howto/summernote.md)--> and *Summernote Editor widget*<!--(summernotewidget.md)-->.
- Added readiness and liveness probes support to the Domino REST API Helm chart. The readiness probe is used by a service to know if a container is available to handle requests. If it fails the configured thresholds, the service is marked as not ready and won't route requests. The liveness probe is similar to the readiness probe. However, if it fails the configured thresholds, the container is killed and restarted. These probes are present and customizable.
- Added installers for **Domino REST API** and **Volt MX Go Foundry**.

##### VoltFormula
- Added Typeahead IntelliSense in the [configuration](../howto/configrosetta.md) which can be seen in the rosetta formula. 

##### Design Import
- Added support for multi-value fields configured in Domino Rest API with the value returned to the imported Domino App as a bulleted list.
- Added **Collapse All** and **Expand All** features in **VoltMX Design Import Wizard**.
- Added unconfigured and configured forms in **VoltMX Design Import Wizard**.

### Improvements

##### First Touch
- Users can now view and explore the First Touch Recipe Catalog app by launching it from Volt MX Go Foundry. 

##### Domino Adapter
- Updated the Rich Text field format in Volt MX Go Foundry Object Services to Base64-encoded HTML
- Added support for the PATCH method for form-based data models.
- Support OData filter parameter for the GET method on form-based data models to return a document’s unknown form name using the document's UNID. For more information, see [Supported OData filter parameters, form-based GET](../topicguides/method.md#supported-odata-query-parameters-for-form-based-get-method).
- Enhanced object service code generation in Volt MX Go Iris for Domino objects so that when using the **Generate Forms** function: 

    - The GRID and DETAILS forms show rich text via the Rich Text widget.
    - The CREATE form allows users to specify the rich text field content using the Summernote Editor Iris component.
    - The UPDATE form allows users to edit the rich text using the Summernote Editor Iris component.  

##### VoltFormula
- IntelliSense improvements on category beside each formula.
- Update the Rosetta API and Rosetta converter which can be seen in [Rosetta API reference documentation](https://help.hcltechsw.com/docs/voltmxgo/javadoc/index.html).
##### Design Import
- Improvements on the error toggle button on the **VoltMX Design Import Wizard**.
- Improve the sort configuration in importing the forms generated.
- Updated the warning message for supported **Project** type.
- Improve the integration services operations in Volt MX Go Foundry app.

### Resolve Issues

##### Design Import
- An error occurred when choosing a new scope in the Scope and Form step in the **VoltMX Design Import Wizard**.
- The list of scopes wasn't fetched again when the service was changed.

### Others
- Changed instances of *Keep* to *REST API* in steps and commands in the installation procedures.
- Updated [Install Domino REST API](../tutorials/downloadhelmchart.md#install-domino-rest-api) procedure by including a step for adding DNS name settings.
- Added [installation procedures](../tutorials/nativeinstallers.md) for installing Domino REST API and Volt MX Go Foundry using installers.
- Updated system requirements for installing [Volt MX Go Foundry](../tutorials/sysreq.md#for-installing-volt-mx-go-foundry) and [Domino REST API](../tutorials/sysreq.md#for-installing-domino-rest-api) using installers.  


## Early Access v2

### New Features

##### Design Import
- Added user-selectable [logging levels](reflogginglevels.md) for better monitoring and evaluation of activities and events.

### Improvements

##### First Touch
- Simplified [uninstall procedure](../howto/uninstallfirsttouch.md) and improved progress view for both install and uninstall for better user experience.

##### Domino Adapter
- Supports [OData filter parameters for the GET method on view-based data models](../topicguides/method.md#supported-odata-query-parameters-for-view-based-get-method).
- Added Domino form alias names to `@form` attribute metadata in form-based data models.

##### Design Import
- Implemented UI improvements on the **VoltMX Design Import Wizard** for better user experience.

##### VoltFormula
- Updated the list of Notes and Open formulas in [Rosetta API reference documentation](https://help.hcltechsw.com/docs/voltmxgo/javadoc/index.html).


### Others
- Updated the installation procedures to update Volt MX Go to the latest version.

## Early Access v1

- First release of the early access version of Volt MX Go.
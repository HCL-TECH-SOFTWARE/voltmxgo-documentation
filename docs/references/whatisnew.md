# What's new

The section provides information on the latest features, improvements, and resolved issues related to Volt MX Go.

## Early Access v3

### New Features

- Added Summernote Editor component in Iris to allow users to enter or edit rich text content in  **Create** and **Update** forms generated from Domino objects.
- Added readiness and liveness probes support to the Domino REST API Helm chart. The readiness probe is used by a service to know if a container is available to handle requests. If it fails the configured thresholds, the service is marked as not ready and won't route requests. The liveness probe is similar to the readiness probe. However, if it fails the configured thresholds, the container is killed and restarted. These probes are present and customizable.

#### VoltFormula
- Added Typeahead IntelliSence in the configuration which can be seen in the rosetta formula which can be seen in [Configuration of Rosetta API setting](../howto/configrosetta.md)

### Improvements

##### First Touch
- Users can now view and explore the First Touch Recipe Catalog app by launching it from Foundry. <!--To learn more about the app, see [First Touch app](../topicguides/firsttouchapp.md).-->

##### Domino Adapter
- Updated the Rich Text field format in Foundry Object Services to Base64-encoded HTML
- Added support for the PATCH method for form-based data models.
- Support OData filter parameter for the GET method on form-based data models to return a document’s unknown form name using the document's UNID. For more information, see [Supported OData filter parameters, form-based GET](../topicguides/dominoadapter.md#supported-odata-filter-parameters-form-based-get).
- Enhanced object service code generation in Iris for Domino objects so that when using the **Generate Forms** function: 

    - The GRID and DETAILS forms show rich text via the Rich Text widget.
    - The CREATE form allows users to specify the rich text field content using the Summernote Editor Iris component.
    - The UPDATE form allows users to edit the rich text using the Summernote Editor Iris component.  

<!-- Added support for *GET document with an unknown form* OData filter parameter for the GET method on form-based data models.-->

##### VoltFormula
- IntelliSense improvements on category beside each formula.
- Update the usage of Rosetta API and Rosetta converter which can be seen in Rosetta API reference documentation.
### Others
- Changed instances of *Keep* to *REST API* in steps and commands in the installation procedures.
- Updated [Install Domino REST API](../tutorials/downloadhelmchart.md#install-domino-rest-api) procedure by including a step for adding DNS name settings.



## Early Access v2

### New Features

##### Design Import
- Added user-selectable [logging levels](reflogginglevels.md) for better monitoring and evaluation of activities and events.

### Improvements

##### First Touch
- Simplified [uninstall procedure](../howto/uninstallfirsttouch.md) and improved progress view for both install and uninstall for better user experience.

##### Domino Adapter
- Supports [OData filter parameters for the GET method on view-based data models](../topicguides/dominoadapter.md#supported-odata-filter-parameters-view-based-get).
- Added Domino form alias names to `@form` attribute metadata in form-based data models.

##### Design Import
- Implemented UI improvements on the **VoltMX Design Import Wizard** for better user experience.

##### VoltFormula
- Updated the list of Notes and Open formulas in [Rosetta API reference documentation](https://help.hcltechsw.com/docs/voltmxgo/javadoc/index.html).


### Others
- Updated the installation procedures to update Volt MX Go to the latest version.

## Early Access v1

- First release of the early access version of Volt MX Go.
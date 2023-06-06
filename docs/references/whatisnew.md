# What's new

The section provides information on the latest features, improvements, and resolved issues related to Volt MX Go. 

## Early Access v3

### New Features
- Added Summernote Editor component in Iris to allow users to enter or edit rich text content in  **Create** and **Update** forms generated from Domino objects.  

### Improvements

##### First Touch
- Users can now view and explore the First Touch Recipe Catalog app by launching it from Foundry. To learn more about the app, see [First Touch app](../topicguides/firsttouchapp.md).

##### Domino Adapter
- Updated the Rich Text field format in Foundry Object Services to Base64-encoded HTML
- Added support for the PATCH method for form-based data models.
- Added support for *GET document with an unknown form* OData filter parameter for the GET method on form-based data models.
- Enhanced object service code generation in Iris for Domino objects so that when using the **Generate Forms** function: 

    - The GRID and DETAILS forms show rich text via the Rich Text widget.
    - The CREATE form allows users to specify the rich text field content using the Summernote Editor Iris component.
    - The UPDATE form allows users to edit the rich text using the Summernote Editor Iris component.  


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
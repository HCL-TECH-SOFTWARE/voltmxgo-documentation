# Methods (Verbs)

## Overview

Methods for interacting with the data models are generated when generating the data models. 

For view-based data model and Other Metadata based data model, only the GET method is generated.

For form-based data models, a number of methods including standard CRUD operations and binary CRUD are generated and supported: 

- POST : *Create* a new Domino document containing the specified fields.
- GET : *Read* existing Domino documents, returning zero or more documents.
- PUT : *Update* an existing document, replacing all specified fields. If a field is omitted from the payload, it's removed from the document in Domino.
- DELETE : *Delete* the specified document.
- PATCH : *Update* an existing document, replacing only the specified fields. If a field is omitted from the payload, the field value in the Domino document isn't modified.
- BULK UPDATE: *Update* an existing collection of documents, replacing only the specified fields in those documents. If a field is omitted from the payload, the field value in the collection of Domino documents isn’t modified.

    !!!warning "Important"
        You must use the `$filter` ODATA query parameter to tell Domino REST API which documents to update. Otherwise, an error occurs.

- createBinary - `Create` a new attachment file to attach to a specified Domino document.
- getBinary - `Read` an existing attachment from a specified Domino document. 
- updateBinary - `Update` an existing attachment from a specified Domino document, replacing it with a new one. 
- deleteBinary - `Delete` an existing attachment from a specified Domino document.
<!--- Batch - `Update` of 1 or more documents matching a specified criteria, for example, all documents of type `employee`.
-->

!!!tip 
    The binary verbs, `createBinary`, `getBinary`, `updateBinary`, `deleteBinary`, are generated only when the Domino REST API administrator includes the **$FILES** virtual field in the form mode. 

Data models in Volt MX Go Foundry are associated with specific Domino forms, so each operation (GET, Update, etc.) only applies to the form associated with the data model. 

## Supported OData query parameters for form-based GET method

!!!note
    The results of the GET method are influenced by the OData query parameters, if specified, and by the document's *form attribute* values.

    - If there are no defined form name aliases in the Domino design for the form, the method returns only documents with the form attribute equal to the form name.
    - If there are defined form name aliases in the Domino design for the form, the method returns only the documents that have the form value set equal to the last alias in Domino.  
    <!-- If there are defined form name aliases in Domino design for the form, the method returns only documents with the form attribute equal to the last name alias.-->  

The Domino Adapter supports these OData query parameters for the GET method on form-based data models:

- `$select`: List of fields to include in the returned documents.
- `$filter`: Specifies field conditions that must be met by a document for it to be in the returned document set.
- `$filter (unknown Form)`: Specifies the UNID of the document to return without knowing the document's form name.
- `$top`: Specifies the number of documents to return, starting from the beginning or from the row specified by `$skip`.
- `$skip`: Specifies the number of documents to skip (zero-based row index of the first returned document).

!!!note
    - `$top` and `$skip` are used together for pagination, for example to define how many entries to skip or how many entries to return from the skip point onward.
    - **When using a special character as part of the search parameter for the `$filter`**, you must encode the special character using `x_00` concatenated with its corresponding hex code. For example, when filtering a `Name` field whose value is `CN=admin/O=ocp`, you must encode the special characters `=` and `/`. So the filter should be `$filter=Name eq CNx_003dadminx_002fOx_003docp`, where we encoded `=` as `x_003d` and `/` as `x_002f`. 

With `$filter`, the following canonical functions are supported:

- `substringof`
- `endswith`
- `startswith`

**Examples**
    
|Example query|Expected result|
|----|----|
|`$filter=Type eq 'Dessert'`|Returns all documents whose `Type` field is equal to `Dessert`.|
|`$filter=Name eq CNx_003dadmin`|Returns all documents whose `Name` field is equal to `CN=admin`.|
|`$top=2`|Returns the first two documents.|
|`$skip=3`|Returns documents starting from the fourth document onwards.|
|`$select=Name&$filter=substringof(Name,'Hot') eq true`|Returns documents with `Hot` included in the `Name` field, only returning the `Name` field.|
|`$select=Name,Ingredients`|Returns documents that include only the `Name` and `Ingredients` fields.|
|`$filter=x_0040unid eq xxxx and Form eq unknown`|Returns only the form name and form alias names for the document specified by UNID xxxx.|
|`$select=Name,mydate,x_0040created&$filter=mydate ge '2022-03-10T05:00:00Z'`|Returns documents that include only the `Name` field, `mydate` field, and `x_0040created` columns, with `mydate` values on or after 2022-03-10T05:00:00Z.|

## Supported OData query parameters for view-based GET method 

The Domino Adapter supports these OData query parameters for the GET method on view-based data models:

- `$skip`: Specifies the number of view entries to skip (zero-based row index of the first returned view entry).
- `$top`: Specifies the number of view entries to return, starting from the beginning or from the row specified by `$skip`.
- `$orderby`: Sort the result-set in ascending or descending order based on a specified column. **The column must be specified as `sortable` in the database design**. 
- `$filter`: Specifies conditions that must be met by a view entry for it to be returned in the set of matching view entries. **Only `sortable` columns can be filtered**.

!!!note
    - For view-based data models, the *view selection formula* determines which documents will be returned. Additionally, the returning documents may be further filtered by the OData parameter settings.
    - You can use formulas to create new sortable columns in Domino Designer. As an example, you can use the formula `@Text(@Universalid)` to create a new sortable column in Domino Designer so that `$filter` and `$orderby` can be used to find a view row by UNID or to order the view by UNID.
    - `$top` and `$skip` are used together for pagination, for example to define how many entries to skip or how  many entries to return from the skip point onward.
    - **When using a special character as part of the search parameter for the `$filter`**, you must encode the special character using `x_00` concatenated with its corresponding hex code. For example, when filtering a `Name` field whose value is `CN=admin/O=ocp`, you must encode the special characters `=` and `/`. So the filter should be `$filter=Name eq CNx_003dadminx_002fOx_003docp`, where we encoded `=` as `x_003d` and `/` as `x_002f`.

With `$filter`, the following canonical functions are supported:

- `startswith`
- `documentsOnly`
- `distinctDocuments`

**Examples**

|Example query|Expected result|
|----|----|
|`$top=10`|Returns 10 rows of data unless the total number of data rows in the view database is less than 10.|
|`$skip=0`|Returns rows starting from the first view entry in the view (skip zero rows), equivalent to omitting `$skip`.|
|`$skip=5`|Returns data starting from the sixth view entry in the view.|
|`$filter=Year eq 2021`|Returns all view entries in the view whose `Year` field is equal to `2021`.|
|`$filter=Name eq CNx_003dadmin`|Returns all view entries in the view whose `Name` field is equal to `CN=admin`|
|`$filter=startswith(Model,'HR') eq true`|The result-set only has data that starts with "HR" in column `Model`.|
|`$filter=documentsOnly eq true`|Returns view documents instead of view entries in a view.|
|`$filter=distinctDocuments eq true`|Returns only distinct view documents in a view.|
|`$orderby=Year` or `$orderby=Year asc`|Returned rows are ordered by ascending values in the `Year` column.`asc` is the default if direction is omitted.|
|`$orderby=Year desc`|Returned rows are ordered by descending values in the `Year` column.|

## Attachments

Domino documents can have associated attachments, which are accessible to Volt MX Go through the binary API.

You may perform the following binary operations:

 - getBinary: `GET <objSvc>/operations/<data model>/getBinary?unid=<document unid>&name=<file name>&type=<input type>`
     - Downloads file content in Base64 format by default. The `type` parameter is optional. You can provide `type` as an input with value `bytes` or `file`. If you specify `bytes`, the response is in a stream format. If you specify `file`, the response is in a downloadable format.
     
        !!!tip
            To download files larger than 50 MB, use a type argument, such as `bytes`, to avoid memory issues with the default Base64 format. This enables downloading of files up to 1 GB.
         
 - createBinary: `POST <objSvc>/operations/<data model>/createBinary?unid=<document unid>&name=<file name>&field=<field name>`
     - Takes the file’s binary content encoded as a Base64 string or in the multipart/form-data format
     - The `field` parameter is optional. If this parameter is provided, it attaches the file to a valid rich text field within the Domino document. If this parameter isn't provided, the file is attached to the Domino document as a whole.

        !!!tip
            To upload large files, upload them to the createBinary API with a Content-Type of multipart/form-data. Pass the UNID and document name as arguments to the API together with a form, having the key `data`, which contains the file content to be uploaded. This enables uploading of files up to 1 GB.

- updateBinary: `PUT <objSvc>/operations/<data model>/updateBinary?unid=<document unid>&name=<file name>&field=<field name>`
    - Takes the file’s binary content encoded as a Base64 string. The old file is deleted and replaced with the new Base64 encoded file content.
    - The `field` parameter is optional. If the attachment you wish to update is associated with a field in the Domino database, include the field in the update request to remove the attachment.

        !!!tip
            To upload large files, upload them to the updateBinary API with a Content-Type of multipart/form-data. Pass the UNID and document name as arguments to the API together with a form, having the key `data`, which contains the file content to be uploaded. This enabled uploading of files up to 1 GB.

- deleteBinary: `DELETE <objSvc>/binary/<data model>?unid=<document unid>&name=<file name>&field=<field name>`
    - The file is deleted from the Domino database and its name is removed from the `$FILES` field.
    - The field parameter is optional. If the attachment you wish to delete is associated with a field in the Domino database, include the field in the delete request to remove the attachment.

!!!warning "Important"
    - Large attachment files may cause some performance issues, so limit the attachment size to the minimum possible size. If you have large-sized attachments, increase your Volt MX Go Foundry configured memory resource by [configuring heap size](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_manual_install_guide/Content/Configuring_Connectors_and_Batch_Files_-_Tomcat.html#configuring-heap-and-permgen-size-for-tomcat "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../assets/images/external-link.svg){: style="height:13px;width:13px"} or updating `integration.resourceMemoryLimit` in `values.yaml` for Volt MX Go Foundry on supported Kubernetes platform.
    
    - By default, there is also a limit in the Domino Rest API on how big an attachment it can support. To learn how to change the size limit, see [Change file size limit](https://opensource.hcltechsw.com/Domino-rest-api/howto/production/changefilesize.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../assets/images/external-link.svg){: style="height:13px;width:13px"} in the Domino REST API documentation.   
 
## Using PATCH verb from Volt MX SDK

The Volt MX SDK has CRUD functions allowing an end-user application to use the REST API to interact with the Domino data in the back end. If you want to use the PATCH verb, you need to use the `customVerb` function from the Volt MX SDK. For more information, see [customVerb method](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_user_guide/Content/ObjectsAPIReference/OnlineObjectService_Class.html#customverb-method "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../assets/images/external-link.svg){: style="height:13px;width:13px"} in the HCL Volt MX Documentation.

???example "Refer to the code example for using the SDK's `customVerb` function."   

    ```
    onPatchDocument: function() {
    var objSvc = voltmx.sdk.getCurrentInstance().getObjectService("myObj", {
        "access": "online"
        });
        var dataObject = new voltmx.sdk.dto.DataObject("dataObj");
        dataObject.addField("x_0040unid", "unid");
        dataObject.addField("field", "value");
        var options = {
        "dataObject": dataObject
        };
        objSvc.customVerb("partialupdate", options,
        function(response) {
        voltmx.print("Partial update succeeded: " + JSON.stringify(response));
        },
        function(error) {
            voltmx.print("Partial update failed:" + JSON.stringify(error));
        });
        } 
    ```

## Using binary APIs from Volt MX SDK

 Using the binary APIs with Domino Adapter requires more properties in the functional call. You need to add an object with a `queryParams` key to the options argument of the `createBinaryContent`. The object should contain query parameters required for using the binary APIs with Domino Adapter, including `unid` and `name` parameters. 

!!!note
    - For more information, see the general use of the [binary APIs from the Volt MX SDK](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/voltmx_foundry_user_guide/Content/ObjectsAPIReference/OnlineObjectService_Class.html#getbinarycontent-method "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../assets/images/external-link.svg){: style="height:13px;width:13px"} in the HCL Volt MX documentation.
    
    - There is no function in the Volt MX SDK for calling `deleteBinary`.

???example "Refer to the code examples for using the SDK's binary functions."

    ```text
    onCreateBinary: function() {
        var objSvc = voltmx.sdk.getCurrentInstance().getObjectService("myObj", {
        "access": "online"
        });
        var dataObject = new voltmx.sdk.dto.DataObject("dataObj");
        var binaryText = "SGVsbG8gd29ybGQh";
        dataObject.addField("data", binaryText);
        dataObject.addField("x_0040unid", "123");
        objSvc.createBinaryContent({
        "dataObject": dataObject,
        "queryParams": {
            "unid": "123",
            "name": "helloworld.txt",
            "field": "Body"
        },
        "binaryAttrName": "data"
        },
        function(response) {
            voltmx.print("Binary content created: " + JSON.stringify(response));
        },
        function(error) {
            voltmx.print("Failed: " + JSON.stringify(error));
        });
    },
    onUpdateBinary: function() {
        var objSvc = voltmx.sdk.getCurrentInstance().getObjectService("myObj", {
        "access": "online"
        });
        var dataObject = new voltmx.sdk.dto.DataObject("dataObj");
        var binaryText = "VXBkYXRlZCBIZWxsbyBXb3JsZCE=";
        dataObject.addField("data", binaryText);
        dataObject.addField("x_0040unid", "123");
        objSvc.updateBinaryContent({
        "dataObject": dataObject,
        "queryParams": {
            "unid": "123",
            "name": "helloworld.txt",
            "field": "Body"
        },
        "binaryAttrName": "data"
        },
        function(response) {
            voltmx.print("Binary content created: " + JSON.stringify(response));
        },
        function(error) {
            voltmx.print("Failed: " + JSON.stringify(error));
        });
    },
    onGetBinary: function() {
        var objSvc = voltmx.sdk.getCurrentInstance().getObjectService("myObj", {
        "access": "online"
        });
        var dataObject = new voltmx.sdk.dto.DataObject("dataObj");
        dataObject.addField("x_0040unid", "123");
        objSvc.getBinaryContent({
        "dataObject": dataObject,
        "queryParams": {
            "unid": "123",
            "name": "helloworld.txt"
        },
        "binaryAttrName": "data"
        },
        function(response) {
            voltmx.print("Binary content: " + JSON.stringify(response));
        },
        function(error) {
            voltmx.print("Failed: " + JSON.stringify(error));
        });
    },

    onDeleteBinary: function() {
        var objSvc = voltmx.sdk.getCurrentInstance().getObjectService("myObj", {
        "access": "online"
        });
        var dataObject = new voltmx.sdk.dto.DataObject("dataObj");
        dataObject.addField("x_0040unid", "123");
        objSvc.deleteBinaryContent({
        "dataObject": dataObject,
        "queryParams": {
            "unid": "123",
            "name": "helloworld.txt",
            "field": "Body"
        },
        "binaryAttrName": "data"
        },
        function(response) {
            voltmx.print("Binary deleted: " + JSON.stringify(response));
        },
        function(error) {
            voltmx.print("Failed: " + JSON.stringify(error));
        });
    }
    ```
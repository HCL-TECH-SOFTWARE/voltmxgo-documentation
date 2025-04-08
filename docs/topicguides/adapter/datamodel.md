# Data models

## Overview

Data models can be generated in an Object Service by Volt MX Go Foundry administrators. For Domino object services, a data model can be generated for any `Form` or `View` associated with a `scope` defined by a Domino REST API administrator. Additionally, Volt MX Go Foundry data models can be generated for `Other Metadata` to provide specific information outside the data contained in the form and view Domino documents.

!!! note

    `Forms` and `views` are created in a Domino REST API `schema` and named by a Domino REST API `scope`.

In addition to some [Meta fields](#meta-fields), generated data models include:

- **Form** data models include all fields defined by the associated Domino REST API `schema`.
- **View** data models include all view columns defined in the NSF design.

- [Other Metadata](#other-metadata) data models include fields that pertain to the requested information.

Volt MX Go Foundry data models are in sync with the Domino REST API `schema` at the time of data model generation. The data models may be out of sync with the `schema`, which may lead to undesired or unexpected results, because of the following:

- data models are edited in Volt MX Go Foundry
- schema is modified in Domino REST API
- changes in the NSF design

For more information on schemas, scopes, forms, and views, see [Using Admin UI](https://opensource.hcltechsw.com/Domino-rest-api/tutorial/adminui.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../assets/images/external-link.svg){: style="height:13px;width:13px"} in the Domino REST API documentation.  

## Data model artifact names

Volt MX Go Foundry data model names, such as field names, are similar but not identical to the names found in Domino REST API. The data model object names must meet all the following conditions:

- contain only alpha-numeric characters or `_` 
- begin with a letter
- be between 1 and 50 characters long 

If the Domino data form or view name doesn't meet these conditions, a user must change the data model name in Volt MX Go Foundry when going through the generation flow.

Volt MX Go Foundry data models are generated based on related artifacts in Domino REST API. For example, data model `fields` are based on `fields` found in Domino REST API for a given scope/schema. The generated Volt MX Go Foundry data model artifacts, such as form names, view names, and field names, are derived from and similar to the corresponding Domino REST API artifact. However, "special characters" in any of those names are encoded. For example, the `@unid` (meta) field becomes `x_0040unid`.

## Effective data types

Field data types in the generated Volt MX Go Foundry data model are the same as the data type defined in the Domino REST API schema. Some field (column) data types are common between Domino and Volt MX Go Foundry, for example string, numbers, and dates. Others, such as Domino `multivalue` (technically, these are `arrays`) and `rich text` aren't found in Volt MX Go Foundry.

For common data types, the field type in the generated Volt MX Go Foundry object models will match the data type in the Domino REST API schema. In the example image, the number of *Servings* is a `float` in the Domino REST API `schema`.

![Domino REST API schema](../../assets/images/recipe-servings-keepschema.png)

In the Volt MX Go Foundry object model, the field type of *Servings* is `number`:

![Volt MX Go Foundry object model](../../assets/images/recipe-servings-foundrymodel.png)

For Domino object types not found in Volt MX Go Foundry, the Volt MX Go Foundry object field type is set to `string` and Domino type information is retained as properties in the field metadata attribute. 

Two properties are used for Domino data type information:

- `dominoSpecialType` property indicates if the data is `Rich Text`, `Array` (multi-value), or `Date Only`. 
- `dominoArrayComponentType` property indicates the array type for multi-value fields, for example, a multi-value array of strings as shown in the following example:

![Metadata dialog](../../assets/images/recipe-richtext.png)

The table shows a simplified list of data-type mappings between Domino REST API and Volt MX Go Foundry:

!!!note
    Examples in the table are from the Volt MX Go Foundry Object Service perspective.

|Domino REST API format|Volt MX Go Foundry type|Additional details|
|---|---|---|
|DATE-TIME|date|Example: `2023-05-09T19:39:47Z`|
|DATE|date|Example: `2023-05-09`<br/><br/>For more information, see [Data model metadata attribute](#data-model-metadata-attribute).|
|BYTE, DOUBLE, FLOAT, INT32, INT64|number|Example: `7`|
|BOOLEAN|boolean|Example: `true`|
|BINARY|string||
|AUTHORS, NAMES, PASSWORD, READERS|string||
|RICH TEXT|string|Field values are in Base64-encoded HTML format.<br/><br/>For more information, see [Data model metadata attribute](#data-model-metadata-attribute).|
|ARRAY|string|Field values are "stringified JSON Array"<br/> Example: `"[\"flour\",\"eggs\"]"`<br/><br/>Other data types may also be marked as multi-value, in which case the JSON array contains values of the corresponding type. Examples:<br/>String array: `"[\"flour\",\"eggs\"]"`<br/>Number array: `"[1,2]"`<br/>Author array: `"[\"CN=mxgo admin/O=ocp\",\"[Admin]\"]"]"`<br/><br/>For more information, see [Data model metadata attribute](#data-model-metadata-attribute).|
|all others|string|

## Meta fields

In addition to the document fields specified in the database design such as `form` or `view`, Domino `meta-fields` are in the list of Volt MX Go Foundry data model fields generated for Domino. As a result, when you `GET` Domino documents from the object service, values for these `meta-fields` are also returned for each document.

For form-based data models, the document's `@unid` is an obvious example. Below are other `meta-fields` you may see for each document:

```{ .yaml .no-copy }
x_0040addedtofile
x_0040aliases
x_0040attachments
x_0040created
x_0040editable
x_0040lastaccessed
x_0040lastmodified
x_0040lastmodifiedinfile
x_0040noteclass
x_0040noteid
x_0040parentunid
x_0040revision
x_0040size
x_0040unid
x_0040unread
x_0040warnings
```

For view-based data models, the following `meta-fields` are returned:

```{ .yaml .no-copy }
x_0040etag
x_0040form
x_0040index
x_0040noteid
x_0040scope
x_0040totalCount
x_0040unid
```

!!! note

    - **All `meta-fields` aren't sortable**. 
    
    - UNID is unique for any set of documents returned on `GET` for a form-based data model. However, UNID isn't necessarily unique for view rows since more than one row in a view may be associated with the same database document.

    - Meta-fields are included in generated data models by default. The Volt MX Go Foundry developer can modify the generated data model as needed, such as removing `meta-field` if desired.

    - `x_0040aliases` doesn't correspond to any attribute in Domino. Documents won't contain any value for this attribute. However, it's for attaching metadata with form name aliases. For more information, see [Data model metadata attribute](#data-model-metadata-attribute).
    
    - Offline objects require a data model to specify a primary key field. `x_0040unid` needs to be set as the primary key for Domino data models. However, with views, the returning list of data may contain items with no UNID or items with the same UNID.<br/><br/>Items with no UNID occur when querying categorized views. These items with no UNID are top-level category items. To avoid receiving these items, a user must scope the view request to return only the document items using the OData filter parameter `<GET view URL>?$filter=x_0040scope eq documents`.<br/><br/>For items with the same UNID, errors may occur when syncing data to the front end.

    - `x_0040totalCount` provides the maximum number of documents in a view, including those documents that might have certain access restrictions. This means that the number of returned documents on `GET` for a view-based data model might be less than the value provided by the `x_0040totalCount` since you might not have access to some of those documents.

        The value of `x_0040totalCount` might not also match the number of returned documents on `GET` for a view-based data model when the view is designed to have a column that shows each value of a multivalue field as a separate document.  

## Data model metadata attribute

The **Metadata** attribute of a Volt MX Go Foundry data model field retains extended Domino design information, which may be of interest to client applications using Volt MX Go Iris.

### Column characteristics

For View columns (only non-meta columns), the data model field **Metadata** attribute includes additional column properties:

|Column property|Description|
|:----|:----|
|position|Refers to column number.|
|sorted|Refers to whether the column is sortable|
|direction|Refers to sort direction, either ascending or descending.|
|resort-asc|Indicates that clicking the column header sorts the view in ascending order.|
|resort-desc|Indicates that clicking the column header sorts the view in descending order.<br/><br/>If both resort-asc and resort-desc are true, clicking the column header changes the sorting between ascending and descending orders.|
|title|Displays the title of the column.|
|multiValueSeparator|NONE indicates the column isn't an array of values (multi-valued). COMMA, SPACE, SEMICOLON, and NEWLINE indicate that the column has an array of values, and the type of separator character is indicated.|

### Form aliases

For the form fields, the form's alias names are itemized on the `x_0040aliases` meta field. One metadata property is added for each alias. For example, if a form in a database has three aliases, the **Metadata** properties look like the following:

![Metadata properties](../../assets/images/formaliasproperties.png)

### Extended data types

Rich text and multi-value (array) form fields are seen as string fields in the data model. For these fields, `dominoSpecialType` and `dominoArrayComponentType` properties are added to metadata.

|For...|dominoSpecialType|dominoArrayComponentType|
|:----|:----|:----|
|RICH TEXT|richtext|not used|
|MULTI-VALUE|array|the array type, such as string, number|
|DATE ONLY|date|not used|

## Other Metadata

There are cases where a user may request Domino information not included in Domino data documents but still necessary for creating a Domino application in Volt MX Go. This information is accessible from the Domino Adapter in the `Other Metadata` section.

To use this information, a Volt MX Go Foundry administrator must select which `Other Metadata` entities to create in the data model generation flow. This creates a Volt MX entity. A user can then perform a GET method on this Volt MX entity to obtain and use the information.

**Implemented `Other Metadata` entities**:

- UserInfo

    This endpoint gets information about a logged in Domino user. The user must be logged in and be able to be authenticated against Domino. The returned fields may include:

    ```{ .yaml .no-copy }
    email
    family_name
    given_name
    mailFile
    mailServer
    names
    preferred_username
    scope
    sub
    ```

- ServerInfo

    This endpoint gets information about the Domino and Domino REST API versions. The returned fields may include:

    ```{ .yaml .no-copy }
    dominoBuildNumber
    dominoFixpackNumber
    dominoHotfixNumber
    dominoMajorVersion 
    dominoMinorVersion
    dominoPlatform
    dominoPlatformBits
    dominoProductionBuild
    dominoQmrNumber
    dominoQmuNumber
    dominoVersion
    keepDescription
    keepImageBuild
    keepName
    keepVendor
    keepVersion
    ``` 

- AttachmentsInfo

    This endpoint gets information about all the attachments on a document. The return fields may include:

    ```{ .yaml .no-copy }
    created
    modified
    name
    size
    ```

    !!! note

        When performing the GET method for **AttachmentsInfo**, an error is thrown if you don't provide the UNID of the document.

        For more information on performing the GET method, see [Test the GET method by viewing a record](../../tutorials/adaptertutorial.md#test-the-get-method-by-viewing-a-record).
           
# Known limitations

## Using Open API Adapter

Volt MX Go doesn't support the use of the Open API Adapter in the Volt MX Go Foundry Integration Services to connect to Domino via Domino REST API. 

## Using helm charts on supported Kubernetes platform

When using helm charts on a supported Kubernetes platform, you must run the `kubectl config set-context --current --namespace=mxgo` command in your Ubuntu terminal session to set the current namespace context after restarting Windows or Rancher Desktop. If you don't run the command after restarting Windows or Rancher Desktop, your kubectl commands might fail.

## Naming 

- Volt MX Go Foundry only allows "letters" (A-Z and a-z) as the first characters in names. For example, `@unid` and `$files`, included in Domino field names, aren't supported. As a workaround, Domino Adapter encodes the problematic characters, for example `@unid` becomes `x_0040unid`.
- Volt MX Go Foundry restricts the length of names, such as field names, to be shorter than the name length supported in Domino.

## Data conversion   

As Domino REST API and Volt MX Go Foundry administrators can redefine field data types, it can cause data conversion issues as they can redefine a field in Domino differently. For example, a Domino REST API administrator can indicate a date field in Domino as a boolean, while a Volt MX Go Foundry administrator can indicate the same date field as a string. This causes conversion issues. As not all possible conversion points have been tested, **data conversion isn't yet supported**.

## Verb mapping

Verb mapping isn't supported for binary verbs in the Volt MX Go Foundry Console.

## Deleting offline documents 
### Hard delete

If a document is hard deleted in the Domino DB by another app, the devices using the offline sync DB won't know about this deletion, and any subsequent sync calls won't remove the document from the sync DB. This results in a stranded document on the device, but not in the back end.

To resolve stranded documents in an offline app, use the [`clearOfflineData`](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Foundry/offline_objectsapi_reference_guide/Content/Object_clearOfflineData.html) function provided by the Volt MX SDK in Volt MX Go Iris. The function clears out the device's sync DB at the level you choose (app level, object service level, object level) so that syncing the app with the back end fully syncs all data without sending any hard deleted documents and allows the device's sync DB to match up with what's in the back end.

### Soft delete

Offline-enabled apps use soft delete to remove deleted documents from a device's sync DB. Add the `IsDeleted` property to the Domino REST API schema to enable soft delete. The property will contain the value *deleted* when the document has been soft deleted and removed entirely from the device’s sync DB upon a sync with the DB.

Disabling document deletion on the Domino DB if using it with an offline-enabled app combined with an agent script on the Domino REST API, which periodically clears soft-deleted documents, enforces soft delete on the Domino DB. These keep the soft-deleted documents long enough for the user devices to sync before pruning the deleted documents and ensure that the Domino DB doesn't have too many soft-deleted documents. 

## Domino Adapter

- Supports only Volt MX Go Foundry Object services.
- Domino object services in Volt MX Go Foundry are only usable by authenticated app users. You must have a valid Domino REST API token for all Domino REST API calls. Customers requiring access to Domino object services as unauthenticated users may be able to implement a Foundry pre-processor to obtain valid Domino REST API tokens and inject Authorization headers in each request.
 
## VoltFormula

- Prompt `[LocalBrowse]` and `[ChooseDatabase]` for Volt MX Go Iris application don't have a filter setting for file type since only [registered file types](https://www.iana.org/assignments/media-types/media-types.xhtml) are allowed in *voltmx.io.FileSystem*. For more information about *voltmx.io.FileSystem*, see the [Volt MX documentation](https://opensource.hcltechsw.com/volt-mx-docs/95/docs/documentation/Iris/iris_api_dev_guide/content/voltmx.io.filesystem_functions.html).

- Date APIs for Notes implementations return JavaScript Date Objects, which differ from Notes Date Objects.



# What's new

The section provides information on the latest features, improvements, and resolved issues related to Volt MX Go.

## Early Access v3

### New Features

##### Domino REST API
Readiness and Liveness probes support has been added to the Domino REST API Helm chart. Readiness probes are used to determine if a service is available to handle requests. If it fails the configured thresholds, the service is marked as not ready and will not be routed requests. The liveness problem is similar, but when it fails the configured thresholds, the container is killed and restarted. These probes are present and may be customized.

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
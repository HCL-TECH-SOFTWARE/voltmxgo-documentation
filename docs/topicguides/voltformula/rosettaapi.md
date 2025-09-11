# Rosetta API configuration options

## Default

```java
{
  _notes: "notes",
  _openFormula: "openformula",
  _defaultAPI: "notes",
  storage: {
    _integration: "integration",
    _object: "object",
    _offline: "offline",
    _defaultServiceType: "object"
  },
  framework: {
    _voltmx: "vmx",
    _javascript: "js",
    _defaultFramework: "js"
  }
}
```
## Getters, setters, and checkers

!!!tip
    For more information about a specific API object, see the [Rosetta API reference documentation](../../javadoc/index.html "Link opens a new tab"){: target="_blank" rel="noopener noreferrer"}&nbsp;![link image](../../assets/images/external-link.svg){: style="height:13px;width:13px"}. 

### Implementation

- `<rosettajs>.API.getDefaultAPI()`
- `<rosettajs>.API.setDefaultAPIAsNotes()`
- `<rosettajs>.API.setDefaultAPIAsOpenFormula()`
- `<rosettajs>.API.isDefaultNotes()`
- `<rosettajs>.API.isDefaultOpenFormula()`

### Framework

- `<rosettajs>.API.getDefaultFramework()`
- `<rosettajs>.API.setDefaultFrameworkAsJS()`
- `<rosettajs>.API.setDefaultFrameworkAsVoltMX()`
- `<rosettajs>.API.isDefaultFrameworkJS()`
- `<rosettajs>.API.isDefaultFrameworkVoltMX()`

### Extending

- `<rosettajs>.API.registerAPI(apiRef, name, code, lang, cat)`
- `<rosettajs>.API.registerAPIs(apiRef, jsonAPIs)`

### Intellisense files

- `<rosettajs>.API.getTernFileNames()`

## Additional information

For more information, see [Configure VoltFormula](../../howto/voltformula/configrosetta.md).

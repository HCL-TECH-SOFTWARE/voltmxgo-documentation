# Runtime Configuration options

## Rosetta API

### defaults:

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
### Getters, Setters, and Checkers

#### Implementation

- `<rosettajs>.API.getDefaultAPI()`
- `<rosettajs>.API.setDefaultAPIAsNotes()`
- `<rosettajs>.API.setDefaultAPIAsOpenFormula()`
- `<rosettajs>.API.isDefaultNotes()`
- `<rosettajs>.API.isDefaultOpenFormula()`

#### Framework

- `<rosettajs>.API.getDefaultFramework()`
- `<rosettajs>.API.setDefaultFrameworkAsJS()`
- `<rosettajs>.API.setDefaultFrameworkAsVoltMX()`
- `<rosettajs>.API.isDefaultFrameworkJS()`
- `<rosettajs>.API.isDefaultFrameworkVoltMX()`

#### Extending

- `<rosettajs>.API.registerAPI(apiRef, name, code, lang, cat)`
- `<rosettajs>.API.registerAPIs(apiRef, jsonAPIs)`

#### Intellisense files

- `<rosettajs>.API.getTernFileNames()`

## Rosetta Converters

### Defaults:

```java
{
  _allowPassthrough: false,
  _nativeness: {
    "_global": true, // true =all native js
    "@Do": true,
    "@DoWhile": true,
    "@For": true,
    "@If": true,
    "@While": true,
    "@True": true,
    "@False": true
  },
  _stripNumbers: true,
  _paramAsFieldName: true
}
```

### Getters, Setters, and Checkers

- `<converter>.config.getAllowPassthrough()`
- `<converter>.config.getNativeness(formula)`
- `<converter>.config.getParamAsFieldName()`
- `<converter>.config.getStripNumbers()`
- `<converter>.config.setAllowPassthrough(allow)`
- `<converter>.config.setNativeness(formula, native)`
- `<converter>.config.setParamAsFieldName(convert)`
- `<converter>.config.setStripNumbers(strip)`

## Volt MXGo

See the [Rosetta options](../howto/configrosetta.md) under the project settings in Volt MXGo Iris.

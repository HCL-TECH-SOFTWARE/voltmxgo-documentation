# The Rosetta API Schema

The Rosetta API is instantiated as a multi-nested JavaScript object defining the each API implementation as methods structured within the object. The structure can be broken down as follows:

## Level I: API Category Objects

```
    Admin
    Agent
    Attachment
    Compatibility
    Create
    Database
    (...trimmed list for readability...)
    UserEnvironment
    UserId
    View
    Window
```

## API Configuration Objects
```
    API
    logger
    build
    version
```

## Level II: Category Objects

Each category object encloses definitions for method definition of the category. For example, below is the Math category object showing all the methods available for the Math category:

```
    abs
    acos
    acosh
    (...trimmed list for readability...)
    tan
    tanh
    trun
```
In addition to the method definitions, there are special objects for the Lotus Notes formula language implementations as well as Open Formula language implementations, defined as:

```
    _notes
    _openFormula
```

## Level III: API Method Definition Objects
Each method definition is composed of the name of the method itself and the functional implementation

Example for the Rosetta implementation of the `<rosettajs>.Math.abs` API:
``
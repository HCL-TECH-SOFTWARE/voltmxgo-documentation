# Rosetta API schema

The Rosetta API is instantiated as a multi-nested JavaScript object defining each API implementation as methods structured within the object. The structure can be broken down as follows:

## Level I: API category objects

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

## API configuration objects

```
API
logger
build
version
```

## Level II: Category objects

Each category object encloses definitions for method definition of the category. For example, below is the Math category object showing all the methods available for the Math category:

```
abs
acos
acosh
(...trimmed list for readability...)
tan
tanh
trunc
```

In addition to the method definitions, there are special objects for the Lotus Notes formula language implementations and OpenFormula language implementations, defined as:

```
_notes
_openFormula
```

## Level III: API method definition objects

Each method definition is composed of the name of the method and the functional implementation.

Examples:

- For the Rosetta implementation of the `<rosettajs>.Math.abs` API:

    ```
    name: "abs"
    abs: ƒ abs(...value)
    ```

- For the Lotus Notes formula language implementation `<rosettajs>.Math._notes.functions.Abs`:

    ```
    name: "Abs"
    Abs: ƒ Abs(...value)
    ```

- For the OpenFormula language implementation `<rosettajs>.Math._openFormula.ABS`:

    ```
    name: "ABS"
    ABS: ƒ ABS(number)
    ```

## Structure and runtime details

The **Rosetta** implementation will call either the *Notes* implementation or the *OpenFormula* implementation. You can think of the Rosetta implementations as a top layer that encapsulates both the *Notes* implementations and the *OpenFormula* implementations.

In this way, we expose a single language of API methods that represent APIs in either formula language, or both. Hence, the naming **Rosetta (Stone)**. Also, some APIs only exist in OpenFormula and some APIs only exist in *Lotus Notes* formula language, and some in both. By **defining the top layer as Rosetta** for all existing APIs in both formula languages, a single API library  corresponding to all possible APIs in either formula language is created.

When an API contains sub-implementations for each formula language, for example, *OpenFormula* **=ABS** and *Notes Formula* **@Abs** being represented by ***Rosetta abs()*** API, the configuration option to use the *Notes Formula* implementation vs the *OpenFormula* (or vice versa) is observed. Sometimes, the sub-implementations for each formula language for a specific API, for example the absolute value (abs) API, may return the result. However, the arguments accepted may differ. For example, the **@Abs()** of *Notes Formula* accepts lists of numbers, and if a list is passed in, a list of is returned. Lists in this context are converted into JavaScript arrays.

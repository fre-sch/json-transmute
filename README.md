# JSON Transmute

Define transformations of JSON with JSON.

This document does not describe a specific implementation, it describes the
Transmute *"protocol"* that implementations should adhere to.

Aside from documenting the operations of Transmute, this repository contains
test JSON files, which can be used to validate an implementation.

## Introduction

```typescript
type JSON = null|boolean|number|string|array|object

Transmute(Expression: JSON, Context: JSON) -> JSON
```

**`Expression`**
: Describes a new JSON object created from `Context`.  `Expression` is always fully recursive.

**`Context`**
: Application specific data.


## Expressions

`expression` describes the resulting JSON. It can contain operator expressions
referencing `context`. Any valid JSON is a valid transmute `expression`. Without
any operator, `expression` simply describes the resulting JSON value.

```javascript
let expression = {
    "person": {
        "firstname": "Alice"
    }
}
let context = {
    "description": "this context isn't being referenced in expression"
}
Transmute(expression, context) === {
    "person": {
        "firstname": "Alice"
    }
}
```

### JSON-Path

Property values must be checked if they're [JSON-Path](https://goessner.net/articles/JsonPath/)
strings, that is, they're starting with a `$` (dollar) symbol. In that case,
the JSON-Path is evaluated against `context` and matching value is retrieved.

```javascript
let expression = "$.person.firstname"
let context = {
    "person": {
        "firstname": "Albert"
    }
}
Transmute(expression, context) === ["Albert"]
```

```javascript
let expression = "$.products.*.price"
let context = {
    "products": [
        {
            "price": "$4.00"
        },
        {
            "price": "$12.99"
        }
    ]
}
Transmute(expression, context) === ["$4.00", "$12.99"]
```

```javascript
let expression = "$.products.*.title"
let context = {
    "products": [
        {
            "price": "$4.00"
        },
        {
            "price": "$12.99"
        }
    ]
}
Transmute(expression, context) === []
```

## Operators

* [`#coalesce` exclude null values](/coalesce/)
* [`#concat` concatenate (multiple) arrays](/concat/)
* [`#extend` copy object and modify](/extend/)
* [`#first` first element of arrays](/first/)
* [`#format` string formatting](/format/)
* [`#map` create arrays](/map/)
* [`#sum` calculate sum of arrays of numbers](/sum/)
* [`#transmute` defer evaluation](/transmute/)

## Test validation

Test JSON files define objects with three properties: `expression`, `context`,
`result`. Implementations are valid, if they're able to produce `result` from
`expression` and `context`.

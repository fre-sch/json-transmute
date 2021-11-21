# Transmute `#extend`

Copy object and add or modify properties. Note that `#extend` cannot remove/unset
existing properties of source object. Extending a non-object value results in that
value, unchanged.

```javascript
let expression = {
    "#extend": {
        "base": "value"
    },
    "key": "value"
}
let context = {}
Transmute(expression, context) === {
    "base": "value",
    "key": "value"
}
```

```javascript
let expression = {
    "#extend": "$.person",
    "lastName": "Modified",
    "country": "DefaultCountry"
}
let context = {
    "person": {
        "firstName": "Alice",
        "lastName": "Tester"
    }
}
Transmute(expression, context) === {
    "firstName": "Alice",
    "lastName": "Modified",
    "country": "DefaultCountry"
}
```

```javascript
let expression = {
    "#extend": "$.person",
    "orders": [
        "$.order"
    ]
}
let context = {
    "order": {
        "invoiceNo": "123",
        "items": [
            {
                "title": "Gadget",
                "price": "$1.00"
            }
        ]
    },
    "person": {
        "firstName": "Alice",
        "lastName": "Tester"
    }
}
Transmute(expression, context) === {
    "firstName": "Alice",
    "lastName": "Tester",
    "orders": [
        {
            "invoiceNo": "123",
            "items": [
                {
                    "title": "Gadget",
                    "price": "$1.00"
                }
            ]
        }
    ]
}
```

```javascript
let expression = {
    "#extend": "not an object",
    "key": "value"
}
let context = {}
Transmute(expression, context) === "not an object"
```

```javascript
let expression = {
    "#extend": "$.person",
    "key": "value"
}
let context = {}
Transmute(expression, context) === null
```

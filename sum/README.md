# Transmute `#sum`

Sum of values. Values are expected to be numbers, invalid values are silently
ignored.

```javascript
let expression = {
    "#sum": "$.products.*.price"
}
let context = {
    "products": [
        {
            "price": 1
        },
        {
            "price": 2
        },
        {
            "price": "invalid value"
        },
        {
            "price": 3
        }
    ]
}
Transmute(expression, context) === 6
```

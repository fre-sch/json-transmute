# Transmute `#join`

Join arrays of values into string. Non-string values should be cast to string.
String representation of objects and arrays is implementation specific.
Optional `#separator` can be provided, default is `""` (empty string). Value
of `#separator` must be string.

```javascript
let expression = {
    "#join": "$.products.*.title",
    "#separator": " | "
}
let context = {
    "products": [
        {
            "title": "Beer",
            "price": 1
        },
        {
            "title": "Pizza",
            "price": 2
        },
        {
            "title": "Brownies",
            "price": 3
        }
    ]
}
Transmute(expression, context) === "Beer | Pizza | Brownies"
```

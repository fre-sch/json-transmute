# Transmute `#join`

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

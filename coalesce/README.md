# Transmute `#coalesce`

```javascript
let expression = {
    "#coalesce": "$.products"
}
let context = {
    "products": [
        {
            "title": "one"
        },
        {
            "title": "two"
        },
        null,
        {
            "title": "three",
        }
    ]
}
Transmute(expression, context) === [
    {
        "title": "one"
    },
    {
        "title": "two"
    },
    {
        "title": "three"
    }
]
```

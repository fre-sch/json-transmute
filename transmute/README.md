# Transmute `#transmute`

Defer value evaluation

```javascript
let expression = {
    "#map": {
        "#transmute": "$.propname"
    },
    "label": "$.it.title"
}
let context = {
    "propname": "products",
    "products": [
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
}
Transmute(expression, context) === [
    {
        "label": "one"
    },
    {
        "label": "two"
    },
    {
        "label": "three"
    }
]
```

# Transmute `#concat`

Concatenate (multiple) arrays into one.

```javascript
let expression = {
    "#concat": [
        [
            "one",
            "two"
        ],
        [
            "three",
            "four"
        ]
    ]
}
let context = {}
Transmute(expression, context) === [
    "one",
    "two",
    "three",
    "four"
]
```

```javascript
let expression = {
    "#concat": [
        "$.tags",
        [
            "$.newTag"
        ]
    ]
}
let context = {
    "tags": [
        "one",
        "two"
    ],
    "newTag": "three"
}
Transmute(expression, context) === [
    "one",
    "two",
    "three"
]
```

```javascript
let expression = {
    "items": {
        "#concat": [
            "$.basketItems",
            "$.couponItems"
        ]
    }
}
let context = {
    "basketItems": [
        {
            "title": "Cool Gadget",
            "price": 100
        }
    ],
    "couponItems": [
        {
            "title": "20% off Cool Gadget",
            "price": -20
        }
    ]
}
Transmute(expression, context) === {
    "items": [
        {
            "title": "Cool Gadget",
            "price": 100
        },
        {
            "title": "20% off Cool Gadget",
            "price": -20
        }
    ]
}
```

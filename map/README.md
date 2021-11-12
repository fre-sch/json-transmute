# Transmute `#map`

`#map` creates arrays from `context`. `#map`s value can be a JSON-Path
referencing `context` or an array. `#map` iterates the items in array, and
provides access to the current items as `$.it` while `$.parent` refers to the
original `context`.

```javascript
let expression = {
    "#map": "$.tags",
    "title": "$.it",
    "price": "$.parent.defaultPrice"
}
let context = {
    "defaultPrice": 3.00,
    "tags": ["beer", "wine", "peanuts"]
}
Transmute(expression, context) === [
    {
        "title": "beer",
        "price": 3.00
    },
    {
        "title": "wine",
        "price": 3.00
    },
    {
        "title": "peanuts",
        "price": 3.00
    }
]
```

```javascript
let expression = {
    "#map": "$.products.*",
    "title": "$.it.title.en",
    "price": "$.it.price.USD"
}
let context = {
    "products": [
        {
            "title": {
                "en": "Beer",
                "de": "Bier",
            },
            "price": {
                "USD": 12.00,
                "EUR": 9.99
            }
        },
        {
            "title": {
                "ja": "豚カツ",
                "de": "Schweineschnitzel",
                "en": "Pork cutlet, breaded",
            },
            "price": {
                "USD": 3.00,
                "EUR": 2.49,
                "JPY": 300,
            }
        }
    ]
}

Transmute(expression, context) === [
    {
        "title": "Beer",
        "price": 9.99
    },
    {
        "title": "Pork cutlet, breaded",
        "price": 3.00
    }
]
```

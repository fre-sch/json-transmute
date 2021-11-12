# Transmute `#first`

`#first` retrieves the first item of an array.

```javascript
let expression = {
    "#first": "$.*.firstname"
}
let context = {
    "ID1": {
        "firstname": "Alice"
    },
    "ID2": {
        "firstname": "Bob"
    }
}
Transmute(expression, context) === "Albert"
```

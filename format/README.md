# Transmute `#format`

`#format` provides template strings and uses `Context` to create a new string.
Template system is implementation specific, however it must provide access to
`context`.

```javascript
let expression = {
    "#format": "Hello {person.firstname}!"
}
let context = {
    "person": {
        "firstname": "Berta"
    }
}

Transmute(expression, context) === "Hello Berta!"
```

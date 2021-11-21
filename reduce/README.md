# Transmute `#reduce`

**THIS IS ONLY A DRAFT**


```javascript
{
    "#reduce": "$.multipleItems",
    "#aggregate": 0,
    "#function": "#sum"
}
```

```javascript
{
    "#reduce": "$.multipleItems",
    "#aggregate": [],
    "#function": "#concat"
}
```

```javascript
{
  "#reduce": "$.multipleItems",
  "#aggregate": {},
  "#function": "#merge"
}
```

Use "friendly" terms, or use common terms?

`#into` - aggregate
`#using` - function for combining aggregate with item

```javascript
{
    "#reduce": "$.multipleItems",
    "#into": 0,
    "#using": "#sum"
}
```

```javascript
{
    "#reduce": "$.multipleItems",
    "#into": [],
    "#using": "#concat"
}
```

```javascript
{
  "#reduce": "$.multipleItems",
  "#into": {},
  "#using": "#merge"
}
```

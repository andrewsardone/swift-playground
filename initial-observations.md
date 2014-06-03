- Option type, encapsulating the notion of `nil` in the type
- Nested functions
- functions are a first-class , that is, just a special case of closures
- The syntax for closures is a little awkward – not a fan of this `in` business, or the params and return types within the braces (`{}`):

```swift
[1, 2, 3, 4].map({
    (number: Int) -> Int in
    return number * 3
})
// [3, 6, 9, 12]

// can be truncated to the concise:

[1, 2, 3, 4].map({ number in number * 3 })
// [3, 6, 9, 12]
```

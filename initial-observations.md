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

// can use numbered index for parameters, too
[1, 2, 3, 4].map({ $0 * 3 })
// [3, 6, 9, 12]
```
- I like the distinction of structs vs classes (pass-by-value, pass-by-reference, mutability based on those values and references, etc.). This gives us a language-level value-object-like setup
- Good use of [protocols](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Protocols.html#//apple_ref/doc/uid/TP40014097-CH25-XID_345) \o/

when subclassing Obj-C classes, subclasses in swift need to stub the designated initializer

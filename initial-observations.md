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
- Array types can be written with the type of the contents (`Array<SomeType>`), but a [shorthand syntax](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/CollectionTypes.html#//apple_ref/doc/uid/TP40014097-CH8-XID_136) is preferred: `SomeType[]`. This is nice – type safety with array contents is a Good Thing™ – but I’m worried I’ll see a lot of people fallback to an unsafe world via `Any[]` or something of the sort.

```swift
let myArray: Any[] = ["foo", "bar", "baz"]
myArray[0] = 1 // :-/
```

when subclassing Obj-C classes, subclasses in swift need to stub the designated initializer

### To Swift, or not to Swift

Reasons for adopting Swift is difficult to pin down, besides Swift being the future of Apple development; however, Objective-C appears to be providing all of Swift's utility. This section is meant to gather thoughts on "business of moving to Swift".

*<pending>*

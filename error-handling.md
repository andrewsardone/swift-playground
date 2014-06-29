## Error Handling

### Cocoa error rerporting

From Swift, Cocoa API interoperability is important, and many Cocoa APIs rely
on consumers to pass in an `NSError **` argument for error handling.

```objc
// The uninitialized `error` will be populated with any error in the task.
NSError *error = nil;
BOOL written = [myString writeToFile:path
                          atomically:NO
                            encoding:NSUTF8StringEncoding
                               error:&error];

// The returned BOOL is the indicator of whether or not the task was
// successful. If it was unsuccessful, then we can inspect our NSError
// reference.
if (!success) {
    NSLog(@"%@", error);
}
```

This is a C idiom, so how can Swift use this Cocoa pattern?

In Swift, we have the [`NSErrorPointer` and the prefix `&` operator][sei] for
working with an optional `NSError`:

```swift
var writeError : NSError?
let written = myString.writeToFile(path,
    atomically: false,
    encoding: NSUTF8StringEncoding,
    error: &writeError)
if !written {
    if let error = writeError {
        println("write failure: \(error.localizedDescription)")
    }
}
```

### Ideal idiomatic Swift error handling

I don’t think `NSErrorPointer` is the ideal method of handling errors in the
world of Swift – it’s a stopgap to bridge into the C-world of Objective-C. When
thinking about idiomatic error handling, we should ask whether or not
conventions are good enough or if the *language* needs to provide some built-in
mechanics?

Exceptions as control-flow are a possible solution, but not one that’s
historically favored by the Cocoa community. Not that exceptions are the way to
go, but it should be noted that *some* sort of better error handling in a
future of version of Swift is on [Chris Lattner’s radar][ehcl]:

> We're aware of the opportunity and also desire better error handling features
> in Swift, but they didn't make it in time for 1.0.

[sei]: https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/BuildingCocoaApps/AdoptingCocoaDesignPatterns.html#//apple_ref/doc/uid/TP40014216-CH7-XID_9
[ehcl]: https://devforums.apple.com/message/995390#995390

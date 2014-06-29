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

[sei]: https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/BuildingCocoaApps/AdoptingCocoaDesignPatterns.html#//apple_ref/doc/uid/TP40014216-CH7-XID_9

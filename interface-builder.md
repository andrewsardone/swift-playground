## Xcode’s Interface Builder & Swift

With the release of Xcode 6, we have a few new source annotations, such as
`@IBDesignable` & `@IBInspectable`. While I don’t think their use is exclusive
to Swift (need to double check), they allow you to get better previews and
Interface Builder interaction [with your
views](https://gist.github.com/KevinVitale/a0e7fc1ffdf61169e7c6):

```swift
import UIKit
 
@IBDesignable
class MyView: UIView {
 
    // Now `fooColor` is configurable in Interface Builder – what up, designers!
    @IBInspectable var fooColor: UIColor?
    
    init(frame: CGRect) {
        super.init(frame: frame)
        // Initialization code
        self.backgroundColor = UIColor.yellowColor();
    }
}
```

# SwiftUI

#### Resources:

* WWDC 2019 - \#204: [Introducing SwiftUI: Building Your First App](https://developer.apple.com/videos/play/wwdc2019/204/)
* WWDC 2019 - \#216: [SwiftUI Essentials](https://developer.apple.com/videos/play/wwdc2019/216/)
* WWDC 2019 - \#226: [Data Flow Through SwiftUI](https://developer.apple.com/videos/play/wwdc2019/226/)
* WWDC 2019 - \#231: [Integrating SwiftUI](https://developer.apple.com/videos/play/wwdc2019/231/)
* WWDC 2019 - \#237: [Building Custom Views with SwiftUI](https://developer.apple.com/videos/play/wwdc2019/237/)
* WWDC 2019 - \#238: [Accessibility in SwiftUI](https://developer.apple.com/videos/play/wwdc2019/238/)
* WWDC 2019 - \#219: [SwiftUI on watchOS](https://developer.apple.com/videos/play/wwdc2019/219/)
* [SwiftUI Apple website](https://developer.apple.com/tutorials/swiftui)
* ---
* WWDC 2019 - \#415: [Modern Swift API Design](https://developer.apple.com/videos/play/wwdc2019/415/)
* WWDC 2019 - \#402: [What's New in Swift](https://developer.apple.com/videos/play/wwdc2019/402/)
* WWDC 2019 - \#233: [Mastering Xcode Previews](https://developer.apple.com/videos/play/wwdc2019/233/)



## Overview

_Xcode Version 11.0 beta 2 \(11M337n\)_

### What is a View?

A view defines a piece of UI. Any struct that conforms to the `View` protocol is considered a view:

```swift
struct ContentView : View {
  var body: some View {
    Text("Learn-Swift.dev")
  }
}
```

The `View` protocol is pretty straightforward:

```swift
public protocol View : _View {
  /// The type of view representing the body of this view.
  associatedtype Body : View

  /// Declares the content and behavior of this view.
  var body: Self.Body { get }
}
```

### Container views

Declared as a composition of other views serving as their content, specified in a special kind of closure caled the `view builder`. Examples: `VStack`. 

Most controls in SwiftUI are also containers.

### Primitive views

The `View` protocol defines the `body` property that defines another kind of View - might feel recursive. The chain stops at the primitive views \(provided by SwiftUI\), views that don't have content of their own and represent the atomic building blocks for from which all other views are built.

Examples: `Text`, `Color`, `Spacer`, `Image`, `Shape`, `Divider`.

### Modifiers

A modifier is a method that creates a new `View` from an existing `View`.

Hence, the order in which modifiers are used matters as they modify the 'previous' `View`:

```swift
Text("Hello World")
  .font(.largeTitle)
  .foregroundColor(.white)
  .padding()
  .background(.red)
  .padding()
  .background(yellow)
  .padding()
  .background(.blue)
```

Modifiers are specific to the View they are applied on \(eg. `.font` for `Text`\) but some are general:

#### Color

```swift
Text("Hello World")
  .foregroundColor(.green)
  .background(.red, cornerRadius: 12)
```

#### Accent Color

```swift
Form {
  ...
}
  .accentColor(Color("avocadoGreen"))
```

#### Disabled

```text
Form {
  ...
}
  .disabled(!connectedToHogwartsServer)
```

#### Padding

```swift
Text("Hello World")
  .padding(.all)
```

#### Flexible frame

```swift
Text("Hello World")
  .frame(minWidth: 0, maxWidth: .infinity, minHeight: 0, maxHeight: .infinity)
```

### Environment

Consists of all the context in with a `View` appears.

Each `View` inherits the environment from its parent - hence all modifiers are applied to the parents.

```swift
SomeView(...) { ... }
  .environment(\.layoutDirection, .leftToRight)
```

Available environment variables:

* contentSizeCategory \(.small, .large, .axLarge\)
* colorScheme \(.light, .dark\)
* locale \(eg. en\_US\)
* layoutDirection \(.leftToRight\)


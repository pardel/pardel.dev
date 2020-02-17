# TabbedView

Provides a tab view with content.

```swift
TabbedView {
  View1() { ... }
    .tabItemLabel {
      Image(systemName: "pencil")
      Text("New Pet")
    }
  View2() { ... }
    .tabItemLabel {
      Image(systemName: "...")
      Text("All Pets")
    }
}
```

